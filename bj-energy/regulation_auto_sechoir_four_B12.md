# Régulation automatique du séchoir et du four — produit B12
**Briqueterie Jemmel — objectif : minimiser le gaz et l'électricité en respectant les consignes de qualité**
Version 1 du 17/10/2026, établie à partir de la mémoire projet (771 lignes), du PDF « Régulation four / récupération / séchoir (version révisée) », des synoptiques du 28/09 et des relevés WinCC du 02/10 au 16/10/2026.

---

## 0. Principes retenus

1. **La chaleur gratuite d'abord.** Ordre des sources de chaleur du séchoir : récupération du four → brûleur ASC (modulant) → B1/B2 (tout-ou-rien, dernier recours). Le brûleur ne complète que ce que la récupération ne fournit pas.
2. **Le moins de température possible, le plus d'air utile possible.** Ordre de grandeur des coûts : 1 °C de moins sur T°C1 ≈ 100 th/h ≈ 7 DT/h de gaz ; 1 Hz de plus sur les deux ventilateurs d'air chaud ≈ 3,4 kW ≈ 1 DT/h. La régulation cherche donc la consigne de soufflage **la plus basse** qui tient la qualité, et règle les ventilateurs **au juste besoin** (loi en cube : P = 85·(fc/50)³ + 141·(fr/50)³ + 88·(fe/50)³ + 25 kW).
3. **La qualité est une contrainte, pas une variable d'optimisation.** Séchoir : humidité avant recyclage ≤ 14 % (consigne de travail 12 %), zone extraction ≤ 2,5 %, T°C1 ≤ 145 °C, T°C4 ≤ 250 °C, balancelles en marche 24/24. Four : températures de zone dans ±10 °C de la recette, T.refroidissement dans sa bande, pression four 0,6 mbar, limites du chef four sur la récupération.
4. **La cadence pilote, l'humidité corrige.** Le signal de cadence est l'ampérage de la chaîne des balancelles (comptage des clefs), pas la mouleuse ni le four. Il donne l'avance (feedforward) ; les mesures d'humidité et de température corrigent (feedback).
5. **Tout dans l'automate, rien dans WinCC.** Boucles, sécurités, AUTO/MAN sans à-coup, anti-windup, repli sur défaut capteur. WinCC ne sert qu'à afficher et archiver.
6. **Priorités entre four et séchoir** : qualité de cuisson > pression du four > demande de chaleur du séchoir > économie d'énergie du séchoir.

---

## 1. SÉCHOIR

### 1.1 Grandeurs utilisées

| Repère | Mesure | Rôle dans la régulation | État |
|---|---|---|---|
| I_chaîne | ampérage chaîne balancelles (ACTUEL / MAX 20,5 A) | **cadence** : 1 pic = 1 clef, 5 clefs/balancelle, 64 balancelles | OK |
| H_AR, T_AR | humidité / température « zone avant recyclage » (canal inférieur) | **variable de qualité principale**, ≤ 14 % | OK |
| H_R, T_R | humidité / température « zone recyclage » (haut du canal supérieur) | pilote recyclage et B1/B2 | OK |
| H_EX, T_EX | « zone extraction » (milieu canal inférieur) | contrôle de fin de séchage (≈ 1–2 %) | OK |
| T°C1 | air soufflé, sortie chambre (≈ 8 m après brassage) | **variable réglée par les sources de chaleur**, ≤ 145 °C | OK |
| T°C4 | chambre de mélange (thermocouple K) | limite ≤ 250 °C, indicateur de l'apport récupération | OK |
| TC3 | arrivée gaine de récupération | feedforward chaleur disponible | OK |
| P2 | canal supérieur (2–5 mbar en marche) | surveillance extraction | OK |
| P3 | canal inférieur avant recyclage (−0,1 à −0,5 mbar) | surveillance tirage interne | OK |
| P1, P4 | — | P1 HS (figé 0,00), P4 figé −1,2 | **à remplacer** |
| Q_gaz | compteur gaz séchoir (Nm³/h) | KPI, détection B1/B2 | OK |
| P_élec | centrale « Séchoir » (kW) | KPI | OK |

### 1.2 Actionneurs

| Actionneur | Commande | Plage de travail | Remarque |
|---|---|---|---|
| Air chaud fc (2 × 75 kW, C200) | Profibus, Hz | 34–45 Hz (standby 30) | Tmax fiche 160 °C, fonctionne à 224 °C depuis des années : non bloquant |
| Recyclage fr (2 × 90 kW, 1 variateur 250 kW) | Profibus, Hz | 30–47 Hz (standby 30) | |
| Extraction air humide fe (3 × 37 kW, ABB) | Profibus, Hz | 30–45 Hz (standby 30) | |
| Brassage (3 × 4 kW) | Hz | 35 Hz fixe (30 standby) | essai 47→35 Hz : +5 °C seulement sur T°C1 |
| Brûleur ASC 3 500 th/h, modulant | consigne 4–20 mA vers Ascon + autorisation de marche | SP 100–140 °C | registre arrière à motoriser (servomoteur) |
| B1 / B2 (tout-ou-rien, ≈ 60 Nm³/h chacun) | marche/arrêt | — | dernier recours |
| Registre récupération (chambre de mélange) | servomoteur à poser | 0–100 % | 100 % en marche normale |
| Fenêtres d'air frais (2) + registre arrière ASC | servomoteurs à poser | 0–100 % | normalement fermées ; ouverture seulement pour protéger T°C4 ≤ 250 |

### 1.3 Architecture des boucles (du plus lent au plus rapide)

```
cadence (I_chaîne) ──► tables de base : fc0, fr0, fe0, T1_base
                                │
H_AR ──► [L1 qualité, lent] ──► T1_SP (100…140 °C)
                                │
T°C1 ──► [L2 chaleur, cascade] ─┬─► demande récupération D (0–100 %) ──► automate four
                                ├─► ASC : SP 4–20 mA + autorisation
                                └─► B1/B2 : hystérésis sur H_R, dernier recours
H_AR ──► [L3 air chaud]  fc = fc0 + trim
H_R  ──► [L4 recyclage]  fr = fr0 + trim
H_R, P2 ─► [L5 extraction] fe = fe0 + trim
T°C4 ──► [L6 protection] registre arrière ASC / fenêtres
```

#### L0 — Cadence et charge (feedforward)
- Détection d'une clef : front montant de I_chaîne au-dessus de 8 A, antirebond 20 s. Taux de clefs k (clefs/h) moyenné sur 60 min glissantes.
- Cadence relative C = k / k_nom, avec k_nom = 320 clefs / 2,5 h = 128 clefs/h (séchoir plein, cycle B12 réel 2 h 30). Production ≈ k × 48 pièces/h.
- Charge en eau Ẇ ≈ pièces/h × 1,1 kg (7 250 g vert → 6 150 g sec). Ẇ sert de pondération aux tables (une table par palier de C : 0,6 / 0,8 / 1,0 / 1,2).
- Numéro de balancelle : compteur modulo 320 clefs recalé sur le capteur du poste de chargement ; donne la balancelle qui bloque quand I_chaîne > MAX (demande du 08/10).

#### L1 — Qualité → consigne de soufflage T1_SP (boucle lente, intégrale seule)
- Mesure : H_AR. Consigne : **12 %** (bande 9–13 %, alarme 14 %).
- T1_SP = T1_base(C) + correction, avec T1_base : C 0,6 → 105 °C ; 0,8 → 112 ; 1,0 → 120 ; 1,2 → 128 °C (points de départ, à recaler).
- Correction intégrale : +2 °C par % d'écart au-dessus de 12 %, −1 °C par % en dessous (asymétrique : on descend plus prudemment qu'on ne monte), période 15 min, bornes 100–140 °C. Dérivée nulle.
- Gel de la correction pendant 20 min après une sortie de standby et pendant toute entrée en standby.
- Contrôle de cohérence : si H_EX > 2,5 % pendant 20 min → T1_SP +5 °C immédiat (séchage de fin insuffisant), quelle que soit H_AR.

#### L2 — Cascade des sources de chaleur sur T°C1
Boucle PI sur l'écart e = T1_SP − T°C1, sortie U (0–100 %), Kp = 1,5 %/°C, Ti = 180 s (temps de réponse mesuré ≈ 5 min), anti-windup, transfert sans à-coup.
Répartition de U :
1. **Récupération four (0–100 % de U)** : D = U transmis au S7-412 par Profibus. Le four augmente la vitesse du ventilateur de récupération dans ses limites (voir § 2.4). Registre récupération à 100 %. Feedforward : si TC3 baisse de plus de 15 °C en 10 min (arrêt four, poussée lente), U est augmenté de 10 % par anticipation.
2. **ASC (prend le relais quand le four signale « récupération au maximum » ou D ≥ 100 %)** : SP_ASC (4–20 mA) = T1_SP + 3 °C ; autorisation ON si T°C1 < T1_SP − 5 °C ; OFF si T°C1 > T1_SP + 8 °C pendant 3 min **et** flag four « récupération disponible » ; temporisation mini 12 min entre deux démarrages (préventilation). En marche, l'Ascon module seul sur sa PV ; l'automate n'écrit que la consigne.
3. **B1/B2 (dernier recours)** : ON si H_R > 32 % pendant 10 min **et** (ASC ≥ 90 % de modulation ou T°C1 < T1_SP − 15 °C) ; OFF dès que H_R < 27 % ou ASC < 60 % pendant 10 min. Jamais ON si ASC est à l'arrêt par excès de température. (Ceci remplace l'hystérésis 25/30 % actuelle par une condition qui exige d'abord l'épuisement de l'ASC.)

#### L3 — Air chaud fc (électricité, et levier préféré avant la température)
- fc = fc0(C) + trim, fc0 : C 0,6 → 36 Hz ; 0,8 → 38 ; 1,0 → 40 ; 1,2 → 43 Hz.
- Trim PI sur H_AR (même logique que l'auto actuel, bornes humidité 9–13,5 %) : Kp 0,5 Hz/%, Ti 600 s, ±3 Hz, rampe 30 s. Priorité : quand H_AR est haute, L3 monte fc **avant** que L1 ne monte T1_SP (L1 est 2 à 3 fois plus lente).
- Bornes 34–45 Hz ; si T°C1 > 145 °C → fc +3 Hz forcé (dilution par débit) et ASC OFF.

#### L4 — Recyclage fr
- fr = fr0(C) + trim, fr0 : C 0,6 → 33 Hz ; 0,8 → 36 ; 1,0 → 38 ; 1,2 → 42 Hz (relevé du 16/10 : 38 Hz à cadence normale).
- Trim P sur H_R autour de 31 % (bande 29–34 %) : ±0,8 Hz par % d'écart, filtré 5 min, ±4 Hz. **Sens d'action à confirmer** par un essai ±3 Hz sur 30 min avant mise en auto (la recette actuelle est proportionnelle, on garde son sens).
- Objectif énergétique : fr est le plus gros poste électrique (141 kW à 50 Hz) ; chaque Hz évité à 40 Hz ≈ 5,4 kW.

#### L5 — Extraction air humide fe
- fe = fe0(C) + trim, fe0 : C 0,6 → 33 Hz ; 0,8 → 37 ; 1,0 → 41 ; 1,2 → 45 Hz.
- Trim PI sur H_R : si H_R > 34 % → fe monte (Kp 0,7 Hz/%, Ti 600 s, +4 Hz max) ; si H_R < 29 % → fe descend (−3 Hz max). Chaque m³ extrait emporte de la chaleur à 45 °C vers la cheminée : l'extraction est réglée **au minimum qui tient H_R ≤ 34 %**.
- Garde-fous pression : P2 < 1,5 mbar ou P3 > +0,2 mbar pendant 2 min → fe +2 Hz ; P2 > 5 mbar → fe −2 Hz.

#### L6 — Protection chambre de mélange (T°C4)
- T°C4 > 235 °C → registre arrière ASC ouvert +10 % par 2 min (air ambiant) ; > 250 °C → fenêtres d'air frais ouvertes 50 %, alarme, ASC OFF ; retour à la fermeture par paliers quand T°C4 < 215 °C.
- Les 16/10 et 11/10, T°C4 atteignait 260–310 °C avec l'ASC en manuel et le registre arrière fermé à 4 cm : ce cas est pris en charge par L6 et plus par l'opérateur.

#### L7 — Standby et redémarrage (demande du 02/10 : ventilateurs maintenus pendant l'attente)
- Détection d'arrêt : aucune clef pendant 5 min (I_chaîne) **ou** coupes/min = 0 pendant 5 min.
- t = 0–5 min : rien ne change (attente mouleuse). B1/B2 OFF immédiatement.
- t = 5 min : T1_SP −10 °C, D = 0 (le four garde sa récupération au minimum, la chaleur part en cheminée si nécessaire), ASC en modulation basse.
- t = 15 min : ASC OFF ; fc → 30 Hz ; t = 20 min : fr → 30 Hz ; t = 25 min : fe → 30 Hz (temporisations existantes de la recette). Brassage 30 Hz. Balancelles : inchangées (elles s'arrêtent d'elles-mêmes).
- Redémarrage sur la première clef détectée : tables rechargées à la cadence mesurée sur 15 min ; T1_SP de départ = T1_base(C) − 5 °C si H_AR < 10 % (séchoir déjà sec), = T1_base(C) + 5 °C si H_AR > 13 % ; correction L1 gelée 20 min ; ASC autorisé seulement si D = 100 % n'a pas ramené T°C1 à T1_SP − 5 °C en 8 min.

### 1.4 Sécurités et replis
- Capteur hors 4–20 mA (H_AR, H_R, T°C1, T°C4, I_chaîne) : boucle concernée en MAN sur la dernière valeur, alarme, et T1_SP figé.
- Perte de la liaison Profibus four : D ignoré, ASC prend tout (comportement actuel).
- T°C1 > 145 °C ou T°C4 > 250 °C : voir L3 / L6 ; les deux sont des limites dures.
- H_AR > 14 % pendant 10 min : alarme qualité, T1_SP +5 °C et fc +2 Hz immédiats (la qualité prime sur l'économie).
- Blocage chaîne (I_chaîne > MAX) : numéro et position de la balancelle affichés, boucles gelées.
- Tous les PID : AUTO/MAN avec suivi, anti-windup, rampes 0,1 Hz/s sur les variateurs.

### 1.5 Blocs automate (S7-317, STEP 7)
| Bloc | Fonction | E/S |
|---|---|---|
| FB100 Cadence | comptage clefs, k, C, Ẇ, numéro balancelle | AI I_chaîne |
| FB101 Tables | fc0, fr0, fe0, T1_base en fonction de C (DB paramètres) | — |
| FB102 Qualité | L1 : T1_SP | AI H_AR, H_EX |
| FB103 Chaleur | L2 : PI T°C1, répartition D / ASC / B1-B2 | AI T°C1, TC3 ; AO 4–20 mA ASC (SM332) ; DO autorisation ASC, B1, B2 ; Profibus D, flags four |
| FB104 Ventilateurs | L3, L4, L5 + rampes | AI H_AR, H_R, P2, P3 ; Profibus fc, fr, fe, brassage |
| FB105 Protection | L6 + sécurités | AI T°C4 ; AO registres (SM332) |
| FB106 Standby | L7 | — |
| DB110 Paramètres | toutes les consignes, bornes, gains, tables (modifiables depuis WinCC, pas la logique) | — |

Matériel à prévoir : 3 servomoteurs (registre récupération, registre arrière ASC, 1 fenêtre jumelée ou 2), remplacement P1 et P4 (PIZ 0–5 mbar), 1 sonde T/H à la cheminée d'air humide (bilan), cartes SM332/SM331 déjà disponibles.

### 1.6 Résultat attendu
- Gaz : T1_SP descend d'elle-même vers 105–115 °C au lieu de 120–130 °C manuels dès que la récupération est en priorité ; l'ASC ne tourne plus 19–22 h/24. Les scénarios du dossier du 07/10 restent la référence : −22 % (séchoir seul) à −54/−72 % (avec récupération par paliers), soit 0,8 à 1,8 M DT/an.
- Électricité : ventilateurs de 38–47 Hz vers 36–41 Hz en cadence normale ≈ −40 à −60 kW en moyenne ≈ 1 000 à 1 400 kWh/j ≈ 300 à 400 DT/j.

---

## 2. FOUR

### 2.1 Grandeurs utilisées
| Repère | Mesure | Rôle |
|---|---|---|
| Turbo1, Turbo2, ZF1, ZF2 | températures de centrale (K) | boucles de température existantes |
| T.refroidissement (csg 650), T.récup bas (csg 500) | zone de refroidissement | **contrainte qualité** pour la récupération |
| P_four (csg 0,6 mbar) | milieu zone de refroidissement | boucle pression |
| P_tirage (−1,7 à −2,2 mbar), T.fumée (77–130 °C) | côté cheminée | surveillance tirage, condensation |
| T.récup voûte, TC3 (séchoir) | chaleur envoyée au séchoir | retour de la demande D |
| FC portes entrée / contre-porte / sortie, FC pousseur | tout-ou-rien, déjà dans le S7-412 | **feedforward poussée et portes** |
| temps de poussée (s) | consigne opérateur | cadence four |
| Q_gaz four = totaliseur − séchoir | KPI | compteur four à réparer |
| O₂ fumées (à installer) | excès d'air | boucle air/gaz (phase 2) |

### 2.2 Actionneurs
| Actionneur | État | Plage |
|---|---|---|
| Modulation brûleurs par centrale (T1, T2, C1, C2) | PID existants | selon recette |
| Électrovannes min/max + servomoteur registre gaz | existant, min pendant la poussée | — |
| Ventilateurs d'air de combustion (15 + 3 × 7,5 kW) | servomoteurs de registre ; **variateurs à poser** | 40–100 % de vitesse |
| Contre-pression CP (22 kW) | variateur Profibus, PID pression | 40–54 Hz ; standby 700 tr/min |
| Récupération (45 kW) | variateur Profibus | 40–50 Hz (750 tr/min, limite chef) ; paliers jusqu'à 1 365 tr/min sur décision |
| Tirage (37 kW) | variateur, manuel | 1 090–1 250 tr/min |

### 2.3 Boucles

#### F1 — Températures de centrale (existant + synchronisation poussée)
- PID existants conservés (consignes B12 : Turbo1 800, Turbo2 810, ZF1 880, ZF2 890 °C).
- **Gel de l'intégrateur** pendant la poussée (FC pousseur ou porte d'entrée) et 60 s après : évite la sur-réaction qui suit la chute de 30–38 °C sur Turbo1 et le rattrapage de 5–9 min.
- **Consignes de ralenti** : si aucune poussée depuis 30 min → Turbo1/Turbo2 −15 °C, ZF1/ZF2 −10 °C ; depuis 60 min → −30 / −20 °C ; retour en rampe 2 °C/min dès la poussée suivante. Bandes à valider avec le chef four (limites qualité ±10 °C en régime normal).
- Pas de recette automatique par temps de poussée tant que le technicien veut intervenir : la recette reste manuelle, seuls les décalages de ralenti sont automatiques.

#### F2 — Air de combustion (variateurs à installer)
- Phase 1, asservissement à la modulation : vitesse_air = v_min + (v_max − v_min) × modulation_brûleurs, v_min = 50 %, v_max = 100 % ; **pendant la poussée** (gaz sur électrovanne min) : vitesse_air = v_min pendant la durée de la poussée + 60 s, puis rampe 2 %/s. Essai préalable recommandé (fermeture manuelle du registre d'air d'une centrale pendant quelques poussées) pour chiffrer la réduction de la chute de température.
- Phase 2, avec analyseur O₂ dans le caisson avant le tirage : trim de v_min/v_max pour tenir O₂ = 4 % (bande 3–6 %) à charge stable. C'est le levier gaz le plus sûr du four (excès d'air), estimé 3 à 6 % du gaz four.
- Gain électrique certain : 4 ventilateurs ≈ 37 kW ; à 50 % de vitesse pendant 2 min sur 11 ≈ −5 kW en moyenne.

#### F3 — Pression four (existant + feedforward portes et récupération)
- PID sur CP : consigne 0,6 mbar, zone morte ±0,1 mbar, P faible, Ti 30–60 s, D = 0, filtre 2–5 s ; point normal avec ≥ 5 Hz de réserve vers le haut (revoir les registres si CP travaille à 50 Hz).
- **Feedforward portes** (FC déjà câblées) : porte de sortie ouverte (dépression −1,1 mbar) → CP +4 Hz immédiat ; porte d'entrée / contre-porte ouverte (surpression +2,4 mbar) → CP −4 Hz immédiat ; retour en rampe 20 s après fermeture. Gains à ajuster sur les courbes WinCC.
- **Feedforward récupération** : ΔCP = G × Δf_récup, G mesuré par paliers de 2 Hz hors poussée (section 5 du PDF).
- Standby CP 700 tr/min conservé.

#### F4 — Récupération (nouvelle boucle, pilotée par la demande du séchoir)
- Consigne : D (0–100 %) reçue du S7-317 → f_récup = f_min + (f_max − f_min) × D, rampe 0,1 Hz/s, intégrateur gelé pendant la poussée.
- f_min = 40 Hz (600 tr/min, ne jamais priver le séchoir), f_max = 50 Hz (750 tr/min) en phase 1 ; paliers 55 → 91 Hz (825 → 1 365 tr/min) en phase 2 sur décision, avec suivi qualité.
- **Contraintes prioritaires** (dans l'ordre) :
  1. T.refroidissement < 620 °C (bande 620–680 autour de 650) → f_récup −1 Hz/min jusqu'au retour dans la bande ; T.récup bas < 450 °C idem.
  2. P_four < 0,3 mbar pendant 10 s ou défaut CP → f_récup = f_min immédiat, alarme (risque d'aspiration de fumées vers le séchoir).
  3. CP > 90 % de sa plage → montée de f_récup interdite.
  4. Four en ralenti (pas de poussée depuis 30 min) → f_max temporaire = 45 Hz.
- Flags renvoyés au séchoir : « récupération au maximum », « récupération disponible », « four en ralenti ».
- Quand le capteur de pression de gaine sera remplacé (−10/+10 mbar, 4–20 mA) : boucle interne rapide de pression de gaine, la boucle D donnant alors une consigne de pression.

#### F5 — Tirage
- Reste **manuel** (qualité), avec deux garde-fous automatiques : T.fumée < 90 °C pendant 15 min → alarme condensation (tirage trop fort ou four trop froid) ; P_tirage < −2,3 mbar → alarme.
- Option phase 2 : décalage automatique −5 % quand le four passe en ralenti, retour à la poussée suivante.

#### F6 — Ralenti four (arrêts de 30 à 60 min, fréquents : ≈ 5 h/j d'arrêts non programmés)
- Déclenché par F1 (pas de poussée depuis 30 min) : consignes de ralenti, CP standby, f_max récupération 45 Hz, tirage −5 % (si F5 phase 2), air de combustion v_min.
- Sortie de ralenti à la poussée suivante : rampes 2 °C/min, 0,1 Hz/s.

### 2.4 Coordination four ↔ séchoir (Profibus S7-317 ↔ S7-412)
| Sens | Mot échangé |
|---|---|
| séchoir → four | D (0–100 %), T°C1, T°C4, TC3, flag standby séchoir, flag alarme T°C4 |
| four → séchoir | f_récup actuelle, flag « récup au max », flag « récup disponible », flag ralenti four, flag poussée en cours, T.récup voûte |
Règle : le four ne monte la récupération que si ses contraintes F4 le permettent ; le séchoir n'allume l'ASC que si le four a répondu « au maximum » ou n'a pas ramené T°C1 en 8 min.

### 2.5 Sécurités
- Mêmes règles que le séchoir : AUTO/MAN sans à-coup, anti-windup, repli sur dernière valeur et alarme sur capteur hors plage, rampes lentes.
- La sécurité de flamme, la préventilation et les électrovannes restent dans les coffrets brûleurs ; l'automate ne donne que des consignes et des autorisations.
- Alarme de cohérence : récupération au maximum et T°C4 encore basse ; pression four hors ±1,5 mbar hors ouverture de porte.

### 2.6 Résultat attendu
- Ratio four actuel 280–313 th/t (référence audit 350, moyenne mondiale four tunnel 250). Leviers par ordre de gain : récupération vers le séchoir (gain comptabilisé côté séchoir), excès d'air (3–6 % du gaz four ≈ 200–400 Nm³/j), chute de température à la poussée (à chiffrer par essai), ralenti automatique (moins de gaz pendant les ≈ 5 h/j d'arrêts).
- Électricité four ≈ 60 kW : −5 kW sur l'air de combustion ; la récupération au-delà de 750 tr/min coûte ≈ +12 kW (négligeable devant le gaz).

---

## 3. Ordre de mise en service (une étape à la fois, plusieurs poussées stables entre deux étapes)

1. **Préalables** : liaison serveur WinCC fiable (pertes de liaison 11/10 et 16/10) ; P1, P4 et capteur de gaine remplacés ; mesure Ascon vérifiée (PV 0,0 vue le 28/09) ; compteur gaz four réparé ; validation du comptage des clefs (FB100) contre le compteur de wagons de l'empilage sur 3 postes.
2. **Séchoir, FB100 + tables** en lecture seule (affichage de C, T1_SP calculée) pendant 2 jours, comparaison avec la conduite manuelle.
3. **L3/L4/L5 ventilateurs** en auto, L1/L2 en manuel.
4. **L2 ASC** en auto avec D = 0 (récupération fixe), puis L1.
5. **Four F3** feedforward portes, puis mesure du gain récupération/CP.
6. **F4 récupération** pilotée par D, f_max 50 Hz ; puis paliers sur décision avec suivi qualité (porosité, retrait, incuit/surcuit, T.refroidissement).
7. **F1 gel/ralenti**, puis **F2** après pose des variateurs et essai manuel ; O₂ en dernier.
8. **L6 / L7** après motorisation des registres.

## 4. Points à confirmer sur site
- Sens d'action du recyclage sur H_R (essai ±3 Hz).
- Bandes qualité du chef four : T.refroidissement, T.récup bas, tolérances de zone, vitesse maximale admise pour la récupération par palier.
- Fréquence maximale continue de la contre-pression (moteur/ventilateur).
- Durée de préventilation de l'ASC (temporisation mini entre démarrages).
- Emplacement du capteur de pression supplémentaire acheté le 06/10 (proposition : gaine de récupération côté séchoir).
- Tables fc0/fr0/fe0/T1_base : à recaler sur deux semaines d'archives une fois FB100 validé.

## 5. Observations tirées des deux vidéos fournies (images extraites le 17/10/2026)

**Vidéo 2 — page SECHOIR et page paramètres, 16/10/2026 de 16:51:13 à 16:52:01 (utilisateur medali)**
- ASC en mode **AUTO (HUMIDITÉ)** à ce moment-là : PV 112–113 °C, SP 111 °C ; paramètres : MANU 120 °C / chambre 127 °C ; AUTO : brûleur max 120 / min 110 °C, humidité recyclage max 34 / min 29 %, temps d'incrémentation et de décrémentation 1 s. C'est donc un pilotage tout-ou-peu de la consigne (110 ↔ 120 °C au rythme de 1 °C/s selon H_R), que L1/L2 remplacent par une consigne continue calculée sur H_AR.
- **Zone avant recyclage 74,5–75,8 °C / 13,8–14,5 %** (bornes affichées max 13 / min 9) : la limite de 14 % est atteinte avec l'air chaud à 43 Hz et l'ASC à 112 °C seulement → c'est exactement le cas où L1 doit relever T1_SP et L3 fc (qualité avant économie).
- Zone recyclage 32,7–33,6 % / 60,5 °C (bande 29–34) ; RECY 43 → 41 Hz ; air chaud SP 43 Hz ; extraction : colonne AUTO 30 Hz, colonne MANUEL 44 Hz, bornes 39–45 Hz.
- TC3 153–156 °C ; T°C4 **155 → 187 °C** en 40 s (pompage de la chambre de mélange déjà noté le 16/10) ; TC2 33–40 °C ; P2 2,8–4,1 mbar ; P3 −0,40 à −0,69 mbar ; P4 figé −1,18 ; P1 0,00.
- B1/B2 en AUTO, B2-REMOTE / B1-REMOTE, brûleur à point PV 55–56 °C (max 80 / min 70) ; brûleur 2 LOCAL, PV 0,0, SP 119.
- Registres : récupération AUT, chambre MAN, arrière séchoir MAN, brûleur AUT, port chambre MAN ; « valeur différence entre chambre et brûleur » = 0 ; consigne température arrière 85 °C.

**Vidéo 1 — gros plan filmé sur l'écran SECHOIR, 68 s, sans horodatage visible (réglage différent du 16/10 16:51)**
- Zone avant recyclage **91,5–91,8 °C / 8,0–8,7 %** avec bornes max 9 / min 5 % : séchage plus poussé que nécessaire (12 % suffisent), donc gaz dépensé au-delà du besoin → cas inverse du précédent, que L1 corrige en baissant T1_SP.
- ASC AUTO (HUMIDITÉ), PV 115 → 120 °C, SP 111 → 112 °C.
- **P3 positif (+0,14 à +0,24 mbar)** alors qu'il est négatif les autres jours (−0,1 à −0,7) : canal inférieur en surpression → extraction trop faible ou recyclage trop fort à ce moment ; garde-fou L5 (P3 > +0,2 mbar pendant 2 min → fe +2 Hz).
- Ces deux vidéos ne contiennent pas de page FOUR ; la vidéo de la poussée four du 14/10 citée dans la mémoire n'est pas parmi les fichiers fournis.

## 6. Sources
Mémoire projet « memoire_claude_briqueterie.md » (sections 1 à 10) ; « Régulation four / récupération / séchoir (version révisée) » du 30/09/2026 ; synoptiques four et séchoir du 28/09/2026 ; relevés WinCC du 02/10 au 16/10/2026 ; les deux vidéos fournies (images extraites, section 5) ; audit énergétique CRA2E/ANME 2016.
