# BRIQUETERIE JEMMEL
## Requirements — projet BJ ENERGY
### 1. Ce qui est demandé (tests, informations, photos, vidéos, données) · 2. L'application BJ ENERGY à développer

**Document interne de la société Briqueterie Jemmel** — Zone industrielle, route de Zeramdine, Jemmel, gouvernorat de Monastir
Édition 1 — 23 octobre 2026

| | |
|---|---|
| **Émetteur** | Briqueterie Jemmel — Direction technique |
| **Objet** | Section 1 : liste de ce qu'il faut fournir (essais, informations, photos, vidéos, exports) pour que l'assistant Claude voie mieux la situation et aide mieux. Section 2 : cahier des charges de la future application BJ ENERGY (gestion énergétique, check-lists, liaison avec Claude) |
| **Documents liés** | Projet de régulation B12 V1 du 19/10/2026 et annexe programmes ; dossier consolidé du 23/10/2026 ; guide des bonnes pratiques, édition 1 |
| **Destinataires** | Direction, chefs de four et de séchoir, électricien-automaticien, responsable qualité, prestataire de développement |

---

## Sommaire

**Section 1 — Ce qui est demandé pour mieux voir et mieux aider**
1.1 Pourquoi cette liste · 1.2 Essais et mesures · 1.3 Informations et documents · 1.4 Photos · 1.5 Vidéos · 1.6 Exports de données · 1.7 Règles de format et de nommage · 1.8 Priorités · 1.9 Check-list de remise

**Section 2 — L'application BJ ENERGY**
2.1 Finalité · 2.2 Utilisateurs et rôles · 2.3 Modules fonctionnels · 2.4 Liaison avec Claude · 2.5 Architecture technique · 2.6 Modèle de données · 2.7 Sécurité et confidentialité · 2.8 Feuille de route · 2.9 Ce que Claude attend de l'application · 2.10 Critères d'acceptation

---

# Section 1 — Ce qui est demandé pour mieux voir et mieux aider

## 1.1 Pourquoi cette liste

Jusqu'ici, l'analyse s'est faite à partir de captures d'écran, de vidéos filmées sur un écran, d'exports de mémoire et de relevés faits à la main. Cela a suffi pour identifier les grands gaspillages (brûleur en MANU, brûleur en standby, chambre de mélange au-dessus de 250 °C) mais pas pour **chiffrer** avec précision ni pour **régler** les boucles : il manque des débits, des échelles de capteurs, des archives sans trou, des réglages de régulateurs et des vues physiques de l'installation. Cette section liste, par ordre de priorité, ce qui permettrait de passer de l'estimation à la mesure.

Chaque élément indique : ce qui est demandé, pourquoi, sous quelle forme, et sa priorité (P1 = bloquant pour la suite, P2 = nécessaire pour chiffrer, P3 = utile).

## 1.2 Essais et mesures

| N° | Essai | Mode opératoire résumé | Ce que cela fixe | Résultat attendu | P |
|---|---|---|---|---|---|
| T1 | **Débits d'air au tube de Pitot** (ou anémomètre) : gaine de récupération, air chaud, extraction, recyclage | mesure à 3 vitesses (min, normale, max) de chaque ventilateur, sur tronçon droit, 5 points par section | débit réel de la gaine (56 300 ou 110 000 m³/h ?), bases des ventilateurs, courbe Hz → m³/h | tableau Hz / tr/min / m³/h / température par ventilateur | P1 |
| T2 | **Température le long de la gaine de récupération** | thermocouple ou pyromètre : départ (four), après ventilateur, avant chambre de mélange, cheminée ; joints et registre contrôlés | chaleur réellement livrée, pertes de gaine | 4 températures à 3 moments de la journée, photos des fuites | P1 |
| T3 | **Échelle de TC3 et des sondes** | lecture de la configuration de l'entrée analogique dans STEP 7 (plage 0-160 ou 0-250 °C), comparaison avec un thermomètre de référence | validité de TC3 (lue à 225 °C pour une Pt100 déclarée 0-160) | capture de la configuration + mesure de référence | P1 |
| T4 | **Humidité des briques en étuve** | 3 briques en sortie séchoir, pesée, étuve 105 °C jusqu'à poids constant, 3 jours différents | cible réelle de séchage (humidité résiduelle en %) | poids humide / sec, % | P1 |
| T5 | **Cycle réel de séchage** | balancelle marquée, heure d'entrée et de sortie, 3 fois | K_tour (tours par cycle) | durées mesurées | P1 |
| T6 | **Registre arrière de l'ASC** | consigne fixe, registre par paliers de 2 cm (15 min par palier), relevé de T°C4, T°C1, gaz | position minimale admissible, loi registre → T°C4 | tableau palier / T°C4 / gaz | P1 |
| T7 | **Part de B1/B2 dans le gaz** | 30 min ASC seul, 30 min ASC + B2, 30 min ASC + B1 + B2, compteur gaz lu avant/après | consommation réelle de chaque brûleur arrière | Nm³ par configuration | P2 |
| T8 | **Pompage de l'ASC** | 1 h d'enregistrement à 1 s : charge du calculateur, vitesse du variateur d'air, flamme, consigne et mesure du Gefran, T°C4, T°C1, gaz ; une fois TC3 < 190 °C, une fois > 210 °C | cause du pompage (régulateur ou charge mini) | fichier CSV + photos des paramètres | P1 |
| T9 | **Réponse à la consigne ASC** | ± 5 °C pendant 20 min, relevés à 30 s de T°C1, humidité avant recyclage, gaz | gains Kp / Ti de FB106, temps de réponse | CSV | P2 |
| T10 | **Base de l'air chaud** | 2 jours à 40 Hz puis 2 jours à 44 Hz, à cadence comparable | gain électrique net, effet sur l'humidité | kWh/j, Nm³/j, humidités | P2 |
| T11 | **Extraction et brassage** | extraction −2 Hz pendant 1 h ; brassage 47 → 40 Hz par paliers | kW par Hz, utilité du brassage | relevés | P3 |
| T12 | **Reprise douce** | 3 reprises après standby : pic de T°C4, humidité avant recyclage | palier de reprise (115 °C / 20 min) | courbes | P2 |
| T13 | **Contre-pression four** | puissance lue sur le variateur à 50 %, puis à chaque palier | dernier palier de récupération possible | kW par palier | P1 |
| T14 | **Portes du four** | 24 h de pression et de modulation enregistrées à 1 s ; FB114 en observation | pas d'anticipation aux portes | CSV | P2 |
| T15 | **Air réduit à la main pendant la poussée** | sur T1, fermer partiellement le registre d'air pendant 5 poussées ; comparer la chute et le temps de retour avec 5 poussées normales | intérêt des variateurs d'air de combustion | courbes avant/après | P1 |
| T16 | **Excès d'air** | analyseur O₂ (location) dans le caisson avant le tirage, 2 poussées, à 2 allures | consigne O₂, gain gaz du four | % O₂, CO, température fumées | P2 |
| T17 | **Consignes selon la poussée** | poussée ≥ 15 min : T1/T2 −10 °C, contrôle qualité de 3 wagons | table de recettes FB111 | résultats labo | P2 |
| T18 | **Fuites d'air comprimé** | fabrication arrêtée : temps de charge / décharge sur 30 min, détection aux ultrasons | kW de fuites | liste des fuites, kW | P1 |
| T19 | **Compensation** | pendant un arrêt : PF, tension, état des gradins | réglage du régulateur PF | relevés | P3 |
| T20 | **Pression mouleuse** | paliers de 1 bar de 17 à 23 bar à cadence maximale, pièces pesées | consigne, intérêt du variateur | tableau | P3 |
| T21 | **Comptage des clefs** | compteur N/320 comparé au compteur de wagons de l'empilage sur 3 postes | validité du signal de cadence | écart en % | P1 |
| T22 | **Contrôle des compteurs** | gaz : séchoir + four calculé contre le totaliseur sur 24 h ; électricité : I mesuré / I calculé par départ | fiabilité des indicateurs | tableau d'écarts | P1 |

## 1.3 Informations et documents

| N° | Document ou information | Pourquoi | Forme | P |
|---|---|---|---|---|
| I1 | **Projet STEP 7 du S7-300 séchoir** (source complet, blocs, DB, table des mnémoniques, configuration matérielle) | adresses réelles des E/S, logique actuelle (standby, recette brûleur, régulation proportionnelle), intégration des FB101-107 | archive du projet (.zip de l'archive STEP 7) | P1 |
| I2 | **Projet STEP 7 du S7-412 four** | idem pour FB110-115 ; adresses des portes, du pousseur, des variateurs | archive | P1 |
| I3 | **Projet WinCC** (ou au minimum : liste des variables archivées, période d'archivage, pages de recettes) | savoir ce qui est archivé, à quelle fréquence, et ce qui manque | export de la liste des tags + captures des pages recettes | P1 |
| I4 | **Documentation du brûleur ASC** : manuel du calculateur Siemens (référence exacte, signification de l'affichage 36,2), manuel et **liste des paramètres programmés** du Gefran 1600, réglages du variateur d'air, fiche du brûleur (plage de modulation, charge mini) | régler ou expliquer le pompage ; définir la consigne 4-20 mA | PDF constructeur + photos des pages de paramètres | P1 |
| I5 | **Schémas électriques** : TGBT (rapports de TC des centrales de mesure), armoires séchoir et four, variateurs (références, paramètres) | vérifier les mesures, raccorder les nouveaux capteurs et variateurs | PDF ou photos lisibles | P2 |
| I6 | **Plan de la ligne** (P&ID ou croquis coté) : chambre de mélange, gaine, position de chaque capteur (P1-P4, humidités, TC1-TC4), registres, fenêtres | situer les mesures ; aujourd'hui la position de P3 affichée au synoptique est fausse | croquis coté, même à la main | P1 |
| I7 | **Fiches des ventilateurs** (déjà transmise le 02/10) complétée par les **dimensions actuelles des poulies du tirage** | correspondance Hz ↔ tr/min ↔ débit | mesure des poulies | P2 |
| I8 | **Recettes actuelles** : page brûleur, page recyclage, paramètres vitesses, recettes four (consignes par centrale, bornes des ventilateurs), avec les dates de modification | état de référence avant tout changement | captures datées | P1 |
| I9 | **Journal des interventions manuelles** depuis le 28/09 (changement de consigne, passage MANU/AUTO, fermeture de registre, arrêts) | expliquer les courbes | tableau date / heure / action / auteur | P1 |
| I10 | **Rapports journaliers de production et d'énergie** sur 12 mois (Excel), **factures STEG et gaz** sur 12 mois | saisonnalité, référence annuelle, chiffrage des gains | fichiers Excel / PDF | P2 |
| I11 | **Données de la nuit de surveillance du 19/10** (log_sechoir.csv, horaire.csv, gaz.csv, courbes.txt, recette_B12.txt, pages recyclage et brûleur, paramètres vitesses) | citées dans la mémoire, jamais reçues ; elles portent les lois découvertes (−3 °C ≈ +1 point) | fichiers tels quels | P1 |
| I12 | **Contrat et contact CMI Impianti** (constructeur) : allure et débit d'air minimaux des centrales, conditions de garantie si l'on touche à la modulation | prérequis de FB115 | courriel ou fiche | P2 |
| I13 | **Plaques et réglages des compresseurs** (modèles, pressions de charge/décharge, sécheurs, besoins de pression par utilisateur) | FB117 et essai T18 | photos + liste | P2 |
| I14 | **Bandes qualité officielles** du chef four et du responsable qualité : T.refroidissement, T.récup bas, tolérances de zone, porosité, retrait, poids, casse ; vitesse maximale de récupération admise par palier | contraintes à coder dans l'automate | tableau signé | P1 |
| I15 | **Mode de calcul des rapports** (facteur de correction retenu, PCS, répartition des tranches) | cohérence des indicateurs | note | P3 |

## 1.4 Photos

Photos nettes, de jour ou bien éclairées, avec un repère d'échelle quand une dimension compte (mètre ruban dans le champ). Une vue d'ensemble puis un gros plan.

**Séchoir**
- Ph1 Chambre de mélange : les deux fenêtres (avec la tôle), le registre arrière du brûleur (position actuelle, échelle), l'arrivée de la gaine, l'aspiration des ventilateurs d'air chaud.
- Ph2 Gaine de récupération sur toute sa longueur : isolation, joints, registre motorisable, cheminée de secours et son registre, traces de fuite.
- Ph3 Chaque capteur en place avec son environnement : P1, P2, P3, P4, humidité/température « avant recyclage », « recyclage », « extraction », TC1, TC2, TC3, TC4 (plaque signalétique + montage).
- Ph4 Coffret du brûleur ASC : plaque du brûleur, calculateur Siemens (référence et **chaque page de l'afficheur**), Gefran 1600 (**chaque page de paramètres** : P, I, D, type d'entrée, échelle, sortie), variateur d'air (plaque et paramètres principaux), détendeur et pression.
- Ph5 Brûleurs B1 et B2 : coffrets, plaques (même effacées), détendeur commun, électrovannes.
- Ph6 Armoire des variateurs du séchoir : plaques (recyclage Telemecanique 250 kW, air chaud C200, extraction ABB), afficheur avec la liste des paramètres de rampe et de bornes.
- Ph7 Chaîne des balancelles au poste de chargement : poste de montée, clefs, emplacement possible des détecteurs inductifs ; moteur de chaîne et sa plaque.
- Ph8 Cheminées d'air humide (extérieur) : emplacement possible du capteur T/HR.

**Four**
- Ph9 Portes d'entrée, contre-porte et sortie avec leurs fins de course ; pousseur et ses fins de course.
- Ph10 Chaque centrale active (T1, T2, Feu 1, Feu 2) : rampe gaz, électrovannes min/max, servomoteur, ventilateur d'air de combustion (plaque, registre, position actuelle).
- Ph11 Ventilateurs de tirage, récupération, contre-pression : plaques moteur et ventilateur, poulies (diamètres mesurés), variateurs.
- Ph12 Capteur de pression de zone et capteur de pression de gaine (HS) : montage, ligne d'impulsion.
- Ph13 Caisson et cheminée de tirage : emplacement possible du piquage O₂ et de la mesure de température de fumées.
- Ph14 Zone de stockage des wagons entre empilage et four : emplacements possibles des détecteurs D1-D6.

**Électricité et air comprimé**
- Ph15 TGBT : centrales de mesure, transformateurs de courant (rapport marqué), batterie de condensateurs et son régulateur (écran de réglage).
- Ph16 Compresseurs : plaques, régulateurs (écrans de pression charge/décharge), sécheurs, manomètres du réseau.

## 1.5 Vidéos

Les vidéos filmées sur l'écran sont exploitables mais fatigantes à lire ; des **captures d'écran WinCC** (touche Impr. écran, image pleine résolution) sont préférables chaque fois que c'est possible. Quand une vidéo est utile :

| N° | Vidéo | Contenu | Durée | P |
|---|---|---|---|---|
| V1 | **Poussée du four du 14/10** (déjà filmée, 8 min 54 s) | transmettre le fichier d'origine | — | P1 |
| V2 | Une poussée complète filmée sur la page FOUR, de la minute qui précède à 10 min après, avec la courbe de Turbo 1 affichée en zoom 1 h et **l'axe des températures visible** | chiffrer la chute et le rattrapage | 12 min | P1 |
| V3 | Chaque page WinCC (FOUR, SECHOIR, FABRICATION, EMPILAGE, MESURE AMPER, paramètres vitesses, recyclage, brûleur, recettes) filmée fixe 20 s, téléphone **en paysage**, écran entier | état de référence complet | 5 min | P2 |
| V4 | Le brûleur ASC en marche : flamme au hublot, afficheur du calculateur pendant 2 min (lire la charge qui bouge), Gefran | comprendre la modulation | 3 min | P2 |
| V5 | Un cycle de standby et de reprise du séchoir sur la page SECHOIR (de l'arrêt de la chaîne à 10 min après la reprise), en accéléré ou par captures toutes les 2 min | valider FB101 et FB107 | — | P2 |

## 1.6 Exports de données

| N° | Export | Détail | P |
|---|---|---|---|
| D1 | **Archives WinCC sur 14 jours**, 1 valeur / 10 s (ou la période réelle d'archivage), au format CSV, une colonne par variable | séchoir : T°C1, T°C2, T°C3, T°C4, humidités et températures des trois zones, P1-P4, Hz de chaque variateur, consigne et mesure ASC, marche B1/B2, flamme, ampérage chaîne, N/320, gaz séchoir (débit et index) ; four : températures de centrales, pression de zone, pression tirage, T.fumée, T.refroidissement, T.récup (voûte et bas), vitesses tirage/récupération/contre-pression, portes, pousseur, temps de poussée, nombre de wagons ; électricité : P, Q, I, PF par départ et transfo ; correcteur gaz (débit brut, corrigé, pression, température) | P1 |
| D2 | Même export **à 1 s** sur 2 heures choisies : une avec poussées régulières, une avec un standby et une reprise | transitoires | P2 |
| D3 | Tableau des **consommations journalières par poste** (case bleue de MESURE AMPER) sur 60 jours | référence | P1 |
| D4 | Fiches labo (mouleuse, séchoir, four) sur 60 jours | qualité | P2 |
| D5 | Alarmes WinCC (historique) sur 14 jours | pertes de liaison, défauts | P2 |

## 1.7 Règles de format et de nommage

- **Nom de fichier** : `AAAA-MM-JJ_HHMM_lieu_objet.ext` (exemple : `2026-10-24_0930_sechoir_registreASC_gros-plan.jpg`).
- **Photos** : JPG, largeur ≥ 2 000 px, non recadrées ; une plaque signalétique = une photo dédiée, lisible.
- **Vidéos** : MP4, téléphone en paysage pour les écrans, stable (appui sur une table), sans zoom numérique ; 30 s suffisent pour une page fixe.
- **CSV** : séparateur `;`, point ou virgule décimale précisé dans le nom du fichier, première ligne = noms de variables tels qu'affichés dans WinCC, horodatage ISO (`2026-10-24 09:30:10`), fuseau indiqué.
- **Essais** : une fiche par essai (date, heure de début et de fin, conditions : cadence, produit, température extérieure, qui a fait quoi), le résultat brut et la conclusion en une ligne.
- **Un envoi = un lot cohérent** (par exemple « photos séchoir », « export 14 jours »), avec un court texte disant ce que contient le lot et ce qui manque.
- Éviter les doublons : ne pas renvoyer un fichier déjà transmis ; indiquer « déjà envoyé le … » si besoin.

## 1.8 Priorités

**P1 — à fournir avant de programmer quoi que ce soit** : T1, T2, T3, T4, T5, T6, T8, T13, T15, T18, T21, T22 ; I1, I2, I3, I4, I6, I8, I9, I11, I14 ; Ph1-Ph4, Ph9, Ph10, Ph12 ; V1, V2 ; D1, D3.
**P2 — nécessaires pour chiffrer et régler** : T7, T9, T10, T12, T14, T16, T17 ; I5, I7, I10, I12, I13 ; Ph5-Ph8, Ph11, Ph13-Ph16 ; V3-V5 ; D2, D4, D5.
**P3 — utiles** : T11, T19, T20 ; I15.

## 1.9 Check-list de remise

- [ ] Fiches des essais P1 remplies (T1-T6, T8, T13, T15, T18, T21, T22)
- [ ] Archives STEP 7 séchoir et four (I1, I2)
- [ ] Liste des variables WinCC et pages de recettes (I3, I8)
- [ ] Documentation et paramètres du brûleur ASC (I4), photos des pages Gefran et Siemens (Ph4)
- [ ] Croquis coté de la chambre de mélange et de la gaine avec position de chaque capteur (I6)
- [ ] Journal des interventions depuis le 28/09 (I9)
- [ ] Données de la nuit du 19/10 (I11)
- [ ] Bandes qualité signées (I14)
- [ ] Photos P1 (Ph1-Ph4, Ph9, Ph10, Ph12)
- [ ] Vidéo de la poussée du 14/10 et vidéo d'une poussée avec axe visible (V1, V2)
- [ ] Export WinCC 14 jours à 10 s (D1) et tableau des consommations journalières (D3)

---

# Section 2 — L'application BJ ENERGY

## 2.1 Finalité

BJ ENERGY est l'application interne de Briqueterie Jemmel pour **gérer l'énergie au quotidien** : afficher les indicateurs, faire remplir et tracer les check-lists de conduite, consigner les interventions, suivre les essais et le plan d'action, et **s'appuyer sur Claude** pour analyser les données, rédiger les comptes rendus et répondre aux questions à partir des documents du projet.

Elle ne remplace ni WinCC (supervision du procédé) ni les automates (régulation) : elle se situe au-dessus, côté gestion. Elle ne commande jamais un équipement.

Objectifs mesurables :
- chaque poste remplit sa check-list (taux ≥ 95 %) et chaque intervention manuelle est tracée ;
- les indicateurs du jour (Nm³/wagon, kWh/wagon, heures de brûleur, alarmes) sont disponibles à 06:00 sans saisie manuelle ;
- un compte rendu hebdomadaire rédigé avec Claude est prêt chaque lundi ;
- toute question sur le projet (V1, annexe, guide, dossier) obtient une réponse sourcée en moins d'une minute.

## 2.2 Utilisateurs et rôles

| Rôle | Qui | Droits |
|---|---|---|
| Direction | gérant, directeur technique | lecture de tout, validation des changements de consigne et des paliers, export |
| Responsable énergie | directeur technique ou désigné | administration des indicateurs, des check-lists, des essais, du plan d'action ; dialogue avec Claude sans restriction |
| Chef de four / chef de séchoir | responsables de ligne | check-lists hebdomadaires, validation qualité des paliers, journal, consultation des analyses |
| Chef de poste / opérateur | 3 postes | check-list du poste, journal des interventions, consultation des indicateurs et alarmes |
| Électricien-automaticien | maintenance | journal technique, état des capteurs, essais, import des exports WinCC |
| Qualité | laboratoire | saisie des fiches labo, bandes qualité |
| Prestataire | développeur | administration technique, sans accès aux données de production en exploitation |

Accès sur téléphone (opérateurs, chefs de poste), tablette et PC (bureau). Mode hors connexion pour remplir une check-list dans l'usine et synchroniser ensuite.

## 2.3 Modules fonctionnels

### M1 Tableau de bord
- Indicateurs du jour, de la semaine, du mois : Nm³ de gaz par wagon (séchoir, four), th/t verte et rouge, kWh par wagon et par tonne, répartition par tranche tarifaire, puissance maximale appelée sur 15 min vs souscrite, cos φ, heures de marche du brûleur ASC, heures en MANU par équipement, nombre et durée des arrêts, nombre de démarrages de brûleur par heure.
- Comparaison avec l'état de référence et avec la même période de l'année précédente ; objectif affiché par indicateur.
- Courbes simples (7 jours, 30 jours), avec les événements du journal superposés (changement de consigne, arrêt, palier).
- Coût en dinars calculé avec les tarifs en vigueur (paramétrables).

### M2 Check-lists
- Les quatre check-lists du guide des bonnes pratiques (par poste, hebdomadaire, mensuelle, avant tout changement), modifiables par le responsable énergie.
- Chaque item : case cochée / non conforme / sans objet, commentaire, photo, valeur saisie si l'item demande une mesure (ex. « T°C4 actuelle »).
- Signature du chef de poste, horodatage, rappel automatique à l'heure prévue, relance si non remplie.
- Les non-conformités créent une action dans le plan d'action (M6).

### M3 Journal des interventions
- Saisie en 20 secondes : équipement, type (consigne, mode AUTO/MANU, registre, arrêt, maintenance), ancienne et nouvelle valeur, raison, auteur, retour prévu (pour un MANU).
- Alerte de gestion : équipement en MANU depuis plus de 24 h ; consigne modifiée sans validation.
- Le journal est la source des « événements » superposés aux courbes et des explications demandées à Claude.

### M4 Essais et paliers
- Fiche par essai (T1-T22 et E1-E23 du projet V1) : protocole, état (à faire, en cours, terminé), dates, conditions, résultats, pièces jointes, conclusion, paramètre fixé.
- Suivi des paliers de récupération : palier courant, date, contrôles qualité associés, décision.
- Calcul avant/après automatique sur les indicateurs choisis, avec la durée de référence.

### M5 Documents et connaissances
- Bibliothèque : projet V1, annexe programmes, guide des bonnes pratiques, dossier consolidé, audit 2016, fiches constructeur, schémas, photos classées par équipement.
- Recherche plein texte et questions à Claude sur ces documents (voir 2.4).
- Versions et dates ; un document remplacé reste consultable mais marqué « remplacé par … ».

### M6 Plan d'action et gains
- Actions (les 12 rangs du dossier consolidé au départ), responsable, échéance, état, coût, gain attendu et gain mesuré.
- Tableau des gains : par action, en unités physiques puis en dinars, avec la méthode de mesure.

### M7 Alarmes et notifications
- Reprise des alarmes WinCC importantes (T°C1, T°C4, humidité avant recyclage, ASC sans flamme en production, ASC en marche en standby, pression four, pertes de liaison) et des alarmes de gestion (MANU > 24 h, check-list non remplie, compteur aberrant).
- Notification sur téléphone (push) et, pour les critiques, SMS ; acquittement tracé.

### M8 Données et imports
- Import automatique des exports CSV de WinCC (dossier surveillé ou export planifié), des index de compteurs gaz, des fichiers Excel de production, des factures STEG et gaz (saisie des totaux).
- Contrôles à l'import : plausibilité (valeur négative, nulle, figée), trous, doublons ; signalement.
- Phase ultérieure : lecture directe des automates par OPC UA (lecture seule).

### M9 Fiches labo et qualité
- Saisie des fiches mouleuse / séchoir / four, bandes qualité, rapprochement automatique avec les indicateurs du même jour.

## 2.4 Liaison avec Claude

### Ce que Claude fait dans BJ ENERGY

| Cas d'usage | Entrée | Sortie | Fréquence |
|---|---|---|---|
| **Compte rendu de poste** | indicateurs du poste, check-list, journal, alarmes | texte de 10 lignes : ce qui s'est passé, anomalies, actions à faire | à chaque fin de poste |
| **Compte rendu hebdomadaire** | 7 jours d'indicateurs, essais, paliers, journal, fiches labo | rapport structuré (constats, écarts à la référence, recommandations, décisions à prendre) | chaque lundi |
| **Analyse d'un export** | fichier CSV WinCC (14 jours), ou une courbe en image | anomalies détectées (pompage, brûleur en standby, dépassements), chiffrage, hypothèses | à la demande |
| **Questions sur le projet** | question libre de l'utilisateur | réponse sourcée (document, section) à partir de la bibliothèque M5 | à la demande |
| **Aide au réglage** | résultat d'un essai (T6, T8, T9…) | proposition de valeurs de paramètres pour les blocs du V1, avec justification | à la fin d'un essai |
| **Rédaction de protocoles et de fiches** | nom de l'essai, contexte | protocole prêt à imprimer | à la demande |
| **Lecture de photos et de captures** | photo d'une plaque, d'un afficheur, d'une page WinCC | valeurs lues, mises en forme, intégrées au journal | à la demande |
| **Détection d'anomalies en continu** (phase 2) | indicateurs du jour | alerte de gestion avec explication | chaque nuit |

Claude ne commande rien : ses propositions de réglage passent par la validation d'un responsable avant d'être appliquées dans l'automate, comme toute consigne.

### Comment l'application appelle Claude

- **Interface** : l'API Claude d'Anthropic (Messages API), appelée depuis le serveur de l'application avec le SDK officiel (Python ou TypeScript selon la pile retenue en 2.5). Jamais depuis le téléphone ou le navigateur : la clé d'API reste sur le serveur.
- **Modèle** : `claude-opus-5-5` par défaut (raisonnement, lecture d'images et de PDF, 1 M de contexte) ; le réglage d'effort (`low` à `max`) adapte le coût à la tâche : `low` pour un compte rendu de poste, `high` pour une analyse d'export. Un modèle plus léger (`claude-haiku-5-5`) peut servir pour les tâches répétitives simples (lecture d'une plaque, classement), sur décision du responsable énergie après mesure de la qualité.
- **Documents** : la bibliothèque (PDF du projet, guide, dossier) est envoyée une fois par la Files API et référencée ensuite par identifiant ; le **cache de prompt** garde ces documents en préfixe stable, ce qui réduit fortement le coût des questions répétées.
- **Données chiffrées** : les indicateurs et extraits d'archives sont transmis en JSON structuré (section 2.9), pas en captures d'écran, sauf pour la lecture de photos.
- **Réponses structurées** : pour les anomalies, les alertes et les propositions de paramètres, l'application demande une sortie au format JSON validé (structured outputs), que le serveur enregistre directement dans la base ; le texte libre est réservé aux comptes rendus.
- **Outils** : pour répondre à une question (« combien d'heures de brûleur hier ? »), Claude peut appeler des fonctions de lecture exposées par l'application (lire un indicateur, lire le journal sur une période, lire un essai) ; aucune fonction d'écriture n'est exposée en phase 1.
- **Traitements de nuit** : les comptes rendus et la détection d'anomalies s'exécutent en lot (Batch API, moitié prix, sans contrainte de latence) ; une alternative pour le rapport hebdomadaire est un agent planifié (Managed Agents), à décider en phase 2.
- **Refus et replis** : l'application gère le cas où le modèle décline une demande (réponse avec motif) et le repli serveur proposé par l'API ; une erreur d'appel n'empêche jamais l'enregistrement d'une check-list ou d'un journal.
- **Coût** : au tarif public de `claude-opus-5-5` (4 $ par million de jetons en entrée, 20 $ en sortie, cache en lecture 0,20 $), un compte rendu de poste (≈ 20 000 jetons en entrée avec cache, 1 000 en sortie) coûte quelques centimes ; une analyse d'export de 14 jours (≈ 300 000 jetons) autour d'un dollar ; une question sur les documents, avec cache, quelques centimes. Un budget mensuel plafonné et un compteur de consommation sont affichés au responsable énergie.
- **Journalisation** : chaque appel est tracé (date, utilisateur, cas d'usage, jetons, coût) ; les réponses de Claude sont conservées avec la version des documents et des données utilisées.

## 2.5 Architecture technique

| Couche | Choix proposé | Remarque |
|---|---|---|
| Interface | application web responsive (PWA) installable sur téléphone, tablette et PC ; mode hors connexion pour les check-lists et le journal | une seule base de code ; pas de boutique d'applications |
| Serveur | Python (FastAPI) ou TypeScript (Node) — à trancher avec le prestataire ; API REST ; tâches planifiées (imports, comptes rendus de nuit) | le SDK Anthropic existe pour les deux |
| Base de données | PostgreSQL ; extension séries temporelles (TimescaleDB) pour les archives WinCC | sauvegarde quotidienne hors site |
| Fichiers | stockage objet local ou cloud pour photos, PDF, exports | chiffré au repos |
| Connecteur WinCC | phase 1 : dossier d'export CSV surveillé (export planifié par WinCC) ; phase 2 : OPC UA en lecture seule vers les S7 | aucune écriture vers les automates |
| Claude | service serveur dédié (file d'attente, limitation de débit, cache, journal des appels) | clé d'API en variable d'environnement, jamais dans le code |
| Hébergement | serveur de l'usine (onduleur) ou cloud avec VPN ; nom de domaine interne ; HTTPS | les pertes de liaison constatées sur WinCC plaident pour un serveur local avec synchronisation différée |
| Authentification | comptes nominatifs, rôles (2.2), mot de passe + code à usage unique pour les rôles d'administration | journal des connexions |

## 2.6 Modèle de données (principales entités)

- **Équipement** (séchoir, four, ventilateur, brûleur, compteur…) : nom, repère, plaque, documents.
- **Variable** : nom WinCC, unité, équipement, plage valide, fréquence d'archivage.
- **Mesure** : variable, horodatage, valeur, qualité (valide / douteuse / figée).
- **Indicateur** : définition (formule sur mesures et production), période, valeur, référence, objectif.
- **Production** : poste, produit, wagons, tonnage vert / rouge, arrêts.
- **Check-list** : modèle, instance (date, poste, auteur), items (état, valeur, commentaire, photo), signature.
- **Intervention** (journal) : équipement, type, avant/après, raison, auteur, horodatage, validation.
- **Essai** : référence, protocole, état, conditions, résultats, pièces jointes, paramètre fixé.
- **Palier** : équipement, valeur, date, contrôles qualité, décision.
- **Alarme** : source, niveau, début, fin, acquittement.
- **Action** : plan d'action, responsable, échéance, état, gain attendu / mesuré.
- **Document** : titre, version, fichier, date, remplacé par.
- **Appel Claude** : cas d'usage, utilisateur, entrées (références), sortie, jetons, coût, horodatage.

## 2.7 Sécurité et confidentialité

- Données de production et d'énergie = données internes de la société : accès par rôle, journalisation des consultations sensibles, export limité à la direction et au responsable énergie.
- Transmission à Claude limitée au nécessaire (indicateurs, extraits, documents du projet) ; pas de données personnelles des salariés dans les prompts (le journal transmis à Claude porte les rôles, pas les noms, sauf accord).
- Clé d'API stockée côté serveur, rotation semestrielle, quota mensuel.
- Sauvegardes chiffrées, test de restauration trimestriel.
- Aucune liaison en écriture vers WinCC ni vers les automates : l'application lit, elle ne commande pas.

## 2.8 Feuille de route

| Phase | Contenu | Durée indicative | Critère de fin |
|---|---|---|---|
| **MVP** | M2 check-lists, M3 journal, M5 bibliothèque + questions à Claude, M1 tableau de bord alimenté par saisie et import Excel, M6 plan d'action | 8 à 10 semaines | 3 postes remplissent leur check-list pendant 2 semaines ; 20 questions testées avec réponses sourcées |
| **V1** | M8 import automatique des CSV WinCC, M1 complet, M7 alarmes et notifications, M4 essais et paliers, comptes rendus de poste et hebdomadaires par Claude | + 8 semaines | indicateurs à 06:00 sans saisie ; rapport du lundi validé 4 semaines de suite |
| **V2** | OPC UA lecture seule, détection d'anomalies de nuit, M9 qualité, agent planifié pour le rapport hebdomadaire, tableau de bord direction | + 8 semaines | anomalies détectées avant l'équipe du matin sur 4 semaines |

Avant le MVP : choix de la pile technique, maquettes des écrans de check-list et de journal validées par deux chefs de poste, liste définitive des indicateurs et de leurs formules (avec le responsable énergie), accès à un export WinCC réel pour construire l'import.

## 2.9 Ce que Claude attend de l'application

Pour que les analyses soient fiables et peu coûteuses, l'application fournit à Claude :
- des **noms de variables stables** (les noms WinCC, documentés dans la bibliothèque, avec unité et position physique) ;
- des **horodatages ISO** avec fuseau, et une seule convention décimale ;
- des **données déjà contrôlées** (plausibilité, trous signalés) : Claude ne doit pas deviner si un 0,00 est une mesure ou une perte de liaison ;
- le **contexte** de chaque période : produit, cadence, arrêts, interventions du journal, température extérieure ;
- les **bandes qualité et les limites** en vigueur (version datée) ;
- pour une analyse, un **objectif explicite** (« chiffrer le gaz brûlé pendant les standbys de la semaine ») plutôt qu'un fichier brut sans question ;
- un **format de réponse attendu** (JSON pour les alertes et paramètres, texte pour les comptes rendus) et la liste des documents de référence à utiliser.

Exemple de structure d'envoi pour une analyse :
```json
{
  "objectif": "chiffrer le gaz brûlé par l'ASC pendant les standbys",
  "periode": {"debut": "2026-10-17T00:00:00+01:00", "fin": "2026-10-23T23:59:59+01:00"},
  "contexte": {"produit": "B12", "cadence_moy_wagons_j": 43, "arrets": [...], "interventions": [...]},
  "variables": ["ASC_consigne", "ASC_mesure", "ASC_flamme", "Chaine_I", "Gaz_sechoir_Nm3h", "TC3", "TC4", "TC1"],
  "donnees": "fichier CSV joint (10 s), 7 jours, contrôlé : 2 trous signalés",
  "limites": {"TC1_max": 145, "TC4_max": 250, "HRa_max": 14},
  "reponse_attendue": {"format": "json", "schema": "anomalies_v1"}
}
```

## 2.10 Critères d'acceptation

- Une check-list de poste se remplit en moins de 3 minutes sur téléphone, hors connexion, et se synchronise sans perte.
- Une intervention se saisit en moins de 30 secondes et apparaît sur les courbes.
- Les indicateurs du jour sont calculés automatiquement à partir d'un export WinCC réel, avec les mêmes résultats que le calcul manuel (écart < 1 %).
- Une question posée à Claude sur le projet V1 renvoie la réponse avec la référence du document et de la section ; dix questions de test validées par le directeur technique.
- Le compte rendu hebdomadaire généré est jugé « utilisable sans réécriture » par la direction quatre semaines de suite.
- Aucun appel à Claude n'est possible sans compte authentifié ; le coût mensuel est visible et plafonné.
- Aucune fonction de l'application n'écrit vers WinCC ou vers un automate (vérifié par revue de code).

---

*Briqueterie Jemmel — Requirements BJ ENERGY, édition 1 du 23/10/2026. Document vivant, mis à jour à chaque lot reçu et à chaque phase de l'application.*
