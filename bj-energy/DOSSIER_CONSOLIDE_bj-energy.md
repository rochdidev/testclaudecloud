# Dossier consolidé — projet de régulation séchoir et four B12
**Briqueterie Jemmel (BJ Energy) — synthèse de tous les documents reçus, historique de la discussion, anomalies, solutions et suggestions**
Établi le 23/10/2026 à partir des fichiers du dossier `bj-energy`. Tous les chiffres sont ceux des documents cités ; ce qui est une estimation est signalé comme tel.

---

## Sommaire

1. Objet et périmètre
2. Inventaire des fichiers reçus
3. L'installation en quelques chiffres
4. Chronologie de la discussion et des versions du projet
5. Lecture détaillée des documents
   - 5.1 PDF « Régulation four / récupération / séchoir, version révisée » (30/09)
   - 5.2 Mémoire du projet (exports du 17/10 et du 19/10)
   - 5.3 Projet définitif V1 du 19/10
   - 5.4 Annexe programmes automate (10 blocs SCL)
   - 5.5 Ma proposition du 17/10 (`regulation_auto_sechoir_four_B12.md`)
   - 5.6 Les six vidéos
   - 5.7 Les captures d'écran
6. Anomalies relevées
   - 6.1 Instrumentation et mesures
   - 6.2 Conduite actuelle du séchoir
   - 6.3 Conduite actuelle du four
   - 6.4 Électricité, gaz, archives
   - 6.5 Incohérences entre documents
   - 6.6 Points à corriger dans le projet V1 et son annexe
7. Solutions : ce que le projet V1 règle, et comment
8. Suggestions complémentaires
9. Plan d'action consolidé par priorité
10. Données encore attendues
11. Annexe A — relevés clés datés
12. Annexe B — formules et paramètres de départ du V1

---

## 1. Objet et périmètre

L'exploitant veut **baisser le gaz et l'électricité du séchoir et du four, à cadence et qualité égales**, en passant d'une conduite manuelle à une régulation automatique en boucle fermée. Le produit étudié est le **B12** seul (contrainte clients). Le projet s'est construit du 30/09 au 19/10/2026 par itérations : dossiers successifs, relevés WinCC, vidéos du synoptique, nuit de surveillance, puis un **projet définitif V1** avec ses programmes automate.

Le présent dossier ne remplace pas le V1 : il le situe dans l'historique, décrit tout ce qui a été reçu, relève les anomalies (de l'installation et des documents) et propose des solutions et des suggestions.

---

## 2. Inventaire des fichiers reçus

| Fichier dans `bj-energy/` | Reçu le | Taille | Contenu | Doublons éliminés |
|---|---|---|---|---|
| `memoire_claude_briqueterie.md` | 17/10 | 111 Ko, 771 lignes | export de la mémoire du projet au 17/10 (10 sections) | — |
| `regulation_four_recuperation_sechoir_version_revisee.pdf` | 17/10 | 207 Ko, 7 p. | première note de régulation, version révisée du 30/09 | — |
| `synoptique_four.jpg`, `synoptique_sechoir.jpg` | 17/10 | 90 Ko | captures des synoptiques du 28/09 15:55 | 1 image en double |
| `video_1.mp4` | 17/10 | 6,2 Mo, 68 s | gros plan écran SÉCHOIR, sans horodatage | 2 copies supprimées |
| `video_2.mp4` | 17/10 | 4,4 Mo, 52 s | SÉCHOIR + paramètres, 16/10 16:51 | 1 copie supprimée |
| `video_3.mp4` | 17/10 | 10,8 Mo, 131 s | SÉCHOIR, courbe TC3, vitesses, recyclage, 17/10 02:11 | — |
| `courbe_centrale_four_13-14_10_2026.jpg` | 17/10 | — | courbe d'une centrale du four, 13/10 17:00 → 14/10 03:00 | — |
| `video_4_vid1.mp4` | 17/10 (message interrompu) | 23,8 Mo, 287 s | FOUR + courbes, 17/10 04:00-04:05 | — |
| `Projet_Regulation_B12_V1.pdf` | 23/10 | 2,3 Mo, 8 p. | projet définitif V1 du 19/10 | — |
| `Projet_Regulation_B12_V1_Annexe_Programmes.pdf` | 23/10 | 135 Ko, 20 p. | 10 blocs STEP 7 SCL | — |
| `Memoire_Claude_Briqueterie_19-10-2026.pdf` | 23/10 | 316 Ko, 56 p. | export de la mémoire au 19/10 (13 fichiers) | — |
| `video_5_vid5.mp4` | 23/10 | 3,6 Mo, 39 s | coffret du brûleur ASC, intérieur du séchoir | — |
| `video_6_vid0_part1.mp4` | 23/10 | 22,8 Mo, 277 s | SÉCHOIR + courbe T°C1, 07/10 18:17-18:21 | — |
| `regulation_auto_sechoir_four_B12.md` | rédigé le 17/10 | — | ma proposition de régulation, avant le V1 | — |

Au total : 3 PDF, 2 exports mémoire, 6 vidéos distinctes (sur 9 fichiers envoyés), 3 images distinctes (sur 4). Les vidéos ont été lues par extraction d'images fixes (8 à 10 par vidéo, plus des agrandissements) ; elles n'ont pas de son exploitable.

---

## 3. L'installation en quelques chiffres

**Production.** B12 uniquement, 2 160 pièces par wagon, 16 pièces par coupe ; mouleuse Morando 620 Synthesis (315 kW, étoile-triangle, 5,7-6,3 coupes/min), mouleuse Lacker en secours, non reliée à WinCC ; ≈ 5 h/j d'arrêts non programmés. Cadence étudiée : 18 wagons par poste à l'empilage, four à 10-12 min de poussée (40-48 wagons/j), 60 wagons/j au grand maximum.

**Séchoir.** Semi-continu à balancelles : 64 balancelles × 5 étages × 48 pièces = 15 360 pièces ; 82 m × 6,35 m ; cycle B12 réel ≈ 2 h 30 (le compteur affiche la moitié) ; chaîne 24/24. Air chaud 2 × 75 kW sur variateurs C200 90 kW (depuis le 16/10) ; recyclage 2 × 90 kW sur un variateur 250 kW ; extraction air humide 3 × 37 kW sur un variateur ABB ; brassage 3 × 4 kW ; récupération four → séchoir 45 kW (gaine 1,80 × 1,90 × 20 m). Brûleur ASC 3 500 th/h modulant air/gaz avec calculateur Siemens, variateur d'air et thermorégulateur Gefran 1600, consigne 4-20 mA depuis le S7-300 ; brûleurs arrière B1/B2 tout-ou-rien ≈ 60 Nm³/h chacun, pilotés sur l'humidité du recyclage (marche > 33 %, arrêt < 27 %). Automate S7-300 CPU 317, STEP 7, Profibus, WinCC.

**Four.** Tunnel Euroimpianti Aris Compact 46, 110 m, 26 wagons ; centrales T1, T2, Feu 1, Feu 2 actives (12 brûleurs chacune, électrovannes gaz min/max, servomoteur d'air pendant la poussée) ; centrales 3-6 arrêtées par choix ; tirage 37 kW, récupération 45 kW, contre-pression 22 kW sur variateurs Profibus ; pression de consigne 0,6 mbar ; automate S7-412 ; signaux des portes et du pousseur déjà câblés.

**Énergie (septembre 2026).** Séchoir 7 570 Nm³/j (ratio 160 th/t verte, plage 90-226), ≈ 6 000 kWh/j ; four 12 800 Nm³/j (313 th/t rouge) ; électricité usine 13 400 kWh/j ; compresseur ≈ 70 kW en permanence. Tarifs : gaz 70,5 millimes/th HT (≈ 0,71 DT/Nm³), électricité 222-377 millimes/kWh selon la tranche, prime de puissance 13 200 DT/mois pour 1 200 kW souscrits.

**Références.** Audit 2016 : ratio thermique 382 th/t (référence 350, moyenne mondiale four tunnel 250), électrique 35,6 kWh/t ; en juillet-août 2021 le séchoir a tourné **sans gaz** avec une poussée continue de 11 min et toutes les entrées d'air de la chambre de mélange fermées.

---

## 4. Chronologie de la discussion et des versions du projet

| Date | Événement |
|---|---|
| 28/09 | captures des synoptiques four et séchoir (15:55) ; ASC en LOCAL, mesure 0,0 °C pour consigne 119 ; T°C4 142,9 °C ; contre-pression à 750 tr/min sans réserve |
| 30/09 | **PDF « Régulation four / récupération / séchoir, version révisée »** : 4 préalables, 2 boucles nouvelles (contre-pression, récupération sur T°C4), autorisation du brûleur, tirage manuel |
| 02-04/10 | réponses détaillées de l'exploitant (questions séchoir) ; archive électrique WinCC du 02/10 (20 courbes, 1 valeur/s) ; dossier 22 p. du 03/10 ; dossier final four + séchoir 21 p. du 04/10 (scénarios S1-S4, 709 k à 1 394 kDT/an) |
| 06-07/10 | capteur P3 posé ; essai de fermeture du registre arrière de l'ASC (T°C4 190 → 300 °C) ; révision 5 du dossier |
| 08/10 | examen complet des synoptiques et des courbes par AnyDesk ; rapport PDF « Courbes WinCC 03-08/10 » ; projet révision 7 ; contraintes fixées : T°C1 ≤ 145 °C, T°C4 ≤ 250 °C |
| 11-12/10 | second examen (historique 08-12/10) ; pertes de liaison WinCC constatées |
| 13-14/10 | courbe de centrale avec chutes à chaque poussée ; vidéo poussée four du 14/10 (03:04-03:13) ; plaques des ventilateurs d'air de combustion ; idée des variateurs sur l'air de combustion |
| 16/10 | variateurs d'air chaud en service ; vidéo des synoptiques 15:56-16:00 ; ASC en MANU 110 °C puis AUTO humidité 111 °C (16:51) |
| 17/10 | vidéo 02:11 (ASC en MANU malgré TC3 à 220 °C, 23 h 27 de brûleur sur 24 h) ; vidéo 04:00 page FOUR ; **ma proposition `regulation_auto_sechoir_four_B12.md`** ; premier export de la mémoire |
| 18/10 | compteurs gaz déclarés fonctionnels ; consigne d'humidité avant recyclage devenue variable |
| 19/10 | nuit de surveillance du séchoir (00:48-06:00) ; vidéo du coffret ASC ; **projet définitif V1 + annexe programmes** ; second export de la mémoire |
| 23/10 | réception du V1, de l'annexe, de la mémoire du 19/10 et de 3 vidéos ; présent dossier |

Le V1 déclare remplacer « tous les dossiers et révisions précédents » : il est la référence. Ma proposition du 17/10 reste utile comme contre-lecture indépendante (section 5.5).

---

## 5. Lecture détaillée des documents

### 5.1 PDF « Régulation four / récupération / séchoir, version révisée » (30/09, 7 pages)

Première note structurée. Objectif : faire de la chaleur récupérée du four la source principale du séchoir, le brûleur de 3 500 th/h n'étant qu'un appoint. Constats du 28/09 : brûleur en marche 22 h 09 sur 24 h, chambre de mélange à 142,9 °C pour une consigne brûleur de 119 °C, air de récupération à 301 °C au départ et 186 °C à TC3, mesure du régulateur brûleur à 0,0 °C en mode LOCAL, capteur de pression de gaine à 0,00, récupération à sa borne haute (45 Hz), contre-pression à 50 Hz sans réserve.

**Quatre préalables** : rétablir la liaison au serveur de données ; remettre en état la mesure et le mode du brûleur ; identifier les boucles existantes derrière « Régulation En Auto » ; redonner de la marge à la contre-pression.

**Boucles proposées** : contre-pression en PI sur la pression du four (P faible, I 30-60 s, zone morte ±0,05-0,1 mbar) ; récupération en I lent sur T°C4, bornée par T.refroidissement ; autorisation de marche du brûleur sur T°C4 (arrêt à consigne + 10 °C, redémarrage à − 10 °C, 10-15 min entre démarrages) ; tirage inchangé. Feedforward récupération → contre-pression, blocage de la récupération si la contre-pression dépasse 90 %. Sécurités côté automate (AUTO/MAN sans à-coup, anti-windup, gel pendant la poussée, repli sur capteur hors plage). Nouveau capteur de pression de gaine. Mise en service en 6 étapes.

**Appréciation.** Note fondatrice ; ses quatre préalables sont encore d'actualité le 17/10 (vidéo 3). Elle supposait la contre-pression à sa borne, ce que les examens suivants ont nuancé (CP à 700-900 tr/min selon les jours). Elle n'abordait pas encore l'humidité avant recyclage, devenue la variable de qualité centrale.

### 5.2 Mémoire du projet (exports du 17/10 et du 19/10)

L'export du 17/10 (771 lignes) contient 10 sections : régulation (≈ 220 énoncés), archive électrique du 02/10, relevés WinCC du 08/10 et des 11-12/10, vidéos du 14/10 et du 16/10, rapports journaliers 30/09-15/10, facture STEG 09/2026, rapports électrique et gaz de septembre, audit 2016. L'export du 19/10 (56 pages, 13 fichiers) reprend le tout et ajoute : compteurs gaz fonctionnels (18/10), ASC modulant air/gaz avec calculateur, variateur d'air et Gefran 1600, consigne d'humidité avant recyclage variable (18/10), tableau des consommations journalières derrière la case bleue de MESURE AMPER, question du 19/10 sur la modulation air/gaz des centrales, fichier « surveillance de nuit du 19/10 » (dont les données elles-mêmes — log, courbes, recette — ne sont pas dans l'export).

**Ce que la mémoire apporte de décisif** (détail en annexe A) : l'ampérage de la chaîne comme signal de cadence ; les limites T°C1 ≤ 145 / T°C4 ≤ 250 °C ; l'humidité avant recyclage ≤ 14 % ; la règle « mouleuse toujours au maximum » ; la limite de 750 tr/min de la récupération et la demande du décideur d'étudier au-delà par paliers ; la formule électrique du séchoir P = 85 (fc/50)³ + 141 (fr/50)³ + 88 (fe/50)³ + 25 kW ; les chutes de 30-38 °C sur Turbo 1 à chaque poussée ; les deux roulements de pression aux portes (−1,1 / +2,4 mbar) ; le compteur compresseur faux d'un facteur 3,22 ; les 74 kW / 370 kVAR de la fabrication à vide.

### 5.3 Projet définitif V1 du 19/10 (8 pages)

**Principe.** Le séchoir tient l'humidité avant recyclage (consigne 12,5 %, limite 14 %) avec, dans l'ordre : chaleur du four, température de l'ASC, ventilation pour les pointes, B1/B2 en dernier ; T°C1 ≤ 145 et T°C4 ≤ 250 °C passent avant tout. Au four : pression stable malgré les portes, récupération montée par paliers avec la contre-pression, centrales modulées air et gaz ensemble. Chaque bloc est chargé 7 jours en observation avant d'être mis en automatique.

**Constats fondateurs (section 2).** ≈ 85 % de l'air soufflé est de l'air ambiant chauffé puis rejeté ; l'humidité avant recyclage suit d'abord la température (nuit du 19/10 : −3 °C ≈ +1 point ; 12,5 % ≈ 83,5 °C) ; les deux dépassements de 14 % sont survenus avec l'ASC en butée à 125 °C et l'air chaud déjà à 45 Hz ; pendant les arrêts de chaîne l'ASC restait à 128-130 °C ; l'ASC pompe (T°C4 175 ↔ 285 °C toutes les 8-10 min le 17/10) ; 1 °C de TC3 ≈ 9 kW, un palier de récupération ≈ 160-180 kW ; aux arrêts la récupération s'effondre (260 → 150 °C en 1-2 h).

**Coûts marginaux (section 3).** Consigne ASC +1 °C ≈ 5-8 Nm³/h ≈ 4-6 DT/h et −0,2 point d'humidité en 3-4 min ; air chaud +1 Hz ≈ 4,7 kW ≈ 1,3 DT/h plus l'air frais à chauffer ; extraction +1 Hz ≈ 3,8 kW + 40 kW de chaleur rejetée ; B1 ou B2 ≈ 43 DT/h chacun. Conclusion : en régime établi, monter la température coûte moins que souffler plus d'air ; la ventilation sert aux pointes.

**Séchoir (section 4).** Sept blocs : FB102 cadence, FB103 limites, FB104 planification de la récupération et régimes A/B/C, FB106 humidité avant recyclage → consigne ASC, FB107 pilote ASC (reprise douce, plafond T°C4, pompage, zéro gaz), FB101 maître (modes, humidité du recyclage, sélecteur, ventilateurs, B1/B2, registre, demande au four), FB105 balancelle au blocage. Modes : production, attente (< 15 min), standby régulé, reprise, repli. Sept réglages immédiats sans programmation (R1-R7), dont : baisser la consigne ASC de 3 °C par 15 min quand TC3 > 200 °C et l'humidité < 12,5 % ; ne pas activer le PID sur l'humidité avant recyclage à 8 % ; registre arrière jamais sous 8 cm quand l'ASC brûle ; butée AUTO à 130 °C ; standby harmonisé à 15 min ; alarmes WinCC ; retrouver la cause de l'arrêt de l'ASC du 16/10 à 22:15.

**Four (section 5).** FB114 pression et portes (contre-pression PI + anticipation, tirage en recentrage lent, pas d'anticipation aux portes, intégrale gelée) ; FB112 récupération par paliers 0-9 (675 → 1 365 tr/min) couplés à la contre-pression, +1 palier par 10 min si la consigne ASC > 128 °C, four maître, un palier validé par semaine ; FB110 poussée, FB111 recette selon la poussée, FB113 comptage (spécifiés, non programmés) ; FB115 modulation air/gaz des centrales avec allure figée à 30 % pendant la poussée et supplément décroissant ensuite.

**Compresseur, électricité, mouleuses (section 6).** Fuites d'air d'abord, puis variateur ; arrêt réel des moteurs à vide ; régulateur PF ; variateur et eau au malaxeur pour la Morando ; raccordement de la Lacker à WinCC.

**Matériel, essais, mise en service, gains (sections 8-11).** 23 essais E1-E23 ; mise en service en 6 étapes ; gains prudents-hauts : séchoir 267-803 kDT/an, récupération + four 305-371, centrales 58-142, compresseur 15-40, moteurs à vide 22-35, total ≈ 667 à 1 391 kDT/an ; budget : étape 0 + séchoir 37-72 kDT, four 65-140, centrales 8-12 + devis, compresseur 16-20, mouleuse 95-165.

### 5.4 Annexe programmes automate (20 pages, 10 blocs SCL)

Chaque bloc a un mode observation (sorties calculées et archivées, commande existante conservée, reprise sans à-coup) et un mode automatique. Lecture bloc par bloc :

- **FB101 REGUL_SECHOIR** (maître, S7-300). Modes 1 à 5 ; boucle PI de l'humidité du recyclage T_HR = 120 + 2 e + intégrale, zone morte ±3 %, bornée 110-135 °C ; sélecteur T_cons = MIN(MAX(T_HR ; T_HRa) ; T_L1 ; T_L4 ; T_L7 ; 135) avec montée ≤ 3 °C/min et descente libre ; signal Gel qui gèle les intégrales et force la demande de récupération à 100 % ; autorisation ASC et registre arrière (fermé si ASC éteint) ; alarme ASC sans flamme en production > 5 min ; ventilateurs : base FB104 + corrections (air chaud ± dF_AC de FB106 borné 36-45 Hz, recyclage +5 Hz si HRa > 13,5 %, extraction forcée à 45 Hz si HR recyclage > 33 %, boucle L5 sur la température de cheminée quand C1 sera posé) ; standby régulé : air chaud et brassage 30 Hz, recyclage et extraction 30 + 1,25 (HR − 26) bornés 25-40 Hz ; reprise en 10 min ; rampes 0,1 Hz/s ; B1/B2 : logique 27/33 % conservée, 10 min mini, option O1 d'anticipation ; demande de récupération.
- **FB102 CADENCE.** Compte les clefs (compteur N/320 du synoptique), moyennes 10 min et 2 min, durée du tour, cycle réel = K_tour × tour (K_tour ≈ 3 à fixer par E5), chaîne arrêtée après 180 s sans clef.
- **FB103 LIMITES.** Filtres 30 s, validité des sondes (hors échelle, saut, valeur figée 10 min) ; limiteurs T_L1 = 135 − 3 (T°C1 − 140), maintien à 100 °C au-dessus de 145 jusqu'à 5 min sous 142 ; T_L4 = 135 − 2 (T°C4 − 230), 95 °C dès 245 ; arrêt critique à 250 °C pendant 2 min ; registre arrière = max(pos_min ; 60 + 4 (T°C4 − 230)), 100 % dès 245, fermé si ASC éteint ; alarmes à trois niveaux.
- **FB104 PLANIF_RECUP.** Chaleur de gaine Q_rec = 56 300 × N/750 × ρ × 1,01 × (TC3 − Ta)/3 600 ; besoin Q_need = q_p × 15 360 / cycle (q_p = 1,05 kWh/pièce, adapté sur 24 h quand le gaz est mesuré) ; charge brûleurs D = mesure gaz + anticipation modèle ; régimes A (D < 0,20 : ASC au minimum, humidité tenue par l'extraction), B (mixte), C (D > 0,95 : extraction −, recyclage +, registre +, B2/B1 anticipés en option) avec hystérésis et 15 min mini ; fréquences de base en fonction du rapport r = 2,5 / cycle ; alarme de capacité.
- **FB105 BALANCELLE_BLOCAGE.** Repère balancelle (1-64) et clef (1-5) au blocage de la chaîne, journal rémanent des 50 derniers blocages, statistique par balancelle ; capteurs inductifs S_REF et S_CLEF à poser, secours par pics d'ampérage.
- **FB106 REGUL_HRA.** Consigne ASC = anticipation (112 + 1,5 × cadence + 0,3 × (180 − TC3) si TC3 < 180) + PI sur (HRa − 12,5) (Kp 2,5 °C/point, Ti 8 min), bornée 110-135, montée 3 °C/min, descente 1 °C/min ; correction air chaud +5 Hz par point au-dessus de 12,5 % (−4/+6 Hz) ; alarme à 13,5 % pendant 2 min. Contient sa propre moyenne de cadence (doublon avec FB102).
- **FB107 ASC_PILOTE.** Reprise douce (≤ 115 °C pendant 20 min puis +1 °C/min) ; plafond sur l'enveloppe de T°C4 (max sur 12 min : −2 °C/min au-dessus de 240, +1 en dessous de 225, jamais plus de 10 °C sous la demande) ; détection du pompage (amplitude ≥ 60 °C, période 3-25 min, 3 cycles) ; zéro gaz (HRa < 12 % et demande ≤ 112 °C pendant 15 min, régime ≠ C ; rallumage si HRa > 13 % pendant 2 min, immédiat à 13,5 % ou T°C1 < 105 °C ; 20 min mini d'arrêt et de marche) ; comptage des démarrages de flamme (alarme > 4/h).
- **FB114 PRESSION_PORTES** (S7-412). Pression filtrée 5 s ; anti-rebond 2 s des portes ; pas d'anticipation à l'ouverture (sortie : CP +5 %, tirage −3 % ; entrée : CP −5 %, tirage +3 %), maintien 30 s puis retrait en 45 s ; PI contre-pression (Kp 4 %/mbar, Ti 60 s, 30-90 %) à intégrale gelée portes ouvertes ; tirage = base + recentrage lent de la contre-pression au milieu de sa plage (600 s, ±15 %, 55-85 %) ; ≤ 2 %/s.
- **FB115 CENTRALE_MOD** (× 4). PID de température → allure U → vitesse du ventilateur d'air, le gaz suivant par régulateur de rapport ; allure figée à 30 % pendant la poussée, intégrale gelée, reprise sans à-coup depuis l'allure d'avant poussée, supplément décroissant en 4 min (T1 +20 %, C1 +10 %) ; dérivée sur la mesure filtrée ; thermocouple HS → allure maintenue.
- **FB117 COMPRESSEUR_VAR.** PI de pression (6,5 bar, Kp 30 %/bar, Ti 15 s, 55-100 %), veille et reprise, séquence du compresseur de base.

Qualité générale : code cohérent, commenté, avec les protections attendues (anti-windup par blocage, reprise sans à-coup, filtres, bornes, rampes, validité des mesures). Les points à corriger sont en 6.6.

### 5.5 Ma proposition du 17/10

Rédigée avant le V1, à partir de la mémoire du 17/10, du PDF du 30/09 et des vidéos 1-3. Sept boucles séchoir (cadence, qualité → T1_SP, cascade des sources, air chaud, recyclage, extraction, protection T°C4, standby) et six boucles four (gel de l'intégrateur et ralenti, air de combustion sur variateur, pression avec feedforward portes, récupération continue 40-50 Hz bornée par T.refroidissement, tirage manuel, ralenti). Elle converge avec le V1 sur l'essentiel et en diffère sur quatre points, détaillés en 8.1 : ordre ventilation/température, B1/B2, critère du zéro gaz, récupération continue contre paliers. Elle reste dans le dossier comme contre-lecture ; le V1 fait foi.

### 5.6 Les six vidéos

**Vidéo 1 (68 s, sans horodatage, gros plan SÉCHOIR).** Zone avant recyclage 91,5-91,8 °C / 8,0-8,7 % avec bornes 9 / 5 % : séchage poussé bien au-delà du besoin (12,5 % suffisent) ; ASC en AUTO humidité, mesure 115 → 120 °C, consigne 111-112 ; **P3 positif (+0,14 à +0,24 mbar)**, alors qu'il est négatif les autres jours.

**Vidéo 2 (52 s, 16/10 16:51, SÉCHOIR + paramètres).** ASC AUTO humidité 112-113 °C, consigne 111 ; paramètres : MANU 120 / chambre 127 ; AUTO brûleur 110-120 °C sur humidité recyclage 29-34 %, incrément/décrément 1 s (pilotage tout-ou-peu) ; **avant recyclage 13,8-14,5 %** (bornes 9-13), air chaud 43 Hz, RECY 43 → 41 Hz ; T°C4 155 → 187 °C en 40 s ; TC3 153-156 ; extraction AUTO 30 / MANUEL 44 Hz, bornes 39-45 ; P2 2,8-4,1, P3 −0,40/−0,69, P4 figé −1,18, P1 0 ; brûleur à point 55-56 °C, B2-REMOTE / B1-REMOTE ; registres : récupération AUT, chambre MAN, arrière MAN, brûleur AUT, port chambre MAN.

**Vidéo 3 (131 s, 17/10 02:11-02:13, SÉCHOIR, courbe TC3, vitesses, recyclage).** Courbe TC3 du 15/10 21:30 au 17/10 02:30 : 180-200 °C puis palier à 215-225 °C après le 16/10 23:10. **ASC en MANU, consigne 120, mesure 125-128, flamme active, 23 h 27 min de marche sur 24 h ; T°C1 137-139 °C ; T°C4 262-277 °C ; séchoir en standby (balancelle 0 Hz, chaîne 0 A, décompte des ventilateurs en cours) et le brûleur continue.** Avant recyclage 80-81 °C / 12,3-12,6 % ; recyclage 29,5-30 % / 67 °C (bornes 27-33) ; extraction 122-125 °C / 1,4-1,8 % ; RECY 38 Hz (40 Hz / 800 tr/min sur la page recyclage) ; air chaud AUTO 41,3-42,1 Hz, bornes 36-43, humidité 8,0-13,5 %, **rampes 400 s** ; extraction AUTO 40 Hz ; défauts d'extraction affichés 10 s (perte de liaison) ; page recyclage : loi proportionnelle 38-46 Hz sur HR recyclage 28-36 %, seconde régulation sur l'humidité avant recyclage (consigne 8 %) non activée.

**Vidéo 4 (287 s, 17/10 04:00-04:05, FOUR + courbes).** Turbo 1 794/800, Turbo 2 809/810, Feu 1 869/880, Feu 2 888/890, Feu 3 512 non régulée ; poussée 600 s. Courbes du 16/10 : Turbo 2 (793 à 16:02 pour 810) sur 15:30-16:30 avec une chute profonde toutes les 11 min, descente en 1 min, remontée en 5-6 min ; la même sur 05:00-11:00 avec deux grands événements vers 06:15 et 09:30 ; CENTRALE3 (Feu 2) stable 880-890 avec un creux à 850 vers 10:00 ; pression four 03:40-04:05 autour de la consigne avec écarts aux portes. Fenêtre gaz : séchoir 611 m³ / 2 148,6 Nm³ sur le poste ; **four négatif (−1 010 m³ / −3 552 Nm³) à 04:04 le 17/10.**

**Vidéo 5 (39 s, 19/10, coffret ASC).** Calculateur Siemens « Système d'allumage et contrôle du générateur » affichant 36,2 ; indicateur rouge 51,3 °C ; thermorégulateur Gefran 1600 à 118 / 119 ; puis intérieur du séchoir (balancelles) et hublot de flamme.

**Vidéo 6 (277 s, 07/10 18:17-18:21, SÉCHOIR + courbe T°C1).** Soir de la fermeture du registre arrière : **T°C4 205 → 234 → 275 °C en 4 min** ; TC3 100 °C (récupération faible) ; ASC MANU 106-110 °C pour consigne 120 ; courbe T°C1 17:12-18:00 : 128-130 °C, creux à 113 °C vers 17:38, consigne 120 ; recyclage 38,3 % / 54 °C (bornes 34-39, essai en cours) ; avant recyclage 75,5 °C / 10,6-12,1 % ; « Régul. Humidité OFF » ; portes d'air chaud en MAN ; extraction 106-109 °C / 1,0 % ; P2 2,3-2,9, P3 −0,46/−0,87.

**Vidéo citée mais non reçue.** La vidéo de la poussée du four du 14/10 (8 min 54 s) décrite dans la mémoire n'est pas parmi les fichiers envoyés.

### 5.7 Les captures d'écran

Synoptiques du 28/09 15:55 (four et séchoir) : base du PDF du 30/09. Courbe d'une centrale du 13/10 17:00 au 14/10 03:00 : plateau avec une chute brève toutes les 11-12 min (≈ 50 poussées en 10 h), une chute trois fois plus profonde vers 18:00 après l'arrêt général de 16:30-17:00, amplitude un peu plus faible après 00:30 ; axe des températures non visible (Turbo 1 d'après la vidéo du 14/10 : creux à 762-770 °C pour 800).

---

## 6. Anomalies relevées

### 6.1 Instrumentation et mesures

| N° | Anomalie | Preuve | Conséquence |
|---|---|---|---|
| A1 | **P1 (séchoir) figé à 0,00 mbar** (problème de plage) | toutes les vidéos et relevés | pas de mesure de pression au canal inférieur côté brassage |
| A2 | **P4 figé à −1,18/−1,20 mbar** depuis le 08/10 au moins | vidéos 2, 3, 6 ; relevés | mesure inutilisable |
| A3 | **Capteur de pression de la gaine de récupération HS** (0,00) | PDF 30/09, synoptiques four | la boucle interne de pression de gaine du V1 ne peut pas démarrer |
| A4 | **Mesure du thermorégulateur ASC à 0,0 °C, mode LOCAL** le 28/09 ; ensuite PV 118-128 | capture 28/09, vidéo 5 | à l'époque le brûleur chauffait sans référence |
| A5 | **Échelle de TC3 à vérifier** : Pt100 déclarée 0-160 °C, lecture 220-225 °C le 17/10 | vidéo 3, V1 §1 | si l'échelle est fausse, Q_rec (FB104) et l'anticipation FB106 le sont aussi |
| A6 | **Compteur gaz four** : négatif (général − séchoir) sur toute la période, encore −3 552 Nm³ le 17/10 04:04 ; déclaré fonctionnel le 18/10 | vidéo 4, mémoire | ratio four non mesurable avant le 18/10 ; vérifier la réparation |
| A7 | **Compteur général gaz à impulsions** : index 277, débit 0 | mémoire 08/10, 11/10 | idem |
| A8 | **Centrale « Compresseur »** faux d'un facteur 3,22 jusqu'au 05/10 midi | archive 02/10 | consommation réelle ≈ 70 kW au lieu de 22 |
| A9 | **Pertes de liaison WinCC ↔ automate** : horloge figée, défauts d'extraction et P2 à 0 (11/10 22:21, 16/10 15:57, 17/10 02:12), dérive de 5 min entre CPU | mémoire, vidéos 2 et 3 | archives trouées, consignes non lisibles ; le V1 exige que les boucles soient dans l'automate, pas dans WinCC |
| A10 | **Compteur « cycle séchoir » affiche la moitié du cycle réel** | mémoire | à corriger ou à ignorer au profit de FB102 |
| A11 | **Pas de mesure de température/humidité à la cheminée d'air humide** (capteur C1 à poser ; 45,6 °C au pyromètre le 07/10) | mémoire, V1 | bilan d'air rejeté impossible, boucle L5 inactive |
| A12 | Pas de sonde ambiante (Ta) ; FB104 utilise 30 °C fixe | V1, annexe | erreur sur Q_rec l'hiver |
| A13 | **Archive FC port** bruitée (parasites), REF WAGON TC25 inexploitable, T.Recycl et brûleurs latéraux figés | mémoire 08/10 | FB114 prévoit un anti-rebond 2 s ; les autres signaux ne servent pas |
| A14 | Rapport de poulies du tirage four modifié, dimensions inconnues | mémoire 06/10 | correspondance Hz ↔ tr/min du tirage incertaine |

### 6.2 Conduite actuelle du séchoir

| N° | Anomalie | Preuve | Ordre de grandeur |
|---|---|---|---|
| B1 | **Le brûleur ASC tourne presque en continu, y compris quand la récupération suffit** : 22 h 09/24 le 28/09, 19 h 53 le 16/10, **23 h 27 le 17/10** avec TC3 à 220 °C, T°C1 18 °C au-dessus de la consigne et T°C4 à 262-277 °C | PDF 30/09, vidéos 2-3 | 280-470 Nm³/h de gaz pendant ces heures : l'essentiel des 6 000-8 800 Nm³/j du séchoir |
| B2 | **Le brûleur continue pendant le standby** (chaîne arrêtée) | vidéo 3 (02:11) | chauffe un séchoir qui ne sèche rien |
| B3 | **ASC en MANU la plupart du temps** (16/10 00:48 et 03:03 à 130 °C, 17/10 02:11 à 120 °C), consigne changée à la main (110, 120, 125, 130, 140 °C selon les jours) | mémoire, vidéos | aucune boucle ne peut l'arrêter |
| B4 | **Pompage de T°C4** : 150 ↔ 310 °C, période 8-10 min (16/10), 175 ↔ 285 °C (17/10), pic 315 °C à la reprise | mémoire, V1 §2 | contrainte 250 °C dépassée en permanence ; cause (PID du Gefran ou charge mini du calculateur) non établie |
| B5 | **T°C4 > 250 °C** en marche normale depuis la fermeture du registre arrière à 4 cm (07/10) : 240-270 °C « presque en permanence » du 08 au 11/10, 260-277 °C les 16-17/10 | mémoire, vidéos 3 et 6 | limite de l'exploitant non tenue ; vidéo 6 : 205 → 275 °C en 4 min |
| B6 | **Humidité avant recyclage > 14 %** : 14,4-14,5 % le 16/10 16:51 avec ASC à 112 °C et air chaud 43 Hz ; deux dépassements la nuit du 19/10 avec ASC en butée 125 °C et air chaud 45 Hz ; ≈ 20 % le 16/10 pendant 43 min d'ASC éteint | vidéo 2, V1 §2 | produit insuffisamment séché à l'entrée du recyclage |
| B7 | **Séchage excessif à d'autres moments** : 8,0-8,7 % (vidéo 1), 11,3 % pendant les arrêts avec ASC à 128-130 °C | vidéo 1, V1 | gaz dépensé au-delà du besoin |
| B8 | **Consignes de ventilation réglées à la main et sans cohérence entre pages** : air chaud bornes 36-43 Hz sur 8-13,5 % puis 9-13,5 ; extraction AUTO 30 / MANUEL 44, bornes 39-45 ; recyclage loi proportionnelle 38-46 Hz sur 28-36 % ; rampes 400 s sur l'air chaud ; second PID sur l'humidité avant recyclage à 8 % non activé (butée 46 Hz) | vidéos 2-3 | le V1 (R2, R3) les harmonise |
| B9 | **P3 positif** (+0,14 à +0,24 mbar) sur la vidéo 1, négatif ailleurs | vidéo 1 | canal inférieur en surpression : extraction trop faible ou recyclage trop fort à ce moment |
| B10 | **Standby** : temps réel 7-8 min au lieu des 5 de la recette (07/10) ; temporisations différentes par ventilateur (15 / 20 / 25 min) ; brûleur non arrêté | mémoire, vidéo 3 | R5 du V1 harmonise à 15 min |
| B11 | **Oscillation électrique lente** du séchoir ±50 kW en cycles de 1 à 2 h 30 (régulation proportionnelle du recyclage + standby) | archive 02/10 | perte ≈ 3 kW, mais surtout signe d'une régulation instable |
| B12 | Entrées d'air frais de la chambre calées par une tôle, registre arrière fermé à la main, registre de récupération non motorisé | mémoire | aucun actionneur piloté sur l'air de mélange |

### 6.3 Conduite actuelle du four

| N° | Anomalie | Preuve | Ordre de grandeur |
|---|---|---|---|
| C1 | **Chute de température à chaque poussée** : Turbo 1 −30 à −38 °C, Centrale 1 −15 à −22 °C, retour en 5 à 9 min pour une période de 11-12 min | vidéo 14/10, capture 13-14/10, vidéo 4 | le four passe la moitié de chaque cycle à rattraper ; l'air de combustion reste plein pendant que le gaz est au minimum |
| C2 | **Pression four aux portes** : −1,1 mbar à l'ouverture de la sortie, +2,4 à l'ouverture de l'entrée, pour une consigne de 0,6 | mémoire 05/10, vidéo 4 | air froid aspiré ou fumées refoulées ; FB114 vise 0 à 1,2 mbar |
| C3 | **Récupération bridée à 750 tr/min** (limite du chef four), bornes 40-45 Hz ne faisant varier le débit que de 12 % ; instabilité quand la cadence change | PDF 30/09, mémoire | la source de chaleur la moins chère est plafonnée |
| C4 | **Tirage bridé dans 1 % de plage** (bornes 71-72 %) et conduit en manuel | PDF 30/09, mémoire | pas de réserve |
| C5 | **Recettes automatiques non utilisées**, temps de poussée changé à la main, stock de wagons estimé à l'œil | mémoire | FB110/FB111/détecteurs D1-D6 du V1 |
| C6 | **Pas de mesure d'O₂ des fumées** ; excès d'air inconnu | mémoire 14/10 | levier gaz du four non chiffrable (V1 : 1-3 % du gaz four, à confirmer par E19) |
| C7 | Centrale « Compresseur » fausse jusqu'au 05/10 et compresseur à ≈ 70 kW même fabrication arrêtée (fuites probables) | archive 02/10, V1 §6 | ≈ 20 000 DT/an par 10 kW de fuites |
| C8 | Fabrication à vide : 50-80 kW et 330-480 kVAR, cos φ 0,2 ; gradins saturés en marche, surcompensation (PF 1,1-1,6) aux arrêts | archive 02/10, courbes | jusqu'à 35 000 DT/an si tout était coupé aux arrêts |

### 6.4 Électricité, gaz, archives

- **Ratios** : séchoir 90-226 th/t verte selon les jours (moyenne 160 en septembre), four 280-481 th/t rouge (moyenne 313) ; en 2021 le ratio four était 169 et le global 268-270. L'écart avec 2021 (poussée continue de 11 min, fenêtres fermées, zéro gaz séchoir l'été) montre la marge.
- **Compteur gaz séchoir** en amont du détendeur (côté 3 bar), facteur de correction variable (3,4 à 3,75) : les Nm³ affichés dépendent du facteur retenu par le correcteur.
- **Archives WinCC** : fenêtres de 1 h ou 5 h sans icône horloge sur certaines courbes, « Pas de liaison au serveur de données » permanent, trous d'enregistrement (05/10 05-08 h, 03/10 soir, etc.), courbes figées. Les essais E1-E23 du V1 supposent des archives fiables : préalable 1 du PDF du 30/09 toujours non réglé.

### 6.5 Incohérences entre documents

| N° | Point | Version A | Version B | À trancher |
|---|---|---|---|---|
| D1 | Débit de la gaine de récupération à 750 tr/min | **56 300 m³/h** (FB104, V_REC) | **110 000 m³/h à 619 tr/min** (fiche ventilateurs) ; 96 260 m³/h à 237 °C (audit 2016) ; 49 500-100 100 m³/h selon palier (V1 §5.2) | essai E3 (Pitot) ; l'écart est d'un facteur 2 sur Q_rec |
| D2 | Moteurs d'air chaud | 55 kW (doc technique, audit 2016) | **75 kW** (exploitant) | 75 kW retenu |
| D3 | Dimensions de la gaine | 170 × 170 cm × 70 m | **1,80 × 1,90 × 20 m** (corrigé le 07/10) | corrigé |
| D4 | Rampes des variateurs d'air chaud | 30 s (mémoire 16/10) | **400 s** (vidéo 3, page paramètres) | 400 s lu à l'écran |
| D5 | Mode de l'ASC le 16/10 | MANU 110 °C (mémoire) | AUTO humidité 111 °C à 16:51 (vidéo 2) | le mode a changé dans la journée |
| D6 | Compteurs gaz four | « fonctionnels » le 18/10 (mémoire) | encore négatifs le 17/10 04:04 (vidéo 4) | vérifier après le 18/10 |
| D7 | Gains annuels | dossier 07/10 : 794 à 1 808 kDT/an (jusqu'à −72 % de gaz séchoir) | **V1 : 667 à 1 391 kDT/an** toutes étapes | le V1 est plus prudent et fait foi ; les deux reposent sur des estimations à confirmer par les ratios FB113 |
| D8 | Humidité du recyclage, plage de travail | 25-30 % (recette d'origine), 27-33 % (V1), 34-39 % (essai du 07/10), 28-36 % (page recyclage du 17/10) | — | le V1 part de 30 ± 3 % et prévoit 36,5 après validation |
| D9 | Vitesse de la récupération | 750 tr/min = « vitesse moteur » (exploitant) ; 15 tr/min par Hz, 50 Hz = 750 tr/min (PDF 30/09) ; 100 % = 50 Hz = 1 500 tr/min (annexe FB104 : « 50 % = 750 tr/min ») | — | cohérent si le moteur fait 1 500 tr/min à 50 Hz et que l'affichage est la vitesse moteur ; la fiche donne un ventilateur à 619 tr/min pour un moteur à 1 000 tr/min : à vérifier avec les poulies |

### 6.6 Points à corriger dans le projet V1 et son annexe

| N° | Bloc | Observation | Proposition |
|---|---|---|---|
| E1 | FB104 | V_REC = 56 300 m³/h contredit la fiche ventilateur (voir D1). Toute la logique des régimes A/B/C et la demande D en dépendent | ne pas activer FB104 en automatique avant E3 ; en attendant, calibrer V_REC sur le gaz mesuré (D = gaz/ASC_MAX) plutôt que sur le modèle |
| E2 | FB104 | Ta fixe à 30 °C : l'hiver, Q_rec est sous-estimée de 10-15 % | poser la sonde ambiante C2 (prévue priorité 2) avant l'hiver |
| E3 | FB102 / FB106 | la cadence (clefs/min sur 10 min) est calculée deux fois, avec deux détections d'arrêt (T_arret 180 s dans les deux) | FB106 devrait lire DB102.R10 et DB102.Marche ; sinon risque de divergence si l'un des deux est modifié |
| E4 | FB101 | en standby, recyclage et extraction suivent l'humidité du recyclage (30 + 1,25 (HR − 26)) ; or pendant un arrêt l'humidité du recyclage monte à 35-40 % (07/10) : les deux ventilateurs tendraient vers 40 Hz, soit plus qu'en production | vérifier le sens de la loi en standby par l'essai E13 ; plafonner à la fréquence de production |
| E5 | FB101 | mode 2 « attente » (< 15 min) : ventilateurs et ASC figés, donc le brûleur reste à sa consigne de production pendant 15 min de chaîne arrêtée (cas de la vidéo 3) | abaisser la consigne ASC de 10 °C dès 5 min d'attente, comme le proposait ma note du 17/10 ; 15 min × 350 Nm³/h ≈ 90 Nm³ par arrêt, ≈ 10 arrêts/j |
| E6 | FB107 | zéro gaz interdit en régime C et conditionné à HRa < 12 % ; avec la consigne à 12,5 %, la condition ne sera remplie qu'en récupération haute : cohérent avec « zéro gaz possible seulement l'été », mais le mode ne jouera pas souvent | garder, mais archiver le temps passé en état 3 pour mesurer |
| E7 | FB103 | T_L1 maintient 100 °C jusqu'à 5 min sous 142 °C : pendant ce temps l'humidité peut dépasser 14 % (deux dépassements de la nuit du 19/10 sont venus de l'ASC en butée) | accepter, mais forcer l'air chaud à 45 Hz pendant le maintien (déjà le cas via dF_AC si HRa monte) et alarmer |
| E8 | FB114 | le tirage recentre la contre-pression : deux actionneurs sur une mesure, découplés par les constantes de temps (60 s / 600 s). Correct, mais le tirage est aussi un levier de qualité (préchauffage) tenu manuel jusqu'ici | borner trim_tir à ±5 % au départ (au lieu de ±15) et valider avec le chef four |
| E9 | FB115 | suppose un régulateur de rapport air/gaz par centrale et un variateur par ventilateur : c'est une transformation lourde des centrales (CMI). Le projet signale lui-même que le gaz peut recouper celui de l'excès d'air | commencer par la phase simple : variateur asservi à l'allure existante (min pendant la poussée), sans régulateur de rapport ; FB115 complet après E19/E20 |
| E10 | FB105 | repose sur deux détecteurs inductifs à poser (S_REF, S_CLEF) ; le mode secours par pics d'ampérage utilise un seuil fixe 14 A alors que les pics vont de 15 à 30 A et la base de 0 à 20 | seuil relatif (pic > moyenne mobile + 5 A) en mode secours |
| E11 | V1 §4.6 R1 | « baisser la consigne de 3 °C toutes les 15 min » est confié à l'opérateur en manuel : c'est exactement ce qui n'a pas été fait du 28/09 au 17/10 | passer FB106 en automatique en premier, avant les autres blocs (le V1 le met en étape 2) ; ou, plus simple encore, remettre l'ASC en AUTO humidité avec butée 130 °C dès maintenant (R5) |
| E12 | V1 §7.3 | alarme « ASC sans flamme en production > 5 min » : utile ; il manque l'alarme inverse « ASC en marche séchoir en standby > 15 min » (cas du 17/10 02:11) | ajouter dans FB101 : Mode = 3 AND Flamme → alarme |
| E13 | V1 §8 | TC3 : « échelle 0-250 °C » proposée alors que la Pt100 est déclarée 0-160 °C et lue à 225 °C | vérifier la configuration de l'entrée analogique avant de changer la sonde |
| E14 | Annexe | FB110-FB113 (poussée, recette, récupération par paliers, comptage) ne sont que spécifiés ; FB112 porte pourtant la plus grosse part du gain (R + F : 305-371 kDT) | les écrire en priorité après les blocs séchoir ; FB113 (comptage gaz) dès que les compteurs sont fiables, car il mesure tous les autres gains |

---

## 7. Solutions : ce que le projet V1 règle, et comment

| Anomalie | Réponse du V1 | Bloc / action |
|---|---|---|
| B1-B3 brûleur en continu, en MANU, en standby | consigne continue sur l'humidité avant recyclage, limitée par T°C1/T°C4, zéro gaz, standby avec brûleur arrêté ; réglages R1, R5 sans programmation | FB106, FB107, FB101 ; R1, R5 |
| B4 pompage T°C4 | plafond sur l'enveloppe de T°C4, détection du pompage, essais E8/E9 sur le Gefran et la charge mini | FB107 ; E8, E9 ; liaison A1 |
| B5 T°C4 > 250 | limiteur T_L4, registre arrière ≥ pos_min (jamais sous 8 cm), arrêt critique après 2 min à 250 | FB103 ; R4 ; E6 |
| B6-B7 humidité hors cible | PI sur HRa à 12,5 % avec anticipation cadence + TC3, air chaud +5 Hz/point aux pointes | FB106 |
| B8 réglages dispersés | tables de base par cadence, corrections bornées, une seule page de paramètres | FB104, FB101 ; R2, R3 |
| B10 standby | harmonisé 15 min, standby régulé sur l'humidité, reprise en 10 min avec ASC ≤ 115 °C pendant 20 min | FB101, FB107 ; R5 |
| B12 air de mélange non piloté | registre arrière motorisé (M2), fin de course de la cheminée de récupération (M5) | matériel M2, M5 ; FB103 |
| C1 chutes à la poussée | allure figée à 30 %, intégrale gelée, bonus décroissant ; variateurs sur l'air de combustion | FB115 ; E20 avant achat |
| C2 pression aux portes | pas d'anticipation à l'ouverture, PI à intégrale gelée, retour en rampe | FB114 ; E17 |
| C3 récupération bridée | paliers 0-9 couplés à la contre-pression, demande du séchoir toutes les 10 min, four maître, un palier par semaine | FB112 ; E16 |
| C5 poussée manuelle, stock à l'œil | détecteurs de wagons D1-D6, poussée calculée, recette selon la poussée | FB110, FB111 ; E18 |
| C6 excès d'air inconnu | analyseur O₂ zircone avant le tirage (location possible) | E19 |
| C7-C8 compresseur, moteurs à vide, compensation | fuites d'abord, variateur à pression constante, arrêt réel au-delà de 3 min, réglage du régulateur PF | FB117 ; E21, E22 |
| A1-A3, A11, A12 capteurs | P1, P4, pression de gaine, C1 cheminée, C2 ambiante, 2ᵉ thermocouple sur T°C4 | matériel priorité 1-2 |
| A6-A7 gaz four | comptage gaz four = correcteur − séchoir, ratios par poste et par jour | FB113 |
| A9 WinCC | toutes les boucles dans l'automate ; WinCC n'affiche et n'archive que | principe 7 |

---

## 8. Suggestions complémentaires

### 8.1 Différences entre ma note du 17/10 et le V1, et position retenue

1. **Ventilation avant température ou l'inverse.** Je proposais d'augmenter l'air chaud avant la consigne ASC ; le V1 fait l'inverse en régime établi, en s'appuyant sur le coût du kWh (gaz ≈ 61 millimes, électricité 222-377) et sur le fait que l'air soufflé en plus est de l'air frais à chauffer. L'argument du V1 est le bon sur le coût ; il laisse la ventilation aux pointes, ce qui correspond à mon dF_AC. Position : V1, à confirmer par E12 (40 Hz contre 44 Hz pendant 2 jours chacun).
2. **B1/B2.** Je durcissais leur condition (ASC à 90 % d'abord) ; le V1 conserve la logique 27/33 % par règle de l'exploitant. Position : V1, avec l'option O1 (anticipation) à décider après E7 (part réelle de B1/B2 dans le gaz).
3. **Zéro gaz.** Mon critère était T°C1 > consigne + 8 °C pendant 3 min ; celui du V1 est l'humidité (HRa < 12 % et demande ≤ 112 °C pendant 15 min). Le critère du V1 est plus sûr pour la qualité ; le mien détecte plus vite un excès de récupération. Suggestion : garder le V1 et ajouter mon critère comme **alarme** « récupération excédentaire » (T°C1 > consigne + 8 °C avec ASC en marche), pour mesurer combien d'heures la situation du 17/10 se reproduit.
4. **Récupération.** Demande continue 40-50 Hz (ma note) contre paliers hebdomadaires (V1). Les paliers sont conformes à la contrainte du chef four et plus faciles à suivre en qualité. Position : V1.

### 8.2 Priorités que je recommande de remonter

- **Remettre l'ASC en AUTO humidité, butée 130 °C, dès maintenant** (R5), avant même l'étape 0 : les vidéos 2 et 3 montrent que le mode MANU est la première source de gaspillage. Puis **arrêter le brûleur en standby** (règle de la recette) et vérifier qu'elle s'applique réellement (B2, B10).
- **FB106 et FB107 en automatique en premier**, avant les ventilateurs : ce sont eux qui remplacent la main de l'opérateur sur la consigne (E11).
- **FB113 comptage dès que les compteurs gaz sont fiables** : sans mesure du gaz four, aucun gain du four n'est démontrable.
- **E3 (Pitot) avant d'activer FB104** : l'écart D1 d'un facteur 2 sur le débit de gaine rend la planification des régimes aléatoire.

### 8.3 Compléments au matériel

- **Thermocouple de secours sur T°C4** (déjà prévu) et **sonde redondante sur l'humidité avant recyclage** : c'est la variable de qualité, et le capteur Halstrup-Walcher est un capteur de pression/humidité unique dont la perte (liaison, encrassement) mettrait FB106 en repli.
- **Sonde T + HR à la cheminée** (C1) : au-delà du bilan, elle permet la boucle L5 déjà codée dans FB101 (extraction au juste besoin).
- **Deux détecteurs inductifs sur la chaîne** (S_REF, S_CLEF) : ils fiabilisent la cadence (FB102) et le repérage des blocages (FB105), demande explicite de l'exploitant du 08/10.
- **Analyseur O₂ en location** pour E19 avant tout achat de régulateurs de rapport.

### 8.4 Méthode de mesure des gains

- Un indicateur unique par consommateur : **Nm³ de gaz par wagon** (séchoir et four) et **kWh par wagon**, par poste, calculés par FB113 et archivés, pour neutraliser les variations de production.
- Un **état de référence** de 2 semaines avant l'étape 2 (toutes les boucles en observation) et un bilan de 2 semaines après chaque étape, comme prévu à l'étape 5 du V1.
- Journal des interventions manuelles (changement de consigne, passage en MANU) : la mémoire montre que les consignes ont changé presque chaque jour, ce qui rend toute comparaison fragile.

### 8.5 Points de vigilance qualité

- Avant chaque palier de récupération : porosité (7-7,2), retrait (1,33 %), poids sortie four (5 600-5 700 g), T.refroidissement (bande 620-680 autour de 650), incuit/surcuit sur 3 wagons (E18).
- Avant de baisser durablement la consigne ASC : humidité résiduelle des briques en étuve (E4), car l'humidité avant recyclage n'est qu'un indicateur d'air, pas de produit.
- Ne pas descendre l'extraction en régime A si l'humidité avant recyclage dépasse 13 % (déjà codé dans FB104).

---

## 9. Plan d'action consolidé par priorité

| Rang | Action | Délai | Coût | Référence |
|---|---|---|---|---|
| 1 | ASC en AUTO humidité, butée 130 °C ; standby 15 min partout ; vérifier l'arrêt du brûleur en standby | immédiat | 0 | R5, B1-B3, B10 |
| 2 | Alarmes WinCC T°C1 / T°C4 / HRa / ASC (deux sens) ; cause de l'arrêt du 16/10 22:15 | semaine 1 | 0 | R6, R7, E12 |
| 3 | Registre arrière : jamais sous 8 cm quand l'ASC brûle ; essai E6 par paliers de 2 cm | semaine 1 | 0 | R4, B5 |
| 4 | Liaison brûleur → S7-300 (charge, vitesse d'air, flamme) ; essais E8/E9 sur le pompage | semaines 1-2 | A1 | B4 |
| 5 | Remplacer P1, P4, capteur de gaine ; vérifier l'échelle de TC3 ; poser C1 et C2 ; confirmer les compteurs gaz | semaines 1-3 | capteurs | A1-A7, A11, A12 |
| 6 | Essais E3 (Pitot), E4 (étuve), E5 (K_tour), E7 (part de B1/B2) | semaines 2-3 | 0 | D1, E1 |
| 7 | FB102, FB103, FB106, FB107, FB101, FB104 en observation 7 jours, puis automatique dans l'ordre FB103 → FB106 + sélecteur → FB107 → ventilateurs → zéro gaz | semaines 2-6 | programmation | V1 étapes 1-2 |
| 8 | FB113 comptage gaz four ; FB114 pression/portes en observation puis en auto (E17) | mois 2 | programmation | A6, C2 |
| 9 | FB112 récupération par paliers, un palier par semaine avec suivi qualité ; FB110/FB111 avec détecteurs D1-D6 | mois 2-4 | détecteurs | C3, C5 |
| 10 | E20 (air réduit à la main en poussée) puis variateurs d'air de combustion asservis à l'allure ; O₂ en location (E19) ; FB115 complet seulement si E19/E20 le justifient | mois 3-4 | 8-12 kDT + devis | C1, C6, E9 |
| 11 | Fuites d'air (E21), régulateur PF (E22), arrêt des moteurs à vide, puis variateur compresseur | mois 3-6 | 16-20 kDT | C7, C8 |
| 12 | Mouleuse Morando : eau au malaxeur, niveau de trémie, variateur après E23 ; Lacker vers WinCC | après devis | 95-165 kDT | V1 §6 |

---

## 10. Données encore attendues

- Brûleur ASC : paramètres du Gefran 1600 (bande proportionnelle, intégrale), modèle du calculateur Siemens et signification du 36,2 (charge en % ?), charge minimale, réglages du variateur d'air ; durée de préventilation ; cause de l'arrêt du 16/10 22:15.
- Échelle réelle de TC3 ; état de P4 ; état des compteurs gaz après le 18/10 ; facteur de correction retenu par le correcteur.
- Résultats de la nuit de surveillance du 19/10 (log, courbes, recette B12, pages recyclage et brûleur) : cités dans la mémoire, non reçus.
- Vidéo de la poussée du four du 14/10 ; courbe de centrale avec axe des températures lisible ; zoom 1 h.
- Adresses S7-412 du pousseur, des portes et des futurs détecteurs ; recettes de référence de la poussée ; fréquence maximale admissible de la contre-pression ; bandes qualité du chef four (T.refroidissement, T.récup bas, vitesse maximale de récupération par palier).
- Plaques et réglages des compresseurs ; pressions d'air et de gaz et débit maximal de chaque centrale (CMI) ; dimensions des poulies du tirage.

---

## 11. Annexe A — relevés clés datés

| Date / heure | Séchoir | Four |
|---|---|---|
| 28/09 15:55 | ASC LOCAL, PV 0,0 / SP 119 ; T°C4 142,9 ; TC3 186,4 ; brûleur 15 h 12 sur le poste, 22 h 09 sur 24 h | récup 675 tr/min (40-45), CP 750 (49-54), tirage 1 202 (71-72) ; pression 0,6/0,6 ; T.refroid 681/700 ; T.récup 301 ; P récup 0,00 ; poussée 600 s |
| 02/10 12:44-20:56 | P séchoir 187-308 kW, moyenne 253 ; standby 196 kW (35/38/38 Hz), production 299 kW (47/47/49 Hz) | four 59 kW ; poussée 15 puis 12 min |
| 07/10 17:40-19:10 | registre arrière fermé de 9 cm (reste 4) ; T°C4 190 → 300-313 ; T°C1 129,8-133 ; avant recyclage 68,8 °C / 20 % à 19:10 ; recyclage 39 % / 61 °C ; TC3 105 ; P2 2,74-2,86, P3 −0,08/−0,12, P4 −1,14 | — |
| 08/10 00:24-00:27 | RECY 45, extraction 41 (1 230 tr/min), air chaud 45 ; recyclage 31,3 % / 67,7 ; avant recyclage 75,9 / 13,7 ; extraction 128 / 1,9 ; ASC MANU 131/130 ; T°C1 137,6 ; T°C4 242,4 ; TC3 157,9 ; P2 3,44, P3 −0,11, P4 −1,20 ; brûleur 1 h 49 / 14 h 55 | poussée 720 s, 40 wagons/j ; Turbo 2 809/810, Feu 2 888/890, Feu 1 877/880, Turbo 1 789/790 ; tirage 1 200 ; pression +0,4/+0,5 ; T.récup voûte 233 ; T.refroid 589/650 ; récup 750 ; CP 400 (standby) |
| 11/10 23:20-23:29 | T°C4 260,5 ; T°C1 134,9 ; TC3 145 ; recyclage 35,5 % / 63,5 ; avant recyclage 77,9 / 14,5 ; ASC 126/125 ; brûleur 0 h 49 / 18 h 02 ; défauts extraction, P1-P3 à 0 (perte de signal) | poussée 660 s ; tirage 1 090, P tirage −1,9 ; CP 893 ; pression +0,7/+0,6 ; récup 675 ; T.refroid 620/650 ; T.récup bas 451/500 |
| 16/10 03:03 | air chaud 40/40 Hz (premier relevé avec variateurs), RECY 38, extraction 41, balancelle 42 ; recyclage 30,4 / 68,7 ; avant recyclage 82,0 / 12,6 ; extraction 127,4 / 1,1 ; ASC MANU 130/125 ; T°C1 134,3 ; T°C4 267,4 ; TC3 147,7 ; brûleur 4 h 20 / 19 h 53 | — |
| 16/10 15:56-16:00 | RECY 38, extraction 41, air chaud 40,7-41,2 ; recyclage 30,5 / 64,9 ; avant recyclage 78,3 / 12,2 ; extraction 120,5 / 1,1 ; ASC MANU 119-121/110 ; T°C1 129-132 ; T°C4 242-248 ; TC3 161-165 | poussée 660 s, 43,6 wagons/j ; Turbo 1 795/800, Turbo 2 800/810, Feu 1 871/880, Feu 2 880/890 ; tirage 1 106, P tirage −2,1 ; pression +0,4/+0,7 ; T.récup voûte 257 ; T.refroid 639/650 ; récup 750 ; CP 862-867 |
| 16/10 16:51 (vidéo 2) | ASC AUTO 112-113/111 ; avant recyclage 74,5-75,8 / **13,8-14,5** ; recyclage 32,7-33,6 / 60,5 ; RECY 43 → 41 ; air chaud 43 ; T°C4 155 → 187 ; TC3 153-156 | — |
| 17/10 02:11 (vidéo 3) | ASC **MANU 120**, PV 125-128, **brûleur 23 h 27 / 24 h** ; T°C1 137-139 ; **T°C4 262-277** ; TC3 220-225 ; séchoir en standby, brûleur en marche ; air chaud 41,3-42,1 (36-43, 8-13,5 %, rampes 400 s) ; RECY 38-40 ; extraction 40 | — |
| 17/10 04:00 (vidéo 4) | — | Turbo 1 794/800, Turbo 2 809/810, Feu 1 869/880, Feu 2 888/890 ; poussée 600 s ; gaz four −3 552 Nm³ (compteur HS) |
| 19/10 nuit | −3 °C ≈ +1 point d'humidité ; 12,5 % ≈ 83,5 °C ; deux dépassements de 14 % avec ASC à 125 °C et air chaud 45 Hz ; ASC 128-130 °C pendant les arrêts (11,3 %) | récupération à 825 tr/min la nuit du 19/10 |

## 12. Annexe B — formules et paramètres de départ du V1

- **Cadence** : R10 = clefs/min sur 10 min ; tour = 320 / R10 min ; cycle = K_tour × tour (K_tour ≈ 3) ; r = 2,5 / cycle (h).
- **Fréquences de base** : air chaud et recyclage 45 + 20 (r − 1) Hz ; extraction 41 + 18 (r − 1) ; brassage 47 + 15 (r − 1) ; bornes 25-50, rampes 0,1 Hz/s.
- **Chaleur de gaine** : Q_rec = V_REC × N/750 × 353/(TC3 + 273) × 1,01 × (TC3 − Ta)/3 600 kW, V_REC = 56 300 m³/h (à confirmer) ; besoin Q_need = 1,05 kWh × 15 360 / cycle ; D = (Q_need − Q_rec)/4 070, corrigé par le gaz mesuré (10,52 kWh/Nm³).
- **Consigne ASC (FB106)** : T_HRa = 112 + 1,5 R10 + 0,3 (180 − TC3)⁺ + 2,5 (HRa − 12,5) + I (Ti 8 min), 110-135 °C, +3/−1 °C/min ; air chaud dF = 5 (HRa − 12,5), −4/+6 Hz.
- **Humidité du recyclage (FB101)** : T_HR = 120 + 2 e + (2/600)∫e, e = HR − 30, zone morte ±3.
- **Sélecteur** : T_cons = MIN(MAX(T_HR ; T_HRa) ; T_L1 ; T_L4 ; T_L7 ; 135) ; T_L1 = 135 − 3 (T°C1 − 140) ; T_L4 = 135 − 2 (T°C4 − 230) ; T_L7 = plafond FB107.
- **Registre arrière** : max(30 % ; 60 + 4 (T°C4 − 230)), 100 % dès 245 °C, 0 % si ASC éteint.
- **Zéro gaz** : HRa < 12 % et demande ≤ 112 °C pendant 15 min ; rallumage HRa > 13 % pendant 2 min, immédiat à 13,5 % ou T°C1 < 105 ; 20 min mini.
- **Four, pression** : CP = anticipation palier + 4 %/mbar × e + I (60 s) ± 5 % aux portes ; tirage = base + recentrage (600 s, ±15 %) ∓ 3 % aux portes.
- **Four, centrales** : PID Kp 2,0 (T1, T2) / 1,5 (C1, C2), Ti 180/240 s, Td 20 s ; allure 30 % en poussée ; bonus T1 +20 %, C1 +10 % sur 4 min.
- **Paliers de récupération** : 675 → 1 365 tr/min par pas de 75 (0-9), contre-pression de départ 750 → 1 345 tr/min ; +1 palier si consigne ASC > 128 °C ou bridée, −1 si < 116 °C ; blocages : départ > 290 °C, T.refroid < consigne − 30, CP au max ou à 0, pression hors ±0,2 mbar.
