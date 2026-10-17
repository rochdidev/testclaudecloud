# Mémoire Claude — export complet du 17/10/2026

## Préférences
- Projet briqueterie (dossier PDF, blocs automate) : ne lui envoyer les fichiers du projet que lorsqu'il le demande ; les mettre à jour sans les envoyer
- Quand il donne une information à noter ou une correction : l'enregistrer et répondre sans commentaire, sauf s'il donne la permission de parler

## Profil
- A une usine de briqueterie (« mon usine briqueterie »)

---

# 1. Briqueterie — régulation (synoptique, projet four et séchoir)

- projet à venir : développer un système de régulation automatique du four et du séchoir de la briqueterie
- veut que les discussions sur ce sujet soient gardées en mémoire pour la suite du projet
- supervision : synoptique de consommation électrique avec centrale de mesure transformateur N1&N2 et départs Préparation, Fabrication, Séchoir, Four, Compresseur ; régulation du cos φ par 3 gradins de condensateurs
- les arrêts pour changement de filière font partie du fonctionnement de la ligne de fabrication
- four : seule la recette manuelle fonctionne actuellement (recettes auto par temps de poussée non opérationnelles) ; produit actuel B12
- la préparation s'arrête quand les stockeurs sont pleins
- dispose des fiches constructeur des ventilateurs four et séchoir (air chaud, recyclage, air humide, tirage, récupération, contre-pression)
- deux transformateurs de 800 kVA chacun (N1 et N2)
- deux mouleuses (donc deux malaxeurs) ; une seule mouleuse est couplée en lecture sur la supervision
- séchoir : 4 brûleurs. Brûleur 1 (celui de la « mesure ASC brûleur ») = brûleur principal, en marche ; 2 modes : manuel et auto humidité (suit la progression d'humidité, cf. page recette séchoir)
- séchoir : brûleur 2 en arrêt permanent (bouton OFF activé)
- séchoir : 2 brûleurs à l'arrière du séchoir, fonctionnent simultanément ; 2 modes : manuel (régulé en température) et automatique (suivant l'humidité)
- séchoir : le compteur « cycle séchoir » est erroné, il faut doubler le temps affiché pour avoir le cycle réel
- séchoir : capteur de pression P1 erroné, à remplacer ; P3 remplacé, installé et fonctionnel (confirmé le 06/10/2026, lecture −0,13 mbar) ; P3 est réellement placé dans le canal inférieur, à côté du capteur d'humidité, avant les ventilateurs de recyclage (position sur le synoptique à corriger très prochainement)
- séchoir : 2 moteurs de recyclage (90 kW, 1000 tr/min chacun) sur variateur de fréquence qui suit la recette activée (page Recyclage)
- séchoir : les 3 ventilateurs N°1, N°2, N°3 fonctionnent simultanément sur un seul variateur et suivent la recette brassage selon le mode activé
- séchoir : grand brûleur (mesure ASC) puissance nominale 3500 thermies/h, avec détendeur gaz, pression de service 150 mbar
- séchoir : brûleurs B1 et B2 (arrière séchoir) pression de service 60 mbar chacun
- séchoir : les 3 ventilateurs d'extraction air humide fonctionnent sur un seul variateur (même comportement)
- séchoir : 2 ventilateurs air chaud (moteurs 2 × 75 kW, 1000 tr/min) ; variateurs de vitesse installés et fonctionnels (16/10/2026)
- séchoir : ventilateurs de brassage (N°1-3) moteurs 4 kW, 1500 tr/min, roue Ø 80 cm, entraînés par poulies (dimensions inconnues), sur variateur (47 Hz relevé, page recette brassage) ; placés sous les ventilateurs d'extraction air humide (≈ 6 m), ils aspirent l'air du compartiment production
- essai brassage 47 → 35 Hz (04/10/2026, séchoir en marche, production en cours, brûleur ASC fermé) : T°C1 n'a augmenté que de 5 °C
- séchoir : T°C1 = température de l'air soufflé dans le canal inférieur, située à environ 8 m des ventilateurs de brassage N°1-3
- séchoir : TC3 = arrivée de la gaine de récupération du four au séchoir ; une gaine alimente le canal inférieur du séchoir depuis la gaine de récupération, sans mesure de température ; son ventilateur (moteur 15 kW, 1500 tr/min) tourne en continu sans variateur
- séchoir : capteur de pression P2 nouvellement installé
- séchoir : capteur humidité/température de la zone recyclage fonctionne ; capteur « zone avant recyclage » = humidité du canal inférieur avant recyclage
- séchoir : humidité zone avant recyclage à garder en dessous de 14 % au maximum
- séchoir : capteur humidité/température « zone extraction » situé à peu près au milieu du canal inférieur ; T°C4 = température de la chambre de mélange
- four : capteur de température « T récupération » installé au début de la gaine de récupération (envoi vers le séchoir) ; thermocouple de sortie four affiché sur le synoptique
- four : capteur de pression de la gaine de récupération (position départ, avant ventilateur de récupération) ne fonctionne pas, à remplacer
- gaz : un totaliseur (correcteur de gaz) compte la consommation de toute l'usine ; parmi les compteurs gaz de la supervision, seul celui du séchoir fonctionne, les autres (général, four) sont défectueux
- dispose d'un tableau d'examen qualité du produit B12 (poids, dimensions, retrait, perte de poids) en sortie mouleuse, séchoir et four ; une page recette « Brûleur » règle le fonctionnement interne du brûleur ASC
- la production verte et rouge varie chaque jour à cause des arrêts non programmés
- dispose d'un rapport mensuel de consommation électrique (kWh par tranche horaire, tonnage vert/rouge, ratio kWh par tonne et coût)
- dispose de rapports mensuels de consommation gaz : un pour le séchoir (consommation, tonnage, ratio gaz séchoir) et un pour le four (ratio four et ratio global four + séchoir)
- tarifs énergie STEG inchangés à ce jour (référence : factures transmises) : électricité MT jour 290, pointe 377, nuit 222 millimes/kWh HT, puissance souscrite 1200 kW (installée 1600 kVA), prime de puissance 13 200 DT/mois ; gaz 70,5 millimes/thermie HT, PCS ≈ 10,05 th/Nm³, débit souscrit 12 500
- rapports gaz four de 2021 (ancienne référence, décembre et janvier) : ratio moyen four 169, ratio moyen global ≈ 268–270, production ≈ 475–500 t/jour
- séchoir semi-continu à balancelles : 2 galeries superposées, 64 balancelles à plusieurs étages tirées par chaînes, longueur 82 m, largeur 6,35 m (utile 5 m) ; cycle normal 3 h à 50 min min ; doit être alimenté en continu 24/24 (arrêts → casse/déformation)
- séchoir : objectif humidité produit < 3 % du poids sec en sortie ; air chaud du four + chambre de combustion avec brûleur, circulation à contre-courant ; brûleur d'appoint en zone de recyclage
- séchoir (doc technique) : introduction chaud 2 × 165 000 m³/h (2 × 55 kW), recyclage 2 × 180 000 m³/h (2 × 90 kW), générateur de chaleur 3 500 th/h, tirage final 3 × 165 000 m³/h (3 × 30 kW) avec variateur, ventilateur brassage four 11 kW, ventilateur récupération 15 kW
- pour des contraintes clients, l'usine ne produit que du B12 : se limiter au B12 pour le projet de régulation
- séchoir : pas de mesure de l'humidité résiduelle en pourcentage ; les ≈ 300 g par pièce B12 sont un constat, pas une cible
- séchoir : la supervision archive la marche et la vitesse des balancelles (tendance « Balancelle ») ainsi que l'ampérage de la chaîne (max / actuel, seuil de blocage)
- séchoir circulation d'air : l'air entre par le canal inférieur côté air chaud et sort par le canal supérieur côté air humide, à contre-sens de la circulation des briques sur les balancelles
- séchoir : les ventilateurs d'air chaud aspirent directement dans la chambre de mélange, sans dilution avant
- séchoir : la chambre de mélange reçoit l'air de récupération du four + de l'air frais (2 fenêtres existantes à côté du brûleur ASC) ; le brûleur ASC a un registre arrière, ouvert quand il fonctionne, par lequel entre l'air ambiant
- séchoir : entrée d'air frais non réglable actuellement ; prêt à installer registres et vérins à commande numérique si nécessaire
- séchoir : registre existant sur l'air de récupération, à motoriser par servomoteur
- séchoir : temps de réponse approximatif ≈ 5 min entre un changement de consigne et son effet sur l'humidité du recyclage
- séchoir : demande des instructions complètes pour la régulation (motorisation des registres, PLC, etc.) à fournir en bloc
- séchoir : brûleur ASC modulant ; B1 et B2 non modulants
- séchoir : le compteur gaz du séchoir mesure toute la consommation gaz du séchoir en bloc (3 brûleurs)
- variateurs : recyclage = 1 variateur Telemecanique 250 kW ; air chaud = 2 variateurs Control Techniques C200 90 kW (achetés sept. 2026, installés et fonctionnels le 16/10/2026 ; relevé 03:03 : air chaud +40,00 Hz sur chaque variateur, recyclage 38 Hz, air humide 41 Hz, balancelle 42 Hz) ; autres variateurs non connus pour l'instant
- automates : Siemens S7-300 pour le séchoir, S7-400 pour le four (supervision WinCC)
- automate séchoir programmé sous STEP 7 ; a le projet source et l'autorisation de modifier le programme
- capteurs de pression et d'humidité du séchoir : marque Halstrup-Walcher (fournisseur Fisme) ; pression type PIZ 0–5 mbar, 4–20 mA, ±1 %, 24 VDC ; températures : Pt100 et T°C4 en thermocouple K
- arrêts non programmés estimés à environ 5 h par jour
- priorité du projet séchoir : baisser la consommation de gaz et d'électricité du séchoir en gardant la cadence et la qualité ; le ratio séchoir varie de 90 à 160 thermies par tonne
- tableaux de septembre 2026 (four et séchoir) fournis le 04/10/2026
- cycle de séchage réel du B12 ≈ 2 h 30 (valeur affichée × 2), variable selon les arrêts
- ventilateurs d'air chaud : fonctionnent depuis des années en aspirant directement dans la chambre de mélange (~224 °C) ; ne pas en faire un point bloquant pour le projet
- ventilateurs d'air chaud : moteurs existants 2 × 75 kW (le document indiquant 55 kW est erroné) ; variateurs 2 × 90 kW achetés par sécurité
- séchoir : casse au séchage quasi nulle
- écart poids sortie séchoir − poids sortie four ≈ 300 g par pièce B12 : c'est un constat, pas une cible
- vitesse des balancelles exprimée en Hz (lisible sur la courbe Balancelle)
- pendant les arrêts, les briques restent dans le séchoir ; tous les brûleurs sont en arrêt total dès que le séchoir entre en standby (recette brûleur) ; recyclage et air humide baissés manuellement à 30 Hz, le reste inchangé
- recette brûleur ASC (auto humidité) : consigne de température basculant entre 110 et 120 °C selon l'humidité du recyclage entre 25 % et 30 % ; cette recette est modifiée par le responsable production
- brûleur ASC : a son propre régulateur et reçoit aussi une consigne du S7-300 par sortie analogique 4-20 mA
- brûleurs B1 et B2 : tout-ou-rien, consommation gaz ≈ 60 Nm³/h chacun (puissance estimée à 50 kW chacun)
- séchoir : les 2 fenêtres d'air frais à côté du brûleur ASC sont calées fermées par une tôle depuis fin sept. 2026 pour réduire l'entrée d'air
- chambre de mélange : fenêtre 1 = 144 × 117 cm, fenêtre 2 = 133 × 130 cm ; registre brûleur ASC = 170 × 166 cm ; gaine de récupération du four à la chambre de mélange = 132 × 132 cm
- ventilateur de récupération du four vers la gaine / chambre de mélange du séchoir : moteur 45 kW (fiche Excel des ventilateurs transmise le 02/10/2026)
- la régulation du séchoir doit s'appuyer sur des tableaux de conduite par cycle et température (fréquences air chaud / recyclage), comme ses tableaux « Cycle … : ventilateurs d'air chaud et de recyclage avec variateur »
- automate séchoir : cartes d'E/S libres disponibles, dont SM332 AO 8×12 bit (6ES7 332-5HF00-0AB0) et SM331 AI 8×RTD (6ES7 331-7PF00-0AB0)
- B1/B2 : puissance inconnue, plaque effacée
- prêt à acheter toutes les cartes d'E/S jugées utiles pour l'automate
- variateurs commandés par Profibus ; variateur de l'air humide (extraction) de marque ABB
- sondes de température du séchoir : Pt100, échelle 0 à 160 °C, sauf T°C4 (chambre de mélange) qui est un thermocouple de type K, échelle 0 à 360 °C
- liaison entre les automates (S7-300 séchoir et S7-400 four) : Profibus
- séchoir : P2 est dans le canal supérieur, à environ 2 m à droite (côté cheminées) du capteur d'humidité du recyclage ; P1 non fonctionnel
- pas de sonde de température/humidité ambiante extérieure actuellement ; prêt à en installer si nécessaire
- la centrale électrique « Séchoir » mesure tous les ventilateurs du séchoir et la chaîne des balancelles
- automate séchoir : CPU S7-300 de type 317
- démarche du projet : traiter d'abord le séchoir (questions), puis le four, et ensuite rédiger l'ensemble (séchoir + four) en un seul bloc ; démarche séchoir proposée (récupération four = source principale, ASC appoint, B1/B2 dernier recours, ventilateurs au juste besoin, arrêts automatisés) présentée
- four : le champ « nombre de wagons 40 » = nombre de wagons à produire en 24 h à la cadence de poussée actuelle ; « 30 wagons » = réalisé de la veille (01/10/2026)
- four : chaque wagon porte 3 piles de briques ; temps de séjour = nombre de wagons × temps de poussée × 3
- four : 2 160 briques B12 par wagon
- four : seules les centrales de brûleurs T1, T2, 1 et 2 fonctionnent ; les centrales 3, 4, 5 et 6 sont en arrêt continu
- four : les valeurs min et max des ventilateurs (tirage, récupération, contre-pression) sont en pourcentage de la fréquence variateur (100 % = 50 Hz)
- four : centrales 3 à 6 arrêtées parce qu'elles sont inutiles (choix de conduite, pas de panne)
- four : 26 wagons dans le four ; la « poussée 10,4 » de la fiche qualité est une erreur humaine (poussée réelle 12 min)
- four : 12 brûleurs par centrale, tous modulants, en voûte
- four : défauts de cuisson variés (incuit, surcuit, etc.)
- four : mode de calcul du ratio gaz four inconnu ; prêt à réparer le compteur gaz du four si nécessaire
- four : ventilateurs de tirage, récupération et contre-pression sur variateurs Telemecanique en Profibus
- four : récupération déjà poussée au-delà de 45 % avec de bons résultats, mais instabilité quand la cadence de poussée change
- four : a l'autorisation de modifier le programme de l'automate du four (CPU S7-412)
- four : recettes automatiques non utilisées car le technicien veut intervenir à chaque fois
- four : stock tampon de wagons parfois présent, parfois non ; lors des arrêts la poussée ralentit la plupart du temps, jusqu'à 60 min
- gaz four : peut être calculé par soustraction totaliseur usine − compteur séchoir
- four : le temps de poussée est toujours changé manuellement par l'opérateur
- gaz : le four et le séchoir sont les seuls consommateurs de gaz de l'usine
- empilage : empilage des wagons de produit séché à la sortie du séchoir ; chaque wagon empilé = 2 160 pièces en 3 piles ; synoptique Empilage disponible (wagons par poste et par 24 h, temps par wagon, archive des wagons)
- exigence séchoir : pendant une attente d'alimentation par la mouleuse (avant la fin du temps de standby), tous les ventilateurs doivent continuer à fonctionner ; à la fin du standby, il faut une régulation qui dépend de l'humidité existante dans le séchoir
- four : le capteur « T récupération » qui affiche ~425 °C est installé en voûte du four, au niveau de la dernière zone de feu (pas dans la gaine du ventilateur de récupération)
- four : la « Régulation en Auto » actuelle = PID de température par centrale (modulation des brûleurs) + PID de pression agissant sur tirage et contre-pression
- four : CPU S7-412 ; thermocouples de température du four de type K
- four : air de combustion des brûleurs par ventilateurs externes, moteurs 7,5 kW 1500 tr/min (puissance ventilateur inconnue)
- four : ventilateurs de refroidissement rapide arrêtés car inutiles
- four : le stock de wagons entre empilage et entrée du four est actuellement évalué à l'œil (pas de comptage par capteurs)
- four : seul le capteur de pression qui affiche zéro (récupération) est défectueux
- four : pas de cibles chiffrées de porosité/retrait ni de norme client
- four : un ventilateur d'air de combustion (7,5 kW) par centrale
- gaz usine : détendeur d'entrée 3 bar absolu, sortie 500 mbar vers la rampe du four ; chaque centrale a une électrovanne (entrée max 500 mbar) avec sortie réglée à 360 mbar (T1), 320 (T2), 300 (Feu 1), 300 (Feu 2)
- gaz séchoir : détendeur d'entrée 3 bar absolu, sortie réglable 300 mbar vers les brûleurs ; B1/B2 ont un seul détendeur commun qui affiche 60 mbar en sortie
- poste WinCC unique : pour la lecture des courbes WinCC (option 2), Claude travaille sur le PC par sessions ; dès qu'un partage de connexion ou un mouvement de souris est constaté, il laisse la main, et ne reprend qu'après 3 min sans mouvement de souris
- objectif : arriver à éliminer totalement la consommation de gaz du séchoir
- zéro gaz au séchoir déjà atteint en juillet et août 2021, avec une poussée continue de 11 min et toutes les fenêtres de la chambre de mélange fermées, y compris le volet du brûleur ASC
- pendant la période zéro gaz séchoir (juillet-août 2021), température ambiante ≈ 46 °C à midi et ≈ 32 °C le soir
- des coupures de connexion à WinCC surviennent parfois, dues notamment aux coupures électriques STEG
- séchoir : 64 balancelles × 5 étages × 48 pièces (2 × 24) par étage = 15 360 pièces B12 dans le séchoir plein
- cadence maximale : jusqu'à 60 wagons B12 en 24 h en sortie séchoir, et 60 wagons au grand maximum pour le four ; jamais atteinte à cause des problèmes de production
- empilage : temps minimum d'environ 20 min par wagon
- séchoir : les 15 360 places sont toutes chargées ; un compteur de wagons au poste empilage est disponible (compte les wagons empilés)
- B1/B2 : en mode manuel régulés sur la température (courbe « brûleur à point ») ; en mode automatique ils suivent l'humidité 25/30 % : arrêt en dessous de 25 %, redémarrage seulement au-dessus de 30 %
- décision : maintenir le fonctionnement actuel de B1/B2 et réguler le brûleur ASC, qui porte l'essentiel de la consommation gaz du séchoir
- séchoir : l'air entre par la chambre de mélange et par les 3 ventilateurs de brassage (canal inférieur), circule de droite à gauche vers le recyclage, monte au canal supérieur vers les 3 ventilateurs d'air humide à droite (cheminées) ; température et humidité de sortie finale inconnues, un capteur sera installé
- cadence étudiée (oct. 2026) : 18 wagons par poste à l'empilage ; four à 10 min de poussée, soit 48 wagons/24 h
- contrainte du responsable four : ventilateur de récupération à ne pas dépasser 750 tr/min, pour la qualité
- fiche ventilateurs (moteur / poulies / ventilateur / débit / puissance absorbée / Tmax) : air chaud 2×75 kW 1000 tr/min 300/630 → 480 tr/min, 2×145 000 m³/h, 2×53 kW, 160 °C ; recyclage 2×90 kW 300/530 → 546 tr/min, 2×180 000 m³/h, 2×77 kW, 95 °C ; air humide 3×37 kW 1500 tr/min 212/355 → 882 tr/min, 3×165 000 m³/h, 3×32 kW, 45 °C ; tirage four 37 kW 180/400 → 666 tr/min, 85 000 m³/h, 32,2 kW, 250 °C ; récupération 45 kW 224/530 → 619 tr/min, 110 000 m³/h, 42 kW, 300 °C ; contre-pression 22 kW 212/450 → 459 tr/min, 85 000 m³/h, 17 kW, 40 °C
- mesure du 01/10/2026 : 7 113 Nm³ de gaz séchoir, 38 wagons, 17 h 25 de marche ; consigne de soufflage ASC 115 °C (Ascon)
- confirme que les 750 tr/min de la limite du chef four sont la vitesse moteur
- décideur du projet : veut l'analyse de la récupération sans la limite des 750 tr/min, avec des paliers de vitesse récupération / contre-pression qui tiennent la consigne de pression du four à 0,6 mbar
- a demandé si fermer les fenêtres et le registre ASC suffirait à atteindre le besoin
- dossier PDF « Dossier_Sechoir_B12_regulation » (22 pages, 03/10/2026) — sections 0-9 (existant, bilans, récupération, scénarios S0-S3, tableaux 5×11 fréquences, régulation ASC continue PI sur HR recyclage 27,5 %, automate FB100/FB101, matériel, mise en service) + 10 cadence 18 wagons/poste vs four 48 wagons/j + 11 couplage récupération/contre-pression (paliers 675→1 365 tr/min) + 12 fermeture fenêtres/registre ASC (registre jamais fermé à 100 % brûleur en marche ; utile mais insuffisant seul) + 13 conclusions/instructions/gains
- gains estimés du dossier vs actuel (≈ 9 294 Nm³/j, ≈ 8 206 DT/j) : solution 1 séchoir seul ≈ 794 000 DT/an (−22 % gaz) ; 2 + gaine isolée ≈ 988 000 (−31 %) ; 3 récup palier 5 ≈ 1 474 000 (−54 %) ; 4 palier 7 ≈ 1 642 000 (−63 %) ; 5 récup maximale palier 9 ≈ 1 808 000 DT/an (−72 %, la plus avantageuse) ; avec limite 750 tr/min ≈ 1,1–1,2 M DT/an ; zéro gaz possible seulement l'été à récupération maximale et arrivée ≥ 200 °C
- données encore attendues — capteur température/humidité sortie cheminée, température TC3 (arrivée gaine)
- mesure au pyromètre de la température à la cheminée d'air humide du séchoir : 45,6 °C (07/10/2026 vers 02:28)
- pression du four (consigne 0,6) en mbar
- après vérification (06/10/2026) : ventilateurs de contre-pression et de récupération du four sur variateur, rapport de poulies d'origine non modifié (fiche valable) ; seul le ventilateur de tirage four a un rapport de poulies modifié (nouvelles dimensions à fournir)
- séchoir : capteur de pression P3 installé (06/10/2026), soit deux capteurs de pression fonctionnels au séchoir (P2, P3) ; un capteur supplémentaire acheté le 06/10/2026, emplacement à choisir parmi canal inférieur côté recyclage, canal inférieur côté brassage, gaine de récupération côté séchoir ou côté four
- température au départ de la gaine de récupération : visible sur le synoptique four
- rapports septembre 2026 (production reprise le 10/09, jours 1-9 à zéro) — séchoir 10-27/09 : 36 293 m³ = 136 258 Nm³ = 1 376 074 th, 8 602 t verte, ratio 160 th/t (jours 109 à 226) ; four 10-27/09 : total usine 97 660 m³, four 61 367 m³ = 230 396 Nm³ = 2 326 772 th, 7 438 t rouge, ratio four 313, ratio global affiché 473 ; électricité 10-30/09 : 401 358 kWh (jour 138 706, pointe jour 45 936, pointe soir 1 788, nuit 214 928), 8 855 t rouge, 10 004 t verte, conso HT 107 768 144 millimes, facture estimée 146 489 896 millimes TTC ; jour 10 = 54 188 kWh
- calculs des rapports : Nm³ = m³ × F.C. 3,7544 ; thermies = Nm³ × PCS 10,099 ; ratio séchoir = th / t verte ; ratio four = th / t rouge ; gaz four = totaliseur − séchoir ; ratio PV / PR = kWh / t verte et rouge
- fiches journalières — 30/09 : vert 28,67 wagons B12, 393 t, séchoir 5 602 Nm³ (ratio 144) ; rouge 27,33 B12 + 1,67 B8, 368 t, four 11 308 Nm³ (ratio 310). 01/10 : vert 39 wagons, 522 t, 7 674 Nm³ (148) ; rouge 41, 505 t, 14 605 Nm³ (292). 02/10 : vert 39,33, 527 t, 7 021 Nm³ (135) ; rouge 38, 468 t, 14 552 Nm³ (314) ; élec 02/10 18 100 kWh. Poste 3 (05-13) produit peu en vert (4 à 7 wagons)
- qualité B12 30/09-02/10 — mouleuse 7 200-7 250 g, pression 23-24, 430-445 A, dégraissant 29-31 ; sortie séchoir 6 050-6 280 g (% séchage 16,8-19,5), T avant 115-130 °C, T arrière 60-70 °C, retrait 5,26 % ; sortie four 5 600-5 700 g, perte totale 27,2-29,5 %, retrait 1,33 %, porosité 7-7,2 ; poussée 15 min le 30/09, 12 min le 02/10
- compteur gaz du séchoir installé en amont du détendeur séchoir (côté 3 bar, comme le totaliseur) ; F.C. ≈ 3,7544 mais varie jusqu'à 3,6 ; le totaliseur a été vérifié conforme au compteur STEG
- gaine de récupération : une cheminée avec registre à la sortie du ventilateur de récupération évacue l'air chaud dehors en cas d'intervention dans le séchoir ; ce registre est peut-être défectueux, à vérifier au prochain jour d'arrêt
- poste 3 (05-13) : faible production verte due à des problèmes techniques et des arrêts non programmés
- gaine de récupération four → séchoir : dimensions 1,8 m × 1,9 m × 20 m de long (corrigé le 07/10/2026, remplace 170 × 170 cm × 70 m), température de surface 50 à 60 °C (mesurée au caméra thermique)
- four : la sonde « T.récupération » en bas à droite du synoptique (≈ 116-148 °C) mesure l'air en voûte du four à cet endroit
- synoptique production (Préparation / Fabrication) — mouleuse Morando ; B12 = 16 pièces par coupe, 2 160 par wagon ; compteurs coupes / pièces / wagons par poste et par 24 h, temps d'arrêt mouleuse par poste et par 24 h, coupes/min instantané et moyen par poste ; vitesses des doseurs (V.DOZ 1-3) et des stockeurs (V.STOCK 1-2) ; bloc « Mouleuse L2 » (coupes/min, pression bar, V. mouleuse Hz, courant A)
- relevé 03/10 20:56 : mouleuse en marche à vide
- relevé 04/10 03:34, marche en charge : 5,71 coupes/min instantané, 5,73 moyenne du poste ; poste affiché 3 : 1 616 coupes / 25 856 pièces / 12,0 wagons et 169 / 2 704 / 1,3 ; 24 h : 1 785 / 28 560 / 13,2 ; arrêt mouleuse poste 1:56:31 et 6:51:23, 24 h 5:23:46 et 13:01:53 ; doseurs 14 / 16 / 9 Hz, stockeurs 3 / 3 ; bloc L2 : 3,75 coupes/min, 17,1 bar, 0 Hz, 1 A
- historique WinCC de production disponible (courbe du 03/10 20:00 au 04/10 03:34)
- mouleuse Morando : pression à vide 15,7 bar (03/10/2026 20:56), en charge 17,1 bar (04/10/2026 03:34)
- deuxième mouleuse = Lacker, en arrêt pour entretien (début oct. 2026) ; du 06/10 ~07 h au 07/10 ~14 h la production s'est faite avec la Lacker (non couplée à WinCC, d'où les courbes coupe et malaxeur à zéro/figées) ; depuis le 07/10 ~14 h c'est la Morando et son malaxeur qui tournent
- la mouleuse Lacker et son malaxeur ne sont pas couplés à WinCC ; projet de les relier à la supervision ; seuls la Morando et son malaxeur sont visibles dans WinCC
- veut que toutes ses réponses aux questions (02/10, 03/10, 04/10/2026) soient enregistrées et servent de base au projet
- ne sait pas si le temps de standby du séchoir (5 min dans la recette brûleur) est réellement appliqué
- 07/10/2026 : a modifié la consigne du temps de standby du séchoir (compteur affichait 7-8 min en standby alors que la recette prévoyait 5 min)
- variateurs d'air chaud Control Techniques C200 90 kW : facture 22 400 DT HT (26 657 DT TTC)
- empilage : travailler sur le temps minimum de 20 min par wagon, par paliers jusqu'à 40 wagons
- méthode de chiffrage validée : raisonner en unités physiques (Nm³, kWh) puis convertir en DT avec les prix de la thermie et du kWh
- dossier final four + séchoir : révision 5 du 07/10/2026 (gaine 1,80 × 1,90 × 20 m, mesure cheminée 45,6 °C), rangée dans la page « Archive électrique WinCC »
- le dossier final four + séchoir (04/10/2026) remplace les dossiers du 02/10 (16 p.) et du 03/10 (22 p.) ; il est rangé avec ses sources dans la page privée « Archive électrique WinCC »
- a demandé d'ajouter au projet un volet mouleuse 1 (Morando) et mouleuse 2 (Lacker)
- mouleuse Morando 620 Synthesis : moteur 315 kW, 1 500 tr/min, 50 Hz, sans variateur de fréquence actuellement, démarrage étoile-triangle ; objectif : pression d'argile la plus stable possible autour de 23 bar, valeur lue sur le capteur du synoptique (capteur de pression de la mouleuse recalibré le soir du 03/10/2026) ; se demande si l'achat d'un variateur est nécessaire
- règle de conduite : ne jamais calculer la vitesse de production de la mouleuse à partir de la cadence du four ; la mouleuse doit produire au maximum, pour dégager du temps d'entretien, compenser les arrêts non programmés et diminuer les coûts de production
- pression four (courbe WinCC du 05/10/2026, consigne 0,6 mbar) : l'ouverture de la porte de sortie provoque la dépression (≈ −1,1 mbar) et l'ouverture de la porte d'entrée provoque la surpression (≈ +2,4 mbar)
- four : dans WinCC, la tendance « CENTRALE1 » (consigne 810 °C) correspond à Turbo 2 et « CENTRALE2 » (consigne 870 °C) à Zone Feu 1 du synoptique
- four : les signaux d'ouverture des portes d'entrée et de sortie arrivent déjà dans l'automate S7-412 (confirmé le 06/10/2026)
- four : une consigne spéciale de récupération (775 tr/min) s'applique quand la contre-porte d'entrée du four se lève ; en fonctionnement normal (PID), la récupération reste à 750 tr/min
- 07/10/2026 : a étalé les consignes d'humidité du recyclage et mis le brûleur ASC en mode manuel ; constat : énergétiquement plus rentable, mais reste manuel ; demande une formule ou un PID pour les ventilateurs et les brûleurs
- 07/10/2026 : consigne manuelle de l'ASC gardée à 120 °C ; se demande si elle reste fiable quand la température de la récupération chute
- 07/10/2026 : la nouvelle plage d'humidité du recyclage fonctionne aujourd'hui, mais il ne sait pas si elle reste fiable quand la température de la récupération chute
- 07/10/2026 (essai, non définitif) : plage d'humidité du recyclage réglée à 34–39 % (capteur en haut du canal supérieur) ; il surveille toujours l'humidité avant recyclage, qui ne doit pas dépasser 14 % pour avoir un produit séché
- veut que T°C1 et TC3 soient intégrés dans les formules de régulation (ASC, B1/B2, ventilateurs du séchoir)
- cadence pour les formules des ventilateurs : ne pas utiliser N (wagons/coupes) mais la mesure d'ampérage de la chaîne des balancelles, en comptant les cycles et la moyenne des montées des clefs de balancelle (plus précis)
- signal de cadence à utiliser : tendance WinCC « Archive ampérage » de la chaîne des balancelles (courbe du 06/10 19:00 au 07/10 03:00 montrée) — variables MAX AMPER (21 A, seuil de blocage), ACTUEL AMPER (pics à chaque montée), BLOCAGE, REAL AMPER
- chaque balancelle contient 5 clefs, 64 balancelles au total ; compter les clefs sur l'oscillation d'ampérage du moteur de la chaîne permet de calculer le cycle moyen et instantané du séchoir ; ce moyen, plus fiable, remplace le débit de la mouleuse dans les formules
- n'impose pas de température de sortie de l'air humide du séchoir (ex. 47 °C) : c'est seulement une mesure ; veut que le dossier fasse le nécessaire et le convainque
- mélangeur d'argile Morando ML8 : moteur 55 kW ; modèle de type mélangeur à double arbre
- 07/10/2026 vers 17:40 : a diminué l'ouverture du volet (registre arrière) du brûleur ASC ; constat : la température de la chambre de mélange (T°C4) a augmenté (≈ 190 → ≈ 300 °C), alors que les autres sondes après la chambre n'ont pas augmenté
- 07/10/2026 vers 18:20 : registre arrière du brûleur ASC fermé de 9 cm, il ne reste que 4 cm d'ouverture ; à 18:26 T°C1 (sortie chambre) = 129,8 °C pour une consigne de 120 °C ; zone extraction 116,6 °C / 1,9 % ; air humide 37 Hz
- séchoir : capteur P1 faux à cause d'un problème de plage (reste figé, affiche 0,00 mbar)
- brûleur ASC : a son propre ventilateur d'air de combustion, avec servomoteur
- 07/10/2026 vers 19:10 : l'humidité s'est aggravée après la diminution de l'ouverture du registre arrière de l'ASC ; synoptique 19:10-19:11 : zone avant recyclage 68,8 °C / 19,9-20,0 % ; recyclage 39,0-39,2 % / 61 °C ; T°C4 311-313 °C ; ASC 129 °C (130 °C affiché) ; T°C1 133 °C ; zone extraction 123 °C / 1,9 % ; TC3 105-106 °C ; air humide 40 Hz ; recyclage 45 Hz ; P2 2,74-2,86 mbar, P3 −0,08/−0,12, P4 −1,14 mbar
- accès au poste WinCC par AnyDesk : Claude ne clique que sur les boutons de page FOUR, SECHOIR, EMPILAGE, FABRICATION et MESURE AMPER, rien d'autre
- 08/10/2026 : accès donné pour l'examen total des synoptiques et l'enregistrement en mémoire de toutes les courbes des 5 derniers jours, tous postes ; ne jamais cliquer sur une consigne de recette, une mise en marche ou un arrêt, ne rien changer, toujours lui demander que faire ; lui faire un compte rendu une fois tout enregistré
- règle WinCC : toujours fermer chaque fenêtre (courbe, archive, popup) que Claude a ouverte ; ne jamais laisser une courbe affichée
- veut que toutes les courbes et données relevées sur WinCC (examen du 08/10/2026) soient gardées en mémoire de façon permanente (section 3)
- contraintes séchoir pour le projet de régulation (08/10/2026) : T°C1 (TC1, sortie chambre) ne doit jamais dépasser 145 °C ; T°C4 (TC4, chambre de mélange) ne doit jamais dépasser 250 °C
- 08/10/2026 : a demandé un rapport PDF (statistiques, anomalies, propositions tirées des courbes WinCC) puis le projet de régulation mis à jour avec ces données
- séchoir : les 64 balancelles sont numérotées ; poste de chargement à l'avant du séchoir (entrée) ; la chaîne avance en continu et s'arrête pour l'alimentation de la balancelle en briques, le pic d'ampérage = avancement vers une autre clef de balancelle
- séchoir : les déraillements de balancelles (sortie du rail) se produisent partout dans le canal ; veut savoir le numéro de la balancelle qui bloque et son emplacement quand l'ampérage dépasse la consigne
- séchoir : sens de marche des balancelles confirmé (08/10/2026) — départ du poste de chargement (entrée) par la galerie basse vers le fond du séchoir, retour par la galerie haute vers l'entrée
- l'usine a deux compresseurs d'air (mesurés ensemble sur le départ « Compresseur » du synoptique)
- four : le ventilateur de contre-pression est sur le toit du four, côté sortie (droite du synoptique), et souffle l'air par des fentes dans la voûte ; envisage (13/10/2026) d'installer 4 ventilateurs sur la porte de sortie du four pour économiser du gaz
- séchoir : manque permanent d'air de récupération du four, le brûleur fonctionne tout le temps (13/10/2026)
- four : ventilateurs d'air de combustion des centrales actuellement réglés par servomoteur ; envisage (14/10/2026) de les passer sur variateur de vitesse et de diminuer l'entrée d'air lors de la poussée
- four : le nombre de centrales a diminué depuis l'audit 2016, mais les 4 ventilateurs d'air de combustion ont été gardés (14/10/2026)
- four : les courbes des centrales montrent une chute de température à chaque poussée (14/10/2026)
- lecture fine (1 h) des courbes des 4 centrales et de la pression four, pour chiffrer la chute de température à la poussée : reportée au 15/10/2026
- four : chaque centrale a deux électrovannes gaz, min et max ; pendant la poussée le gaz passe par l'électrovanne min et le servomoteur ferme le registre au tiers ; ce servomoteur agit seulement sur la vanne gaz (pas sur l'air) et reste fixe entre deux poussées (14/10/2026)
- plaques signalétiques des ventilateurs d'air de combustion des centrales du four (14/10/2026) — T1 : moteur ABB IE3 M2BAX 160MLB 2, 15 kW, 2 pôles, 400 V Δ 26,5 A, 2 939-2 947 tr/min, cos φ 0,88, rendement 91,9 % (100 %) ; ventilateur F.lli Ferrari FI632 N4A LG270 (2016, 213 kg, moteur 15 kW 2P 160, Vmax 3 000 tr/min, Tmax 60 °C, rendement 77 %, N77, sans variateur). T2 : moteur Cantoni Sg 132S-2B (06/2014), 7,5 kW, 400 Δ / 690 Y, 13,9 / 8,1 A, 2 920 tr/min, cos φ 0,88, rendement 88,5 % ; ventilateur F.lli Ferrari FE631 P4A RD270 (2015, 147 kg, moteur 7,5 kW 2P 132, Vmax 3 000 tr/min, Tmax 60 °C, rendement 63 %, N63, sans variateur). C1 et C2 : moteurs Varta MS132SB-2, 7,5 kW, 400 Δ / 690 Y, 14,1 / 8,16 A, 2 920 tr/min, cos φ 0,88, IP55, classe F (identiques) ; ventilateurs Thermivent IPH 600 - LG/270, n° 2009V 0339 et 2009V 0342, moteur 7,5 kW 2P 230/400 V 25,4/14,7 A 50 Hz
- projet variateurs des ventilateurs d'air de combustion des centrales : l'action du variateur (baisse de vitesse) se fera au moment de la poussée (gain électrique à calculer sur la durée des poussées)
- four : durée approximative d'une poussée ≈ 2 min ; vitesse des ventilateurs d'air de combustion visée pendant la poussée : à déterminer (14/10/2026)
- four : intéressé par une mesure en continu de l'O2 (et CO2) des fumées (14/10/2026) ; piquage possible dans la cheminée ou dans le caisson avant le ventilateur de cheminée (tirage) ; température des fumées au niveau du tirage entre 70 et 150 °C ; possède un Gastech MiniFlow (testeur d'étanchéité gaz, pas un analyseur de fumées)
- travail sur son PC via AnyDesk : toujours réduire la fenêtre de discussion Claude pour qu'il voie l'écran ; autorisation permanente de redémarrer/reconnecter AnyDesk quand la session coupe
- synoptique four : les 3 petits carrés sous la flèche jaune = fins de course du pousseur des wagons ; sous chaque porte (entrée, contre-porte d'entrée, sortie) un voyant vert = fin de course actionné, rouge = non actionné ; « Archive FC port » = historique des fins de course des 3 portes, avec un problème de parasites/harmoniques sur la courbe
- broyeur à marteaux (broyage d'argile) : moteurs 160 kW, 1 000 tr/min ; envisage (15/10/2026) d'installer un variateur de fréquence et de le faire tourner à 40 Hz
- objectif (16/10/2026) : diminuer la consommation kWh de la fabrication en charge
- fabrication (16/10/2026) : vitesses des stockeurs (trémies) utilisées 25, 30, 35 et 40 Hz, alors que la vitesse de la mouleuse est fixe ; envisage de faire varier la vitesse du moteur de la mouleuse selon la vitesse d'argile des trémies
- mouleuse Morando (16/10/2026) : la courbe de pression WinCC présente des parasites dus aux harmoniques ; envisage de programmer un variateur pour tenir une pression stable (23 ou 25 bar) et de stabiliser l'humidité au mélangeur/malaxeur
- chambre à vide de la Morando : deux dévidoirs tournants alimentent les hélices, pas de possibilité d'installer un capteur physique à l'intérieur ; elle a des fenêtres en verre qui se couvrent de boue en marche
- 16/10/2026 : brûleur ASC en mode MANU, consigne 110 °C (confirmé ; T°C4 oscille 150↔310 °C, période ~10 min, ce jour-là)

---

# 2. Archive WinCC électrique du 02/10/2026 (12:44-20:56)

## Fichier source
- archive « csv.rar » (20 fichiers CSV WinCC, UTF-16, séparateur « ; », virgule décimale, colonnes « Courbe 1 Time » / « Courbe 1 ValueY », ≈ 57 600 lignes chacun) = historique électrique WinCC du 02/10/2026 de 12:44:02 à 20:56:18, une valeur par seconde, sans trou ; ne plus perdre ce fichier
- extraction RAR5 possible via libarchive.so.13 en ctypes (unrar/pip indisponibles dans l'espace de travail)
- données complètes (fusion 1 s et 1 min, 20 colonnes) sauvegardées dans la page privée « Archive électrique WinCC » https://claude.ai/artifact/S5athKyKNhmQyUZv3KFVje (fichiers wincc_elec_2026-10-02_1s.csv et wincc_elec_2026-10-02_1min.csv, séparateur « ; », point décimal)

## Correspondance des courbes
- Control1 = courant transfo (A) ; Control13 / Control12 / Control14 = P (kW) / Q (kVAR) / cos φ de la préparation
- p/q/i/pf + séchoir, fabrication, four, compresseur = P kW, Q kVAR, I A, cos φ de chaque départ (fichiers psechoir, qsechoir, isechoir, fpsechoir ; pfabrication, qfabrication, ifabrication, pffabrication ; pfour, qfour, ifour, pffour ; pcompresseur, qcompresseur, icompresseur, « pf compresseur »)
- contrôle aux écrans de 19:02 conforme (séchoir 299 kW, fabrication 416 kW, préparation 52 kW, transfo 1 448 A ↔ 961 kW / 342 kVAR)

## Conclusions de l'analyse
- compteur compresseur faux d'un facteur 3,22 (I mesuré / I calculé = 3,225 contre 0,985-0,986 sur séchoir, fabrication, four) ; puissance réelle ≈ 70 kW au lieu de 22 kW ; vérifier rapport TC ou câblage d'une phase
- compresseur à 61-69 kW même pendant l'arrêt fabrication 14:34-15:00 → suspicion de fuites d'air (≈ 20 000 DT/an par 10 kW de fuites, hypothèse 24 h × 330 j × 0,27 DT/kWh)
- fabrication à l'arrêt = 74 kW et 370 kVAR (cos φ ≈ 0,2) ; 11 arrêts = 58 min sur 8 h ; jusqu'à ≈ 35 000 DT/an si tout pouvait être coupé (5 h d'arrêt/j)
- réactif : fabrication ≈ 450 kVAR quasi constant, préparation 132 kVAR pour 53 kW (cos φ 0,36), total départs ≈ 770 kVAR → 3 gradins saturés ; piste compensation locale (≈ 120 kVAR préparation + fabrication), selfs anti-harmoniques si mouleuse sur variateur à thyristors
- séchoir 187-308 kW, moyenne 253 kW (≈ 2 000 kWh sur 8 h), oscillations lentes ≈ 100 kW en cycles de 1 h à 2 h 30 (13:45-14:25, 15:30-16:20, 19:05-20:40), indépendantes de la fabrication et de la préparation → ventilateurs suivant les recettes (recyclage / air humide)
- four stable ≈ 59 kW, cos φ 0,88 ; transfo pic 1 580 A sur 1 min (≈ 1 095 kVA), max 15 min ≈ 910 kW (+ ≈ 75 kW non mesurés) < 1 200 kW souscrits ; préparation arrêtée 7 fois, 3 h 06 au total
- questions ouvertes : moteurs de fabrication restant en marche à l'arrêt, type de variateur de la mouleuse, rapport TC compresseur (réglé vs réel), export courbes séchoir 12:45-20:45 (fréquences, humidités, balancelles, sortie ASC)

## Analyse séchoir / four (04/10/2026)
- mesures toutes les ≈ 3 s ; tension estimée ≈ 406 V
- courant séchoir moyen 440 A (1 min : 347-517 A ; 1 s : 323-533 A) ≈ 40-60 % de la somme des courants nominaux des moteurs séchoir (≈ 850-880 A) ; courant four moyen 96 A (1 min : 87-107 A) ≈ 35-40 % des nominaux (≈ 270 A)
- énergie sur 7 h 52 : séchoir 1 991 kWh (253 kW), four 467 kWh (59 kW) ; extrapolé 24 h : séchoir ≈ 6 070 kWh/j ≈ 1/3 de l'électricité usine (18 100 kWh le 02/10), ≈ 11,5 kWh/t verte ; four ≈ 1 420 kWh/j ≈ 3 kWh/t rouge
- séchoir Q = 0,285 P + 106 (r 0,92) → la partie qui varie a un cos φ ≈ 0,96 (ventilateurs sur variateur : recyclage, air humide) ; base ≈ 106 kVAR fixe → hypothèse : air chaud encore en direct sur réseau le 02/10 (variateurs pas encore en service)
- séchoir : oscillation lente ±50 kW, pics toutes les 1 à 2 h 30 (15:33, 16:44, 19:08, 20:09) ; le « ≈ 20 min » donné le 04/10 était un artefact de filtrage (corrigé) ; cause : régulation proportionnelle du recyclage sur l'humidité + passages standby / redémarrage ; perte électrique directe ≈ 3 kW
- séchoir standby : déclenché 6-8 min après l'arrêt mouleuse ; arrêt 14:34-15:00 → descente 254 → 190 kW en 16 min (minimums recyclage 35 Hz, extraction 38 Hz, air chaud 50 Hz) ; redémarrage : 6 min sans action puis +110 kW en 22 min ; 13:58:57 : standby déclenché 1 min après la reprise de la mouleuse (arrêt 13:51-13:57), −48 kW
- calage des ventilateurs séchoir sur 2 relevés de synoptique : 15:04 standby (35/38/38 Hz) = 196 kW ; 19:02 (47/47/49 Hz) = 299 kW → P = 85 (fc/50)³ + 141 (fr/50)³ + 88 (fe/50)³ + 25 kW ; moyenne de production 256 kW ≈ 43 Hz ; la formule de fiche du dossier (106/154/96 + 28) surestimait de 14-17 %
- dossier final four + séchoir révision 1 (04/10/2026, 21 pages) recalé sur cette archive et sur toutes les réponses des 02-04/10 (arrêt séchoir pris à 160 kW, recyclage/extraction à 30 Hz à la main), rangé avec ses sources (modele.py, scenarios.py, figures.py, fig_archive.py, build_pdf.py) dans la même page privée ; gains prudents S1 709 000, S2 1 030 000, S3 1 272 000, S4 1 394 000 DT/an ; total S4 + F1 ≈ 1,54 à 2,33 M DT/an
- four : poussée visible sur le courant (groupe hydraulique : ≈ 30 s en charge +2-4 kW / +5-7 kVAR puis ≈ 50 s à vide) ; cycle ≈ 15 min jusqu'à 14:00, puis 12,0 min régulier de 14:42 à 20:41 (30 intervalles) → 40 wagons / 24 h (cohérent avec 38 wagons rouges le 02/10) ; four +3 kW après le passage à 12 min (56,6 → 60 kW)
- four électrique faible : passer la récupération de 750 à ≈ 1 100 tr/min coûterait ≈ +12 kW (≈ 75 DT/j), négligeable devant le gain gaz

## Moyennes horaires (kW ; compresseur corrigé × 3,22)
heure | I transfo A | prép | fab | séchoir | four | comp | total
13-14 | 1304 | 55 | 372 | 276 | 57 | 53 | 812
14-15 | 906 | 0 | 240 | 220 | 60 | 66 | 586
15-16 | 1366 | 41 | 429 | 262 | 60 | 71 | 863
16-17 | 1314 | 36 | 418 | 252 | 59 | 71 | 835
17-18 | 1330 | 13 | 451 | 263 | 59 | 72 | 858
18-19 | 1352 | 53 | 407 | 234 | 60 | 74 | 828
19-20 | 1367 | 24 | 434 | 272 | 61 | 72 | 862
20-20:56 | 1317 | 35 | 410 | 241 | 61 | 74 | 821

## Moyennes 10 min
début | I transfo A | prép P/Q | fab P/Q/cos | séchoir P/Q/cos | four P/Q | compresseur P/Q corrigés × 3,22
12:50 | 1241 | 16/45 | 435/460/0.69 | 237/169/0.81 | 56/29 | 56/37
13:00 | 1412 | 58/132 | 461/464/0.71 | 257/175/0.83 | 56/29 | 58/37
13:10 | 1446 | 57/132 | 461/461/0.71 | 274/179/0.84 | 56/29 | 57/37
13:20 | 1291 | 55/131 | 359/430/0.59 | 273/178/0.84 | 56/29 | 57/37
13:30 | 1226 | 56/132 | 313/417/0.53 | 275/179/0.84 | 57/31 | 56/37
13:40 | 1432 | 49/132 | 449/455/0.70 | 299/186/0.85 | 57/30 | 44/28
13:50 | 1020 | 53/134 | 186/397/0.34 | 278/182/0.84 | 58/30 | 47/30
14:00 | 1264 | 12/37 | 444/460/0.70 | 232/170/0.81 | 59/31 | 67/39
14:10 | 1174 | 0/0 | 428/457/0.67 | 216/165/0.79 | 61/33 | 66/38
14:20 | 850 | 0/0 | 222/403/0.39 | 205/165/0.78 | 60/33 | 65/39
14:30 | 886 | 0/0 | 215/409/0.38 | 244/175/0.81 | 58/31 | 64/37
14:40 | 646 | 0/0 | 65/379/0.17 | 226/169/0.80 | 60/33 | 65/37
14:50 | 615 | 0/0 | 64/377/0.17 | 198/160/0.78 | 59/33 | 67/38
15:00 | 1104 | 0/0 | 389/447/0.62 | 203/160/0.78 | 59/32 | 70/38
15:10 | 1350 | 33/90 | 444/458/0.70 | 257/175/0.83 | 58/31 | 68/37
15:20 | 1440 | 54/131 | 432/451/0.68 | 293/185/0.85 | 59/31 | 69/37
15:30 | 1446 | 54/131 | 415/445/0.68 | 300/187/0.85 | 62/35 | 73/39
15:40 | 1467 | 53/131 | 457/455/0.71 | 275/181/0.84 | 60/33 | 74/39
15:50 | 1391 | 54/131 | 438/451/0.70 | 247/173/0.82 | 58/31 | 74/39
16:00 | 1295 | 55/133 | 407/446/0.66 | 218/166/0.79 | 58/31 | 71/38
16:10 | 1375 | 55/134 | 472/467/0.71 | 206/165/0.78 | 58/32 | 71/39
16:20 | 1290 | 43/112 | 431/459/0.68 | 215/168/0.79 | 59/32 | 67/38
16:30 | 1116 | 0/0 | 323/440/0.52 | 280/191/0.83 | 60/34 | 69/41
16:40 | 1383 | 11/38 | 448/473/0.68 | 303/197/0.84 | 60/35 | 75/42
16:50 | 1425 | 54/135 | 425/459/0.67 | 288/192/0.83 | 59/33 | 72/41
17:00 | 1461 | 54/133 | 452/461/0.70 | 273/185/0.83 | 58/32 | 76/41
17:10 | 1386 | 27/72 | 450/467/0.69 | 275/188/0.82 | 58/32 | 73/41
17:20 | 1287 | 0/0 | 453/474/0.69 | 265/188/0.82 | 61/36 | 69/40
17:30 | 1299 | 0/0 | 454/474/0.69 | 265/189/0.81 | 61/35 | 74/42
17:40 | 1258 | 0/0 | 444/473/0.69 | 251/185/0.80 | 59/34 | 71/41
17:50 | 1290 | 7/30 | 452/472/0.69 | 249/183/0.80 | 60/34 | 69/40
18:00 | 1377 | 58/138 | 419/457/0.66 | 235/176/0.80 | 59/33 | 74/41
18:10 | 1424 | 59/146 | 458/458/0.71 | 224/169/0.80 | 59/32 | 75/41
18:20 | 1401 | 52/132 | 458/456/0.71 | 218/167/0.79 | 59/32 | 75/41
18:30 | 1200 | 42/129 | 350/427/0.56 | 204/163/0.78 | 61/34 | 73/40
18:40 | 1410 | 52/132 | 446/455/0.70 | 234/170/0.81 | 60/32 | 75/41
18:50 | 1298 | 54/133 | 314/415/0.52 | 293/189/0.84 | 59/32 | 74/41
19:00 | 1328 | 19/53 | 389/442/0.63 | 299/191/0.84 | 60/34 | 73/41
19:10 | 1363 | 0/0 | 453/463/0.70 | 298/192/0.84 | 61/35 | 73/40
19:20 | 1311 | 0/0 | 442/462/0.69 | 271/185/0.82 | 62/34 | 70/39
19:30 | 1365 | 25/76 | 443/459/0.69 | 260/181/0.82 | 60/33 | 70/38
19:40 | 1412 | 54/134 | 435/455/0.69 | 252/179/0.81 | 60/34 | 72/39
19:50 | 1424 | 52/134 | 443/459/0.70 | 249/179/0.81 | 60/33 | 74/39
20:00 | 1419 | 53/134 | 421/450/0.66 | 265/183/0.82 | 61/33 | 76/40
20:10 | 1410 | 53/134 | 431/455/0.69 | 256/180/0.82 | 61/34 | 72/39
20:20 | 1435 | 53/135 | 453/462/0.70 | 248/178/0.81 | 62/35 | 72/39
20:30 | 1047 | 0/8 | 299/429/0.49 | 232/178/0.79 | 60/33 | 73/40
20:40 | 1241 | 0/0 | 451/473/0.69 | 212/173/0.77 | 60/33 | 75/41

---

# 3. Relevés synoptiques et courbes WinCC (examen du 08/10/2026 et suivants)

## MESURE AMPER — instantané 07/10/2026 23:53
- Transfo N1&N2 : 1354 A, 405 V, P 917 kW, Q 256 kVAR, PF 0,96 ; kWh 7 877 081
- Préparation 174 A / 54 kW / 101 kVAR / PF 0,47 ; Fabrication 805 A / 392 kW / 413 kVAR / 0,71 ; Séchoir 499 A / 294 kW / 191 kVAR / 0,84 ; Four 103 A / 64 kW / 33 kVAR / 0,89 ; Compresseur 81 A / 47 kW / 32 kVAR / 0,82 (TC cohérent ce jour)
- Régulation PF auto : SP 0,98, PV 0,96, 3 gradins ON, temporisation 64 s
- Ampérages act/max (A) : broyeur meule 0/250, brise-mottes 26/250, mélangeur 69/80, malaxeur 72/90, broyeur marteau 1 0/150, marteau 2 1/161, cylindre rapide 114/145, dégrossisseur 1 50/50, dégrossisseur 2 38/35, cylindre lent 42/45

## Courbes MESURE AMPER (30/09 → 08/10/2026)
- Mélangeur (MAX AMPER 80 A) : marche normale 30–100 A, oscillant autour du max ; arrêts (0 A) ~30/09 soir, 01/10 ~18 h, 02/10 ~15 h, 07/10 après-midi ; pics isolés 170 A (30/09, 01/10), ~270 A (03/10 nuit et 07/10 23 h) ; signal BLOCAGE ponctuel 06/10 ~01 h
- Malaxeur (max 90 A) : 0 A du 30/09 au 03/10 ~19 h (pas d'enregistrement ou arrêt), marche 03/10 19 h → 06/10 ~07 h (25–130 A, pics > 260 A au redémarrage 03/10), 0 A 06/10 07 h → 07/10 ~14 h, marche depuis 07/10 ~14 h (60–95 A)
- Broyeur à meule (max 250 A) : marche intermittente par cycles, 20–40 A en marche, démarrages 150–180 A, pics > 260 A le 04/10 nuit ; nombreux arrêts
- Brise-mottes (max 250 A) : ≈ 0 A presque tout le temps ; démarrages 05/10 ~22 h et 07/10 matin, marche ~30 A depuis 07/10 23 h
- Broyeur marteau 1 (max 150 A) : intermittent, 50–70 A en marche, démarrages 180–200 A (> 260 A le 04-05/10 et 06/10 ~16 h)
- Broyeur marteau 2 (max 161 A) : à l'arrêt toute la période, seulement quelques démarrages (02/10 nuit, 05/10 ~22 h, 06/10 ~16 h)
- Cylindre rapide (max 145 A) : marche 95–150 A, souvent au-dessus du max ; arrêts 30/09 (quelques heures), 01/10 matin, 02-03/10 courts, 06/10 ~01 h, 07/10 ~14–17 h
- Cylindre dégrossisseur 1 (max 50 A) : marche 45–65 A, en permanence au niveau ou au-dessus du max ; très nombreux démarrages avec pics > 260 A
- Cylindre dégrossisseur 2 (max 35 A) : marche ~30–40 A, au niveau du max ; nombreux démarrages à ~165 A (pic > 260 A le 05/10)
- Cylindre lent (max 45 A) : marche stable 40–50 A ; arrêts aux mêmes moments que le cylindre rapide
- Toutes les courbes ampérage : chute de la consigne MAX vers 0 le 06/10 ~01 h (même instant que le BLOCAGE mélangeur) → probable redémarrage/perte de liaison automate

## FOUR — instantané 08/10/2026 00:24
- poussée 720 s (12,0 min), 40 wagons/24 h, Nbr wagons actuel 6 / ancien 31 ; B12 ; Régulation En Auto
- Turbo 2 809/810 °C, Zone Feu 2 888/890, Zone Feu 1 877/880, Zone Feu 3 512/0, Turbo 1 789/790, Zones 4-6 à 0 ; T.AvantF.2 465 °C, T.AvantF.3 518 °C ; T.Fumée 88 °C (consigne 160) ; T.Recycl 357/350 ; brûleurs latéraux 830/600
- tirage 1200 tr/min (min 69 / max 70 %) ; pression tirage −1,7 mb ; pression four +0,4 mb (consigne +0,5) ; T.récupération voûte 233 °C ; P.récupération 0,00 (capteur HS) ; T.refroidissement 589/650 °C ; T.récupération 408/600 °C ; T.récupération bas 88 °C
- récupération 750 tr/min (min/max 50 %) ; contre-pression 400 tr/min avec STANDBY CP actif (valeur standby 400) — à 23:50 la contre-pression était à 825 tr/min
- REF wagons : TC25 76 °C, TC15 56 °C, TC25(bis) 94 °C ; message permanent « Pas de liaison au serveur de données ! »

## Courbes FOUR
- Archive FC port : 4 signaux tout-ou-rien (fins de course portes) qui basculent très souvent, illisible sur plusieurs jours
- Archives T.Recycl et brûleurs latéraux : courbes plates (figées le 07/10 08 h–14 h), pas exploitables
- Vitesse récupération (échelle 600–1200 tr/min, en dessous de 600 coupé) : 03/10 750 avec impulsions 0–4 h, puis ~670 4–11 h, arrêt ~11–12 h, instable 600–700 l'après-midi, 670–750 le soir ; 04/10 ~670 avec impulsions, chutes ~05 h et ~10 h, 700–720 dès 18 h, 750 dès 23 h ; 05/10 750 0–5 h, descente < 600 vers 5–6 h, 750 8–11 h, instable 11–13 h, ~670 avec impulsions 700 dès 14 h ; 06/10 base 675 avec impulsions 775 jusqu'à ~15 h puis base 750 avec impulsions ~775 ; 07/10 base 750 avec impulsions 800 (portes), chutes < 600 vers 04 h et 13–14 h, pic 1200 vers 13 h
- Vitesse contre-pression (tr/min ; les chutes à 400 = STANDBY CP) : 03/10 800–820 0–9 h, 650–700 10–14 h (chute à 0 ~13 h), oscille autour de 800 15–17 h, 650 17–20 h, 450 20–22 h, 600–700 après 22 h ; 04/10 730–750 stable 0–7 h, 700–780 7–14 h, 650–700 ~15 h, 750–850 fluctuant 17–24 h ; 05/10 850 0–4 h, trou de données ~5–8 h, 850 8–11 h, ~770 11–13 h, chutes à 0 12–14 h, 650–700 13–16 h, 750 avec chutes à 400 16–21 h, 800 vers 23 h ; 06/10 ~800 0–8 h, 600 plat 8–10 h, 700–800 avec chutes fréquentes 10–17 h, ~750 avec chutes à 400 17–21 h, 800–870 après 22 h ; 07/10 850 0–9 h avec chutes à 400, 650–700 9–15 h (chute à 0 ~13 h), 800–850 dès 16 h avec chutes à 400

## SECHOIR — instantané 08/10/2026 00:27
- recyclage 45 Hz ; extraction air humide N°1/2/3 41 Hz (1230 tr/min) en AUTOMATIQUE ; air chaud 45 Hz ; balancelles 0,000 Hz à cet instant ; ampérage chaîne max 20,5 / act 15,1 A
- zone recyclage 31,3 % / 67,7 °C (plage MAX 37 / MIN 30 %) ; zone avant recyclage 75,9 °C / 13,7 % (régul. humidité OFF, 85 °C / 2,0 %) ; zone extraction 128,0 °C / 1,9 % (140 °C)
- ASC MANU : 131,0 °C mesure, consigne 130 °C ; T°C1 sortie chambre 137,6 °C ; T°C4 chambre de mélange 242,4 °C ; TC3 157,9 °C ; TC2 45,6 °C
- P2 3,44 mbar (36,54 mmH2O), P3 −0,11, P4 −1,20, P1 0,00 mbar
- B1/B2 AUTO ; brûleur à point PV 69 °C (max 80 / min 70) ; brûleur 2 LOCAL OFF (consigne 119 °C)
- panneau « Registres » existant sur le synoptique : Récupération AUT, Chambre MAN, Arrière séchoir MAN, Brûleur AUT, Port chambre MAN (bargraphes + boutons +/−) ; portes air chaud 1 et 2 en MAN
- cycle séchoir 320/320 ; compteurs 1:0:19 et 1:2:38 ; temps de fonctionnement brûleur actuel 1 h 49 min 44 s, avant 24 h 14 h 55 min 7 s

## Courbes SECHOIR
- Ampérage chaîne balancelles (30/09–08/10) : marche 0–20 A en dents de scie (MAX 20/21 A) ; arrêts 01/10 ~16–19 h, 03/10 ~18–22 h, 04/10 ~13–15 h, 05/10 ~00–05 h (trou), plusieurs courts ; signaux BLOCAGE ponctuels 30/09, 01/10 (×3), 02/10, 06/10 (×2), 07/10 (×2)
- Marche ventilateurs air chaud 1 et 2 : presque toujours en marche ; arrêts 03/10 ~12 h et ~22 h, 04/10 ~12–13 h et ~14–15 h, 05/10 ~12–13 h, 06/10 ~01–03 h et ~13–15 h, 07/10 ~03 h (court) et ~07:30–15:30 (8 h)

## FABRICATION — instantané 08/10/2026 00:29
- B12, 16 pcs/coupe, 2160 pcs/wagon, poste 3 ; 6,32 coupes/min instantané, 6,24 moy/poste ; poste : 1272 / 20352 / 9,4 wagons (ancien 1412 / 22592 / 10,5) ; 24 h : 2684 / 42944 / 19,9 ; arrêt mouleuse poste 0:03:47 (ancien 4:01:10), 24 h 15:07:12 (ancien 13:01:53)
- doseurs V.DOZ 3/2/1 = 9 / 30 / 14 Hz ; stockeurs 2/1 = 4 / 3 ; bloc Mouleuse L2 : 3,43 coupes/min, 28,0 bar, N° 7, 0 Hz, 1 A
- Courbe coupe 07/10 16:30–08/10 00:30 : 6–7 coupes/min stable (pic 13 vers 19:45), moyenne ~6 ; bit production avec interruptions 19–21 h ; changement de poste vers 21 h

## EMPILAGE — instantané 08/10/2026 00:30
- poste 3 : 9,0 wagons (ancien 10,7) ; 24 h : 9 (ancien 28) ; temps wagon 0 h 08 min (ancien 0 h 25) ; pile 2/3, couche 0/10 ; références wagons file : 19, 44, 58, 16, 69, 4
- Archive wagons/24 h (relevé à 21 h) : 28/09 48 ; 29/09 33 ; 30/09 32 ; 01/10 38 ; 02/10 37 ; 03/10 25 ; 04/10 37 ; 05/10 38 ; 06/10 41 ; 07/10 28
- Archive wagons/poste (fin de poste 05 h / 13 h / 21 h) : 02/10 21 h P2 17,0 ; 03/10 05 h P3 17,3, 13 h P1 7,3, 21 h P2 3,0 ; 04/10 05 h P3 15,0, 13 h P1 9,3, 21 h P2 15,3 ; 05/10 07:32 P3 18,3, ~12–13:47 plusieurs petites entrées (5,0 ; 1,0 ; 1,3 ; 1,3 ; 1,0), 21 h P2 16,3 ; 06/10 05 h P3 14,0, 13 h P1 14,0, 21 h P2 16,7 ; 07/10 05 h P3 15,3, ~13 h P1 5,0 + 1,0 + 1,0, 21 h P2 10,7
- le poste 1 (05–13 h) est le plus faible en wagons empilés sur toute la période
- Archive temps wagon (07/10–08/10) : 30 wagons du 07/10 00:52 au 08/10 00:32 ; temps par wagon le plus souvent 22–49 min ; un trou de 8 h 21 min entre 07/10 07:55 et 16:16 (arrêt prolongé, cohérent avec l'arrêt des ventilateurs air chaud 07:30–15:30)
- Turbo 2 (consigne 810 °C, 800 le 05/10 matin) : mesure 800–810 °C stable ; 03/10 creux ~745 °C vers 06–07 h ; 05/10 trou de données ~05–07 h ; 06/10 chute vers 00–01 h ; 07/10 ~740 °C plat 03–08 h (probable trou d'enregistrement) et creux vers 12–13 h
- Zone Feu 2 (consigne 890 °C) : 875–890 °C stable ; 03/10 creux ~850 °C 06–08 h et vers 21 h ; 05/10 trou ~05–07 h ; quelques chutes ponctuelles (coupures)
- Zone Feu 1 = CENTRALE2 (consigne 880 °C, 870 le 05/10 07–10 h) : 860–880 °C ; 03/10 creux ~820 °C 06–08 h et ~840 °C 20–21 h ; 05/10 trou 05–08 h ; 06/10 creux ~840 °C vers 18 h ; 07/10 chutes ponctuelles vers 03 h et 13–14 h
- Turbo 1 (consigne 790–800 °C) : dents de scie 770–800 °C à chaque poussée ; 03/10 creux ~700 °C 06–08 h et ~750 °C vers 20 h ; 05/10 trou ~05–08 h ; 07/10 creux ~720 °C 03–05 h
- Zone Feu 3 (C4, ~512 °C) : courbe hors échelle (échelle 500–1000), rien de lisible
- T.AvantF.2 : stable 465–490 °C (07/10)
- T.récupération (case centre-droit, 233 °C à 00:24) — courbe très variable : 02/10 270–290 °C le matin, 170 °C vers 13 h, 230–245 °C le soir ; 03/10 230 °C jusqu'à ~10 h puis chute à 160 °C vers 14 h et < 100 °C de 18 h jusqu'au 04/10 matin ; 04/10 remonte de 110 à 170 °C (09 h), 140 °C (11 h), 190 °C (13 h) puis 250 °C au 05/10 01 h ; 05/10 245 °C, trou 05–09 h, 240 °C 09–13 h, chute à 130 °C vers 16 h, remonte à 240 °C au 06/10 00 h ; 06/10 240 °C, creux 210 °C vers 10 h, 250–260 °C l'après-midi, 280–290 °C le soir ; 07/10 260 °C 01–04 h, chute brutale vers 05 h à 150 °C (07 h), reste ~145–150 °C jusqu'à ~19 h puis remonte à 230 °C à minuit
- T.récupération (case bas droite 408/600 °C, tendance « RECUPERATION ») : 03/10 440–455 °C la nuit, baisse dès 08 h (430) → 350 °C (13 h) → 300 °C (16 h) → 220–240 °C (22–24 h) ; 04/10 280–300 °C la nuit, 380 °C vers 06 h, creux 230 °C vers 09 h, 330–370 °C ensuite ; 05/10 420–440 °C 0–4 h, trou 05–07 h, 420 °C 08–12 h, chute à 300 °C vers 13–14 h, 350–380 °C le soir ; 06/10 410–440 °C le matin, montée à 480–495 °C vers 22–23 h ; 07/10 460–475 °C 0–4 h, chute à ~350 °C (06 h), ~300 °C 08–17 h (min 280 °C vers 14 h), remonte à 400 °C à minuit
- les deux températures de récupération suivent la même évolution, avec de fortes baisses les jours d'arrêt (03/10 après-midi, 05/10 midi, 07/10 matin)
- Pression four : fenêtre courte (~1 h), autour de la consigne +0,5 mbar avec creux jusqu'à −1,5 et pointes ~+1 mbar (portes) ; T.refroidissement : 520 → 590 °C en hausse lente le 07/10 soir (consigne 650)
- Séchoir zone recyclage (03/10 → 08/10) : température 55–75 °C, humidité 20–40 % ; 03-04/10 60–75 °C / 20–30 % ; 05/10 trou ~05–08 h ; 06/10 60–75 °C / 25–35 %, chute brutale vers 01 h (coupure) ; 07/10 matin ~70 °C / 30 %, après-midi ~52–60 °C / 35–40 % (pendant l'arrêt), soir 65–70 °C / 31–37 %
- Séchoir zone avant recyclage (consigne 85 °C) : température 65–100 °C, humidité 5–20 % ; 03/10 70–95 °C puis ~60 °C 13–20 h, 8–15 % ; 04/10 oscille 65–90 °C, 8–12 % ; 05/10 trou ~03–07 h, ~100 °C 08–11 h puis 75–85 °C, 8–15 % ; 06/10 70–95 °C, ~8–10 % ; 07/10 80–85 °C le matin, 45–50 °C 08–16 h (arrêt) avec humidité jusqu'à ~20 %, 80–90 °C / 12–15 % le soir
- Brûleur ASC (tendance Ascon) : 03/10 consigne basculant 110–120 °C (auto humidité), T 105–120 °C la nuit, brûleur arrêté longtemps 13–20 h (T 60–80 °C) ; 04/10 consigne ~120–130 °C, T ~120 °C avec chutes fréquentes à 50–80 °C (arrêts brûleur nombreux) ; 05/10 consigne 120 °C, trou ~03–07 h, arrêt brûleur vers 13–14 h ; 06/10 consigne 120 °C, T ~120 °C avec chutes à 60–80 °C (standby), oscillations 120–135 °C l'après-midi ; 07/10 T 120–125 °C (consigne 120) la nuit, brûleur arrêté 07:30–16:00 (T ~40 °C), consigne passée à 130 °C vers 18:45, T 130–137 °C ensuite
- Fenêtre ASC : panneaux « CHAMBRE » et « ARRIERE SECHOIR » avec bargraphes consigne 85,000 / mesure 79,278 / erreur 5,722 et TEMP MOTEUR 40,000 (valeurs identiques dans les deux panneaux à 00:47)
- T°C1 sortie chambre (consigne affichée 120 °C) : en marche 120–140 °C, chutes à 60–90 °C à chaque arrêt brûleur ; 03/10 120–135 °C la nuit, plusieurs creux à 80 °C le matin, ~60–80 °C de 13 h à 21 h, retour 120 °C le soir ; 04/10 nombreux creux à 70–80 °C (05–07 h, 09 h, 12 h, 14 h, 22 h), 130–140 °C entre ; 05/10 trou ~05–07 h, creux 80 °C 11–15 h, 125–130 °C ensuite ; 06/10 creux à 80–90 °C 02–03 h et 08–10 h, 135–145 °C l'après-midi avec oscillations ; 07/10 130–140 °C la nuit, ~55–60 °C 07:30–16:00 (arrêt), 130–140 °C le soir (consigne 140 vers 23 h)
- T°C4 chambre de mélange (06/10 14 h → 08/10) : 06/10 après-midi oscille 110–190 °C au rythme marche/arrêt du brûleur (~20 min), creux 75 °C vers 14:45 ; 07/10 ~150–180 °C, palier plus haut ~220–260 °C le 07/10 soir puis ~300 °C après la fermeture du registre arrière ASC (vers 17:40–18:20) ; 08/10 00 h 240–260 °C avec un creux à ~100 °C vers 20:30 le 07/10
- Zone extraction (07/10 → 08/10) : en marche 125–135 °C et ~1–2 % d'humidité ; creux ponctuels à ~100 °C ; pendant l'arrêt du 07/10 (~09–16 h) ~60–65 °C avec humidité 5–8 %
- TC3 arrivée gaine de récupération au séchoir (06/10 soir → 08/10) : 06/10 soir 180–185 °C ; 07/10 nuit 175–185 °C, baisse à ~130 °C le matin puis ~110 °C ; 07/10 journée ~100–110 °C ; remonte à 125–150 °C le soir et ~155 °C à minuit — suit la température de récupération du four
- P2 séchoir (08/10 nuit) : 3–4 mbar avec fluctuations rapides
- Balancelle (07/10 20 h → 08/10 01 h) : marche par impulsions, ~40–45 Hz quand elle avance ; arrêtée 20:00–20:30 puis avance régulièrement
- T.Fumée four (consigne 160 °C) : 03/10 85–95 °C le matin, montée dès 13 h jusqu'à 150–160 °C vers 19–21 h, 125 °C à minuit ; 04/10 125 °C à 0 h en baisse jusqu'à 85 °C vers 11 h, 90–100 °C ensuite, 80 °C vers 22 h ; 05/10 85–100 °C, trou 05–08 h, jusqu'à 120 °C vers 15 h ; 06/10 85–105 °C ; 07/10 85–100 °C, pic 130 °C 06–08 h, ~110 °C en journée, 90–95 °C le soir
- Bouton « Vitesse » du tirage : courbe rouge = vitesse tirage (tr/min), courbe verte = probablement le temps de poussée (min, échelle 0–55 ; 12 au moment du relevé, à confirmer)
- Tirage tr/min : 03/10 1200 jusqu'à 09 h, 1100 09–14 h, ~1000 14–21 h avec chute ~800 vers 19–21 h, 1000–1150 en fin de journée ; 04/10 1050–1100 en montée jusqu'à 1200 vers 20 h ; 05/10 1200 jusqu'à 08 h, 1100 09–14 h, 1050–1100 14–16 h, 1200 dès 16 h ; 06/10 1200 puis 1250 dès 15 h ; 07/10 1250 jusqu'à 08 h, 1100 08–15 h, 1100–1200 15–19 h, 1200 dès 19 h
- Courbe verte (poussée, min) : 03/10 12,5 jusqu'à 10 h, 15–25 10–17 h, ~16 17–21 h, 55 (max) 21–23 h, puis 12,5 ; 04/10 15 (0–5 h), 12,5 (5–8 h), 15, 20 (9–11 h), 15, 20 (13–16 h), 15, 12 dès 17 h ; 05/10 12,5, 18 (10–12 h), ~37 (12–15 h), 25, 20, 15 (17–20 h), 12,5 ; 06/10 ~12,5–13 toute la journée ; 07/10 12,5 jusqu'à 05 h, 20 (05–17 h), 15 (17–19 h), 12,5 ensuite
- Bouton « Température » du tirage = profil du préchauffage four : T.fumée, TC2, TC3, TC4 (07/10 12:38 : 114 / 384 / 468 / 507 °C) ; sur 03/10 → 07/10 : TC4 520–580 °C, TC3 480–530 °C, TC2 350–420 °C, T.fumée 85–150 °C ; 03/10 hausse générale en fin d'après-midi (TC4 ~580, TC3 ~530, TC2 ~420, T.fumée ~150 °C) ; 04/10 baisse lente toute la journée (TC2 440 → 360 °C) ; 05/10 trou ~05–07 h ; 06–07/10 stables (TC4 ~530, TC3 ~490, TC2 ~360–380, T.fumée ~90–110 °C)
- REF WAGON TC25 (four) : signal très bruité 0–120 °C, inexploitable en courbe
- Brûleurs arrière séchoir B1/B2 (05/10 ~09 h → 08/10 01 h) : mesure 55–75 °C ; B2 fonctionne par cycles marche/arrêt (nombreux cycles 06/10 17–24 h et 07/10 00–08 h, puis 07/10 18:15–19:00, 19:15–20:15, 20:25–20:45 et en continu dès 20:55) ; B1 quasiment jamais en marche ; pendant l'arrêt du 07/10 (08–16 h) brûleurs arrêtés, mesure ~50 °C
- TC2 séchoir (07/10 20 h → 08/10 01 h) : 40–50 °C, bruité
- P3 séchoir (08/10 00:20–01:00) : −0,1 à −0,3 mbar
- P4 séchoir (même fenêtre) : ligne parfaitement plate à −1,2 mbar → mesure figée, à vérifier
- P2 séchoir sur 03/10 → 08/10 : 2–5 mbar en marche ; chutes à 0 le 03/10 ~09–11 h, ~1,5 mbar 03/10 ~14–18 h, chutes à 0 le 04/10 vers 00 h et 13 h, 05/10 trou ~05 h puis 0 vers 11–13 h, 06/10 vers 01 h, 12 h et 18 h, 07/10 vers 05 h et 07–09 h, valeurs basses vers 14 h (arrêt)
- Zone extraction sur 03/10 → 08/10 : en marche 110–130 °C et 1–3 % ; 03/10 100–120 °C le matin, descente à 50–60 °C 13–21 h ; 04/10 oscille 70–120 °C avec nombreuses chutes ; 05/10 ~120 °C, trou ~05–08 h, chutes vers 13 h ; 06/10 120–130 °C ; 07/10 120 °C la nuit, ~45 °C 09–16 h (humidité jusqu'à ~8 %), 130–135 °C le soir
- T°C4 chambre de mélange sur 03/10 → 06/10 : 03/10 matin 150–260 °C très variable, 03/10 après-midi et nuit ~60–100 °C (brûleur arrêté) ; 04/10 → 06/10 150–200 °C avec chutes fréquentes à 50–100 °C (arrêts brûleur) ; 05/10 trou ~05–08 h
- Pression four sur 06/10 → 08/10 : consigne 0,6 mbar constante ; mesure centrée 0,3–0,8 mbar avec écarts très fréquents de −1,5 à +2,5 mbar (portes) ; 06/10 ~07–09 h nettement plus basse (~−0,5 à 0 mbar)
- Courbe coupe sur 30/09 → 08/10 : valeurs plates (aucun enregistrement) jusqu'au 03/10 ~19 h ; 03/10 19 h → 06/10 ~07 h production 5–7 coupes/min (pics 10–15) avec interruptions, moyenne ~5,7–6 ; 06/10 ~07 h → 07/10 ~14 h valeurs plates (coupes 3,5 figé) ; reprise 6–7 coupes/min dès 07/10 ~14 h — mêmes périodes que la courbe du malaxeur à 0 A
- Courbe coupe : poste actuel bascule 1/2/3 aux heures de changement de poste
- T.AvantF.3 (07/10 20 h → 08/10 01 h) : stable 515–525 °C

## Centrales électriques (30/09 → 08/10)
- Transfo N1&N2 I moy : 400–1600 A ; 800–1500 A en production, 350–600 A pendant les arrêts (30/09 midi, 02/10 soir, 03/10 soir, 05/10, 07/10 journée) ; P/Q du transfo non cliquables (pas de courbe)
- Transfo N1&N2 PF : 0,95–0,98 en marche normale ; monte à 1,1–1,3 (surcompensation, gradins restant enclenchés à faible charge) pendant les arrêts : 30/09 soir → 01/10 0 h, 02/10 nuit (0–06 h), 07/10 ~12–18 h ; chutes ponctuelles à 0 (coupures)
- Préparation P : 0–70 kW, fonctionnement intermittent ~50–60 kW en marche (arrêts quand stockeurs pleins), pics isolés 230–290 kW (02/10, 06/10)
- Fabrication P : en production 350–500 kW (pics 550), à vide 50–80 kW ; à zéro 30/09 ~14–16 h et 07/10 ~10–16 h ; courbe active aussi le 06/10 (centrale fabrication inclut la Lacker)
- Séchoir P : 150–320 kW, le plus souvent 200–300 kW ; bas à 30–50 kW le 01/10 ~16–19 h et 02/10 ~16 h, ~100 kW le 03/10 soir, 140–170 kW le 07/10 midi
- Four P : 50–75 kW stable, ~45 kW le 03/10 soir et le 07/10 midi
- Compresseur P : du 30/09 au 05/10 ~midi seulement 10–25 kW (anomalie TC), saut le 05/10 ~12 h à 35–50 kW ; dès le 06/10 ~10 h cycles charge/décharge 30–82 kW ; 07/10 soir 35–50 kW → mesure corrigée depuis le 05/10 midi
- Fabrication PF : 0,70–0,75 en production, chute à 0,15–0,20 à vide, pics ~0,9 (01/10, 02/10)
- Séchoir PF : 0,75–0,88, creux à ~0,6 lors des arrêts
- Fabrication Q : 330–480 kVAR presque en permanence, y compris à vide (50–80 kW) ; à zéro seulement 30/09 ~14–16 h, 02/10 ~22 h, 07/10 ~10–16 h ; pics isolés 600–1000 kVAR (démarrages)
- Pression tirage four (mb) : 03/10 −1,8 en montée progressive jusqu'à ~−0,8/−1,1 vers 19–21 h puis −1,3 ; 04/10 −1,5 à −1,8 ; 05/10 −1,8, trou 05–08 h, ~−1,3 vers midi, −1,6 le soir ; 06/10 −1,7/−1,8, valeurs absentes ~09–16 h, −1,8 ensuite ; 07/10 −2,0 la nuit, −1,3 dès ~09 h (arrêt), −1,5 le soir
- T.REC (case bas droite du four, 88 °C) 02/10 → 08/10 : 02/10 130–180 °C jusqu'à 10 h, chute à 55 °C vers 11 h, 100 °C vers 16 h, 120 °C vers 22 h ; 03/10 40–80 °C, pic 165 °C vers 09–10 h, retombe à 40 °C vers 15 h puis 35–40 °C ; 04/10 35–50 °C (60 °C vers 13 h), remonte dès 22 h ; 05/10 100–110 °C 01–04 h, trou 05–07 h, 90–100 °C 07–11 h, 50 °C vers 13 h, 110–140 °C vers 23 h ; 06/10 90–120 °C la nuit, 45–60 °C 08–11 h, 140–180 °C de 16 h au 07/10 03 h ; 07/10 chute brutale vers 04 h à 45 °C, 45–55 °C jusqu'à 20 h, ~100 °C à 01 h le 08/10
- Extraction air humide (ventilateur N°1 en Hz + marche) 02/10 → 08/10 : 02/10 38–48 Hz modulé ; 03/10 40–48 Hz la nuit, 38 Hz fixe ~09–15 h, 35 Hz puis 22 Hz ~16–20 h, 45 Hz vers 21 h ; 04/10 35–48 Hz modulé ; 05/10 45 Hz, trou 05–07 h, 30 Hz fixe ~09–15 h, 45 Hz ensuite ; 06/10 45 Hz fixe, creux 30–35 Hz vers 03 h et 09–11 h, 30–45 Hz modulé 11–22 h ; 07/10 30–45 Hz 01–10 h, 30 Hz fixe 10–19 h (ventilateur arrêté ~15–17 h), 33–45 Hz le soir, 45–47 Hz vers 01 h le 08/10
- Archive REF WAG (empilage) : référence du wagon et 3 piles par wagon ; ne garde que les ~31 derniers wagons (07/10 01:22 → 08/10 01:16) ; durées 21–59 min hors arrêt, poste 3 la nuit, 1 le matin, 2 l'après-midi
- Préparation PF : 0,4–0,5 en marche ; à l'arrêt −1 (parfois −2), sans signification
- Four PF : 0,85–0,90 stable (chutes à 0 = coupures)
- Compresseur PF : 0,80–0,88 ; dès le 06/10 cycles fréquents à 0,6–0,7 (marche à vide / décharge)
- Fabrication I : ~500 A à vide, 900–1000 A en production (pics 1 300–1 500 A aux démarrages) ; 0 A 30/09 ~14–16 h, 02/10 ~22 h, 03/10 soir, 07/10 ~10–16 h
- Séchoir I : 250–550 A, le plus souvent 400–520 A ; bas 70–150 A le 01/10 ~16–19 h et 02/10 ~16 h, ~270 A le 03/10 soir, 230–260 A le 07/10 midi
- Séchoir Q : 150–200 kVAR en marche (pics 300 au démarrage) ; ~40–100 kVAR lors des arrêts
- Four I : 85–125 A (≈ 75 A le 03/10 soir) ; Four Q : 28–45 kVAR stable
- Préparation I : 0 A à l'arrêt, 200–230 A en marche, pics 300–1 200 A aux démarrages ; Préparation Q : 0 à l'arrêt, 130–140 kVAR en marche (PF ~0,4)
- Compresseur I : 70–100 A en général, périodes à 120–140 A (03/10, 05/10 soir, 06/10), pics 160–170 A (01/10, 05/10) ; le courant ne change pas de niveau le 05/10 alors que P passe de 10–25 à 35–50 kW → c'est la mesure de puissance qui était fausse avant le 05/10 midi
- Compresseur Q : 10–15 kVAR jusqu'au 05/10 ~12 h, puis 30–35 kVAR, cycles 30–48 kVAR dès le 06/10 ~10 h
- Toutes les courbes des centrales (I, P, Q, PF de chaque départ + transfo I et PF) relues sur 30/09 → 08/10

## Durée de fonctionnement centrale (synoptique four) — 08/10/2026 01:46
- Chronomètre des centrales à feu (T1, T2, C1, C2, C3) : poste actuel 2:50:15, 3:25:45, 3:46:55, 3:38:17, 0 ; poste précédent 2:02:00, 3:52:00, 5:07:00, 6:17:00, 0 ; 24 h 4:53:05, 7:17:55, 8:54:00, 9:56:15, 0 ; 24 h précédentes 0, 0, 0:12, 0:14, 0 (compteur probablement remis à zéro)
- Gaz général : index 277, débit 0 (compteur HS) ; paramètre T 60 min, C 3,5
- Gaz séchoir : index 511 214 ; débit brut 120,5 m³/h, corrigé 416,1 Nm³/h ; poste 546 m³ / 1 908,9 Nm³ (précédent 507 / 1 762,7) ; 24 h 1 053 m³ / 3 671,6 Nm³ ; paramètre T 30 min, C 3,5
- Gaz four : index −510 937 et débits négatifs (−67 m³/h, −229,5 Nm³/h) car calculé = général (HS) − séchoir → inexploitable
- Correcteur de gaz (totaliseur usine) : 38 179 118 Nm³ ; débit brut 292,3 m³/h, corrigé 1 017,3 Nm³/h ; pression 2 837,5 mbar ; température 25,5 °C ; C 3,5 → gaz four réel ≈ 1 017 − 416 ≈ 601 Nm³/h à cet instant
- Historique gaz séchoir (30/09 → 08/10) : moyenne 250–450 Nm³/h en marche, instantané 0–500 en tout-ou-rien fréquent ; débit nul 30/09 ~15–18 h, 01/10 ~13–20 h, 02/10 matin (faible), 03/10 ~12–21 h, 05/10 trou ~05–08 h, 07/10 ~08–17 h ; reprise ~400–450 le 07/10 soir
- Historique gaz général plat à 0 ; gaz four non exploitable ; le correcteur n'a pas de bouton historique — son débit corrigé instantané est la seule mesure valable pour le four par soustraction
- Archive correcteur DEBIT BRUT (cliquer « Débit Brut » dans Durée de fonctionnement centrale ; × ~3,5 pour Nm³/h) : 03/10 250–340 m³/h 0–07 h, ~200 07–14 h, 100–200 14–21 h, 250–330 22–24 h ; 04/10 200–340 avec chutes fréquentes ; 05/10 300–330 0–05 h, trou 05–08 h, 250–300 08–11 h, 100–200 11–16 h, 250–350 ensuite ; 06/10 250–340, ~200 vers 08–10 h ; 07/10 200–350 la nuit, 150–250 07–08 h, 50–200 09–16 h (four seul), 250–340 de 16 h à 02 h le 08/10 → arrêts séchoir : ~100–200 m³/h bruts ≈ 350–700 Nm³/h = four seul
- Archive PRESSION (03/10 → 08/10) : stable 2 800–2 950 mbar (2 940 le 07/10 13:54) ; chutes = coupures ; trou 05/10 ~05–08 h
- Archive TEMPERATURE : ~25 °C la nuit, 30–35 °C vers 12–15 h ; 32,2 °C le 07/10 13:55
- Historique gaz séchoir par fenêtres de 8 h (03/10 02 h → 08/10 02 h) : deux niveaux nets ~280–300 et ~430–470 Nm³/h, et 0 à l'arrêt ; moyenne 30 min 250–450. Détail : 03/10 02–09:30 cycles 280–450, 0 de 09:30 à 11:15, 280–450 11:15–14:00, 0 de 14:00 à ~21:30, 280–300 puis 0 ~22:30–23:15, ~450 dès 23 h ; 04/10 450–470 02–05 h, 280–300 05–06 h, 0 ~06–07:30, 280 08–10 h, 280 puis 450 l'après-midi avec arrêt ~13–14 h (~50), 430–470 le soir avec creux à 100–200 vers 22 h ; 05/10 280–300 jusqu'à 05 h, trou 05–07:30, ~280–290 de 10 h à 18 h, 400–450 18–02 h ; 06/10 ~280–300 02–10 h avec pointes 430, cycles 280–450 10–18 h, 300–450 18–02 h ; 07/10 cycles 280–450 00–08:30, 0 de ~08:30 à 15:30, ~290 dès 15:30 puis alternance 290/440 le soir

## Rapport tiré de cet examen
- rapport PDF « Rapport_Courbes_WinCC_B12_03-08_10_2026.pdf » (9 pages, 08/10/2026 02:14 : synthèse, production, électricité, gaz, four, séchoir, anomalies, propositions, limites) ; rangé dans la page privée « Archive électrique WinCC » (https://claude.ai/code/artifact/cb1853ec-f37c-409d-9f03-ec47ac386069) avec le projet de régulation révision 7 (Projet_Regulation_Four_Sechoir_B12_rev7.pdf) ; à garder en mémoire, pas à enregistrer sur le PC WinCC

## Examen du 11-12/10/2026 (historique 08/10 → 12/10)
- MESURE AMPER 11/10 ~23:00 : transfo I 1290 A, U L-N 236 V, U L-L 409 V, P 925 kW, Q 199 kVAR, PF 0,98, 7 944 546 kWh, 1 713 993 kVARh ; prép 6 A/-3 kW/PF -1,00/2 007 826 kWh ; fab 885 A/448 kW/433 kVAR/PF 0,72/3 196 332 kWh ; séchoir 495 A/292 kW/191 kVAR/PF 0,83/1 731 311 kWh ; four 114 A/68 kW/41 kVAR/PF 0,85/3 482 914 kWh ; comp 134 A/82 kW/48 kVAR/PF 0,87/2 790 583 kWh ; régulation PF SP 0,98 PV 0,98
- Machines 23:00 : broyeur à meule 0, broyeur M1 0, M2 1, dégrossisseur 1 0, dégrossisseur 2 0, mélangeur 83 (max 80!), malaxeur 93 (max 90!), cyl. rapide 116 (max 145), cyl. lent 43 (max 45), brise-mottes 2
- Deltas énergie depuis 08/10 ~01h (≈93,7 h) : transfo +66 249 kWh (≈707 kW moy) ; fab +27 390 ; séchoir +20 021 ; four +5 771 ; comp +5 965 ; prép +83 kWh (suspect, compteur prép quasi figé/PF -1)
- Problème communication séchoir 11/10 ~22:21 : horloge automate figée 15-20 s puis rattrapage ; défauts ExtractAirHum1/2/3 (42 Hz affiché, 0 tr/min), P2 0,00 mbar ; à 22:59 retour normal (45 Hz, 1380 tr/min, P2 3,14 mbar). Page TIME CPU : CPU CHARGEUR 22:59:21 vs CPU FABRICATION 22:54:03 (dérive ≈5 min). Postes : 1 = 5-13 h, 2 = 13-21 h, 3 = 21-5 h. Horloge PC distante ≈1 h en retard sur Paris
- Archives MESURE AMPER 08/10 00h → 11/10 23h :
  - Mélangeur (max 80) : 30-100 A, pointes 120-140 ; arrêts 08/10 ~04h30-11h30 (pointe 255 A ~08h30), 09/10 ~11h-15h40 (palier 30 A puis 0, pointe 170 au redémarrage), 11/10 ~07h20-11h ; pointe 165 A au redémarrage 11/10
  - Malaxeur (max 90) : 25-130 A, mêmes arrêts ; pointes démarrage >260 A (08/10 11h30, 09/10 15h40, 11/10 11h)
  - Cylindre rapide (max 145) : 100-140 A ; SURCHARGE nuit 10→11/10 ~00h-07h à 200-225 A ; arrêts courts 09/10 ~05h, 10/10 ~01h et ~14h30, arrêt 11/10 07h30-11h
  - Cylindre lent (max 45) : 40-50 A, mêmes arrêts
  - Broyeur à meule (max 250) : cyclique (toutes 2-3 h) 30-45 A, démarrages 140-160 A ; arrêté depuis 11/10 ~08h
  - Brise-mottes (max 250) : marche 08/10 00-10h (25-30 A, pointes >250) puis à vide 2-3 A ; pointes isolées 10/10 ~04h (205 A) et 11/10 ~14h30
  - Broyeur marteau 1 (max 150) : cycles 55-70 A (démarrages 160-200 A) 08/10 11h → 11/10 07h ; 11/10 12h-23h démarrages très fréquents 150-260 A (anormal)
  - Broyeur marteau 2 (max 161) : arrêté 08/10→11/10 12h ; en marche 11/10 12h-23h à 100-260 A (dépassements)
  - Dégrossisseur 1 (max 50) : cycles 45-70 A (au-dessus du max), démarrages >200 A, continu cyclique sur 4 jours
  - Dégrossisseur 2 (max 35) : cycles 30-38 A, démarrages 160-170 A
- Centrales 08/10 00h → 11/10 23h :
  - Transfo I : 700-1450 A en production ; arrêts fab 08/10 05-09h ~500 A puis 09-11h 350-400 A, 09/10 13-15h ~400-450 A, 11/10 07h30-11h 320-350 A ; micro-coupures à 0 vers 08/10 ~10h30, 09/10 ~12h, 11/10 ~14h ; pointe >2000 A 10/10 ~05h ; soir 11/10 900-1700 A (courbes transfo dispo : I, U L-N, U L-L, PF)
  - Transfo PF : 0,95-0,98 en marche ; >1 aux arrêts fab : 08/10 06-09h 1,05-1,25, 09/10 13-15h 1,2-1,6, 11/10 07-11h 1,3-1,5 ; creux 0,8 09/10 ~12h
  - Séchoir I : 350-550 A ; 08/10 05-09h 350 A puis 09-12h 100-110 A, 09/10 12-14h 0 puis 180-190 A, 11/10 08-11h ~60 A
  - Fabrication I : 500-850 A en marche ; ~0-40 A 08/10 05h30-11h30, 09/10 12h-15h30, 11/10 07h-11h ; pointes 1300 A 10/10 ~09h, 1200 A 11/10 ~10h30
  - Four I : 90-120 A ; 80-90 A 08/10 09-12h, 75-85 A 09/10 13-17h ; pointes 145 A 10/10 ; chutes à 0 aux micro-coupures
  - Compresseur I : 08/10 00-05h ~80 A, 05-08h 160-175 A ; 08/10 08h → 09/10 23h cycles 70-100 A ; 10/10 00-07h 140-170 A (pointe 240) ; depuis 10/10 07h cycles 60-140 A
- FOUR 11/10 23:20 : poussée 660 s (11,0 min), wagons/24h 43,636 (actuel 4, ancien 41), B12 ; tirage 1090 tr/min, pression tirage -1,9 mb ; T.Fumée 104 (csg 160) ; AvantF2 475, AvantF3 520 ; Turbo1 786/800, Turbo2 801/810 ; ZF1 859/880, ZF2 874/890, ZF3 512 (csg 0), ZF4-6 0 ; contre-pression 893 tr/min ; pression four +0,7 mb (csg +0,6) ; T.récup voûte 236 ; P récup +0,00 ; refroidissement 620/650 ; récupération 675 tr/min ; T.récup bas 451/500 ; T.REC 100 ; T.Recycl 363/350 ; brûleur latéral 896/600 ; réf wagons TC25 99, TC16 63, TC26 98
- FOUR historique 08/10 → 11/10 :
  - Turbo1 (csg 800, 790 le 09/10) : 760-800 °C ; creux 705 °C 08/10 01-02h ; plat 790 08/10 10-14h30 (arrêt) ; 09/10 11h30-13h30 trou/chute ; chutes à 0 aux micro-coupures (11/10 ~14h)
  - Turbo2 (csg 810) : 790-810 °C ; creux 760 08/10 01-02h
  - ZF1 (csg 880) : 850-875 °C ; 835-845 08/10 01-03h ; ~870 après 09/10 13h
  - ZF2 (csg 890) : 870-890 °C ; 860 08/10 01-03h
  - ZF3 : ~510 °C (non régulée) ; ZF4-6 à 0
  - T.récup voûte : 08/10 220→250 °C (07-10h), après arrêt chute à 110 °C 14h puis 220 à 23h ; 09/10 190-240, palier 230 (11h30-13h30), pointe 280 à 14h, chute 140 à 17h, 160-170 à 23h ; 10/10 160→250 (10h), 230, 190 (18-21h) ; 11/10 250-280, 0 à 14h (coupure), 300 à 19h, 240 à 23h
  - T.Fumée (csg 160) : 08/10 85-100, 115-130 pendant arrêt 10-14h ; 09/10 85-95 puis 140 °C 17h après redémarrage, 100-110 ; 10/10 105→80-90 ; 11/10 90-115, 80-90 de 11 à 16h
  - Tirage + poussée : 08/10 1120-1130, 09-10h 1050, arrêt 10-13h 800-900 (poussée 25→60 min), 14h poussée 12, après-midi 1150-1200 ; 09/10 1100-1130, arrêt 11h30-13h, 13-17h 800-850 (poussée 40), puis 1050-1100 (poussée 20→15→12), 23h 1180 ; 10/10 1170→1130 (03h)→1090 (12h), poussée 11 ; 11/10 1090-1100, poussée 12 de 07h à 22h puis 11
- SECHOIR 11/10 23:29 : ExtractAirHum1/2/3Defaut (47 Hz, 0 tr/min), P1 0,00, P2 0,00, P3 0,00, P4 -1,20 mbar (perte signal) ; T°C4 260,5 °C (> limite 250) ; T°C1 134,9 ; TC3 145 ; TC2 41,3 ; recyclage 35,5 %/63,5 °C ; avant recyclage 77,9 °C/14,5 % (csg 85) ; ASC 126 (csg 125) ; zone extraction 124,3 °C/1,4 % (csg 120) ; brûleur à point PV 56 °C ; brûleur 2 SP 119 PV 0 ; ampérage chaîne 17,3 A (max 20,5) ; balancelle 40 Hz ; RECY 47 Hz ; cycle 26/320 ; temps brûleur actuel 0 h 49 min, 24 h précédentes 18 h 02 min
- SECHOIR historique :
  - T°C1 (csg 130, 135 le 10/10, 125 depuis 10/10 22h) : 08/10 140 jusqu'à 04h, 85-90 (04-09h), 60-70 (09-13h), 80 (13-14h), puis 130-145 avec pointe 155 vers 20h ; 09/10 140-145, chute 95 à 09h30, 13-17h 55-65 (arrêt), 17h 135-140 ; 10/10 135-142, creux 95 13h et 100 21h ; 11/10 135-140, 05h creux 100, 07h-11h30 descente à 80, 14h coupure, 15-23h 125-145 avec creux à 100 (17-21h)
  - T°C4 (limite 250) : en marche 240-270 °C presque en permanence ; creux 120-170 lors des arrêts (08/10 05h-14h 130-150, 09/10 ~03h/05h30/06h, 07h, 10h30-13h30, 19h30 ; 10/10 13h30-14h30 100, 21h 120 ; 11/10 05h30-06h30 120, 07h30-11h 145) ; pointes au redémarrage 290-300 (08/10 14h, 09/10 13h30, 11/10 11h) ; 11/10 20h20-21h50 pompage fort 130↔300 °C ; 22-23h30 260-280
  - Zone extraction (csg 120, ~1 %) : 125-132 °C en marche ; 08/10 03-05h 130→85, 05-10h 80-85, 10-13h 45-60, 13-14h remontée à 125 ; 09/10 125-130, ~10h 95, 13-17h 50-60, 17h 130 ; 10/10 ~130 (creux 95-105 vers 08h et 14h) ; 11/10 130, creux 110 à 05h30, 07h30 75 jusqu'à 11h puis 130, coupure ~14-15h, 17h30 100, 20h20-21h50 oscillations 115-130, 23h 125
- GAZ 11/10 23:35 : totaliseur 38 259 527 Nm3 ; débit brut 225,6 m3/h, corrigé 798,3 Nm3/h ; 2881,4 mbar ; 24,2 °C ; C 3,5. Générale : index 277, débit 0,0 (compteur à impulsions ne compte pas). Séchoir : index 519 105, 97,9 m3/h brut, 341,4 Nm3/h ; poste 254 m3 / 896 Nm3 (précédent 772 / 2716) ; 24 h 1026 m3 / 3612 Nm3 (précédent 1953 / 6872). Four calculé : index -518 828, -67 m3/h, -229,5 Nm3/h → anomalie
- GAZ historique séchoir : régulation tout-ou-peu ~300 ↔ ~420 Nm3/h (moyennes 330-430) ; arrêts à 0 : 08/10 ~07h40-13h30, 09/10 ~13h-17h, 11/10 ~11h (court) ; creux 100-150 le 08/10 ~17h et 19h, 11/10 06h et 18h-18h45 ; 11/10 20h20-21h50 marche/arrêt rapides 130↔420 (même moment que le pompage T°C4) ; 22-23h30 ~340-350
- GAZ totaliseur historique : 250-350 m3/h en marche ; 08/10 05-10h 200-220, 10-13h 50-150 ; 09/10 09-11h 150-250, 11-13h trou (200 figé), 13-17h 100-200 ; 10/10 12-14h 100-200 ; 11/10 06-09h 200-240, trou ~14h30-16h. Pression 2900-3000 mbar, chutes à 0 aux coupures (08/10 ~10h et ~13h, 09/10 ~11h et 12h30, 11/10 ~15h). Température gaz 22-27 °C (30 °C le 08/10 12-14h)
  - P2 (11/10 22h40-23h40) : 3-4,5 mbar en continu alors que le synoptique affichait 0,00 → l'automate mesure bien, c'est l'affichage/la liaison WinCC qui décroche (idem défauts extraction 0 tr/min)
  - Zone recyclage : 11/10 19-23h40 65-71 °C, H 30-35 % ; 09/10 10h40-15h40 67 → 55 °C, H 22-25 %, coupure ~13h
- Extraction 11-12/10 non terminée (arrêt à 23:43, quelqu'un utilisait le PC) : restent T.récup bas, T.REC, pression four, refroidissement, récupération/CP vitesse, AvantF2/F3, T.Recycl, brûleur latéral (four) ; TC2, TC3, P1/P3/P4, ASC, avant recyclage, brûleur à point, ampérage chaîne, balancelle, air chaud, extraction air humide (séchoir) ; P/Q/PF des départs ; historique gaz générale/four. Courbes P2/TC4/zones séchoir s'ouvrent sur 1 h ou 5 h (pas d'icône horloge)
  - T.récup bas (csg 500) : 08/10 400-460 (creux 350 ~02h), après arrêt 10h chute à 250 (14h), 300-350 après-midi ; 09/10 440-470 jusqu'à 11h, palier 410 (11h30-13h), 280 (17h), 300-350 jusqu'à 23h ; 10/10 300→460 (00-10h), 420-460, creux 300 ~19h ; 11/10 440-480, creux 400 à 04h, palier 490 13-15h, 0 à 15h (coupure), 470-500 le soir
  - Vitesse récupération : ~690-700 en régime normal ; 08/10 10-13h 800, 14-21h 710, puis 610-650 ; 09/10 13-17h 840, 17-20h30 760, puis 600 ; 10/10 12-23h ~600 ; 11/10 06-10h 790, 10-13h 680, 15h+ 690-700
  - Pression four (11/10 21h45-23h45) : 0,5-0,7 mb (csg 0,6), écarts +1,8 vers 23h00 et 23h30, -1,4 vers 23h15
  - Refroidissement (11/10 19-23h45) : 630→620 °C (csg 650)
  - Ampérage chaîne séchoir (11/10 15h40-23h45) : impulsions 15-20 A, pointes fréquentes 25-30 A (> max 20) ; arrêts ~20h40-21h et ~22h-22h30
  - 11/10 23:48 : extraction air humide revenue à 1410 tr/min ; toutes les fenêtres fermées, page SECHOIR affichée

## Synoptiques du 16/10/2026 (photos)
- MESURE AMPER 00:48 : transfo 1210 A, 237/411 V, P 833 kW, Q 187 kVAR, PF 0,98, 8 014 399 kWh, 1 736 776 kVARh ; PF auto SP 0,98 / PV 0,98, 3 gradins ON, 64 s ; prép 6 A / −2 kW / 2 kVAR / PF −1,36 / 2 016 634 kWh ; fab 865 A / 402 kW / 465 kVAR / 0,66 / 3 223 674 kWh ; séchoir 399 A / 251 kW / 131 kVAR / 0,89 / 1 752 595 kWh ; four 109 A / 66 kW / 41 kVAR / 0,85 / 3 489 105 kWh ; comp 99 A / 57 kW / 43 kVAR / 0,80 / 2 796 788 kWh
- Ampérages act/max 00:48 : meule 0/250, brise-mottes 2/250, mélangeur 62/80, malaxeur 0/90, marteau 1 0/150, marteau 2 1/161, cyl. rapide 117/145, dégrossisseur 1 0/50, dégrossisseur 2 0/35, cyl. lent 44/45
- SECHOIR 03:03 (premier relevé avec variateurs air chaud) : air chaud N°1/N°2 +40,00 Hz ; RECY 38 Hz ; extraction N°1/2/3 41 Hz, 1230 tr/min, AUTO ; balancelle 42 Hz ; chaîne max 20,7 / act 16,5 A ; recyclage 30,4 % / 68,7 °C (plage 29–34 %) ; avant recyclage 82,0 °C / 12,6 % (max 13, min 7) ; zone extraction 127,4 °C / 1,1 % (csg 127) ; ASC MANU 130 °C (csg 125) ; T°C1 134,3 ; T°C4 267,4 (> 250) ; TC3 147,7 ; TC2 40,6 ; P1 0,00, P2 2,77 mbar (26,64 mmH2O), P3 −0,50, P4 −1,19 ; B1/B2 AUTO, brûleur à point PV 67 °C ; brûleur 2 LOCAL OFF (SP 119) ; B12 ; cycle 267/320 (0:44:51 / 0:52:21) ; temps brûleur actuel 4 h 20 min 3 s, 24 h précédentes 19 h 53 min 42 s ; registres : récup AUT, chambre MAN, arrière MAN, brûleur AUT, port chambre MAN

---

# 4. Vidéo synoptiques WinCC du 16/10/2026 15:56-16:00

## SECHOIR 15:56-15:57
- RECY 38 Hz ; extraction N°1/2/3 41 Hz / 1230 tr/min AUTO ; air chaud CH1/CH2 SP 40,72 → 41,17 Hz ; balancelle 0,000 Hz ; chaîne max 20,5 / act 0,0 A
- recyclage 30,5-30,7 % / 64,9 °C (max 34 / min 29) ; avant recyclage 78,2-78,4 °C / 12,1-12,3 % (max 13 / min 9) ; zone extraction 119,8-120,9 °C / 1,1 % (csg 127)
- ASC MANU 119-121 °C (csg 110) ; T°C1 129,3-132,1 ; T°C4 241,9-248,0 ; TC3 165,0 → 161,4 ; TC2 41,6-44,0 °C
- P1 0,00 ; P2 2,45-2,47 mbar (24,9-26,0 mmH2O) ; P3 −0,37/−0,43 ; P4 −1,18 mbar
- brûleur à point PV 67-68 °C, B1/B2 AUTO ; brûleur 2 LOCAL, SP 119 ; cycle 203/320 (0:47 / 0:59:39) ; temps brûleur actuel 16 h 56 min, avant 24 h 19 h 53 min 42 s ; registres récup AUT, chambre MAN, arrière MAN, brûleur AUT, port chambre MAN
- 15:57:21 : défauts ExtractAirHum1/2/3Defaut, B2-RESET et brûleur « ?????? » (perte liaison passagère)

## PARAMETRES VITESSES (variateurs séchoir) 15:59
- Air chaud 1 et 2 en AUTO : SP régulateur 39,64 Hz, SP manuelle 40, max 43 / min 36 Hz, humidité max 13,5 / min 9,0 %, rampes 30 s
- Standby : air chaud 30 Hz / 15 min ; recyclage 30 Hz / 20 min ; air humide 30 Hz / 25 min ; brassage 30 Hz

## FOUR 15:57
- poussée 660 s (11 min), 43,636 wagons/24 h, actuel 33, ancien 42 ; B12 ; régulation auto
- Turbo1 795/800, Turbo2 800/810, ZF1 871/880, ZF2 880/890, ZF3 512 (csg 0), ZF4-6 0 ; brûleurs T1, T2, 1, 2 ON, 3-6 OFF
- AvantF2 460, AvantF3 508 ; T.Fumée 77 (csg 160) ; tirage 1106 tr/min, pression tirage −2,1/−2,2 mb ; pression four +0,4 (csg +0,7) ; T.récup voûte 257 ; P récup 0,00 ; refroidissement 639/650 ; T.récup bas 449-450/500 ; T.REC 125 ; récupération 750 tr/min ; contre-pression 862-867 tr/min, standby CP 700 ; T.Recycl 348/350 ; brûleur latéral 859/600 ; réf wagons TC25 25→90, TC16 63, TC26 98
- wagons dans le four (positions 1→26) : 53, 43, 27, 77, 2, 37, 70, 69, 68, 19, 42, 59, 21, 10, 35, 33, 6, 32, 44, 74, 28, 38, 26, 61, 72 (B8), 12 (B8) ; sortie 12 (B8) ; autres B12

## GAZ 15:57:41
- Chronomètre centrales — poste actuel T1 2:00:10, T2 1:40:07, C1 2:30:50, C2 2:14:28, C3 0 ; ancien 5:22, 4:29, 5:28, 4:20 ; 24 h ancien 16:55, 13:18, 17:25, 15:19
- Générale index 277, débit 0 (HS) ; séchoir index 526 026, 8,2 m3/h brut / 31,7 Nm3/h, poste 19,0 m3 / 67,8 Nm3, 24 h précédentes 1 010 m3 / 3 552,1 Nm3 ; four calculé −525 749 (inexploitable)
- Correcteur : totaliseur 38 352 384 Nm3 ; 332,1 m3/h brut, 1 142,6 Nm3/h ; 2 808 mbar ; 26,6 °C ; facteur C 3,4 (était 3,5 le 11/10)

## MESURE AMPER 15:57:25
- transfo 825 A, 233/405 V, P 525 kW, Q 248 kVAR, PF 0,90, 8 026 634 kWh, 1 740 134 kVARh ; régulation PF SP 0,00 / PV 0,00 / time 0
- prép 361 A / 236 kW / 34 kVAR / PF 0,99 / 2 018 007 kWh ; fab 541 A / 68 kW / 373 kVAR / 0,18 / 3 229 240 ; séchoir 349 / 219 / 106 / 0,90 / 1 756 099 ; four 106 / 65 / 35 / 0,88 / 3 490 087 ; comp 85 / 49 / 34 / 0,83 / 2 797 711
- ampérages act/max : meule 0/250, brise-mottes 2/250, mélangeur 32/80, malaxeur 0/90, marteau 1 124/150, marteau 2 114/161, cyl. rapide 101/145, dégrossisseur 1 46/50, dégrossisseur 2 31/35, cyl. lent 43/45

## FABRICATION / EMPILAGE 15:57-15:58
- B12, 16 pcs/coupe, 2160 pcs/wagon, poste 2 ; 4,14 coupes/min, 6,12 moy/poste ; 24 h ancien 1198 coupes / 19 168 pcs / 8,9 wagons ; arrêt mouleuse poste 0:22:41 (ancien 1:20:55), 24 h 14:42:59 (ancien 9:03:28) ; doseurs 3/2/1 = 9/22/18 Hz, stockeurs 4/4 ; mouleuse L2 3,08 coupes/min, 7,3-7,5 bar, N°7, 0 Hz, 1 A (à l'arrêt)
- Empilage : wag/poste actuel 7,0 (ancien 17,7), 24 h 41 (ancien 44), temps wagon 0 h 11 (ancien 0 h 25), pile 2/3, couche 3/10 ; file 23, 22, 41, 4, 65
- Archive empilage 15/10 18:11 → 16/10 15:46 : produit 5 (PLTR) à 18:11, 2 (B8) 18:37-22:22, 1 (B12) dès 22:51 ; durées 21-56 min ; 16/10 : 32 wagons de 00:06 à 15:46 ; codes 1=B12 2=B8 3=H16 4=H19 5=PLTR

## Courbes
- Avant recyclage 15/10 16 h → 16/10 16 h (csg 85) : 90-100 °C 15/10 17-23 h, 78-85 °C 01-04 h, 85-90 °C ensuite, ~95 vers 13 h, 78-80 °C après 14 h ; H 7-13 % (03:57 : 88 °C / 10 %)
- Recyclage 16/10 11-16 h : 58-70 °C en dents de scie, H 28-35 % (13:27 : 67 °C / 31 %)
- T°C4 16/10 11-16 h : pompage continu 150-180 ↔ 280-310 °C, période ~10 min (312 °C à 13:28), amplitude plus faible après 14 h (150-270 °C)
- P3 16/10 10:30-16 h : −0,3 à −0,8 mbar, pic +1,6 vers 15:28 ; TC3 : courbe non chargée

---

# 5. Vidéo poussée four du 14/10/2026 (03:04-03:13)

- réglage : poussée 660 s = 11,0 min, 43,636 wagons/24 h, B12, Régulation En Auto ; wagons/24 h actuel 11-12, ancien 39
- poussée observée de 03:05:36 à 03:07:06 ≈ 1 min 30 s (porte d'entrée ouverte, têtes de brûleurs passées du vert au rouge)
- Turbo 1 (csg 800 °C), zoom 01:15-03:10 : chute à chaque poussée toutes les 11 min ; creux 762-770 °C (−30 à −38 °C) ; chute ≈ 1 min ; retour ≥ 796 °C ≈ 5 min après (jusqu'à 9 min) ; creux vers 01:18, 01:28, 01:40, 01:51, 02:01, 02:13, 02:24, 02:35, 02:46, 02:57, 03:08
- Centrale 1 (csg 810 °C) : creux 788-795 °C (≈ −15 à −22 °C) à chaque poussée
- Centrales 2 et 3 (≈ 880-890 °C) : stables 860-880 °C
- courbe 24 h (13/10 05 h → 14/10 03 h) : arrêt général vers 16:30-17:00 le 13/10, puis reprise
- vitesse contre-pression : 900 tr/min normal, 700 par moments (≈ 02:00-02:05, 02:35-02:38, 03:08-03:11) ; 700 puis 814-860 pendant la vidéo (min 54, max 60)
- tirage 1 106 tr/min (min 65, max 66) ; récupération 675 tr/min (45-46) ; température récupération ≈ 649-650 °C ; pression four −1,7 à −2,1 mbar
- pression four (14/10 02:15-03:10) : −1,5 à +1,7 autour de la consigne 0,6, creux vers 02:35 et 03:03-03:05

## Discussion du 14/10/2026 (03:49-03:53) — gain gaz des variateurs (à reprendre)
- question : gain gaz des variateurs sur les ventilateurs d'air de combustion confirmé ? Réponse : gain électrique certain, gain gaz possible mais non confirmé ni chiffré
- raisonnement : pendant la poussée le gaz passe en électrovanne min mais l'air reste au même débit → excès d'air froid qui refroidit le four et part à la cheminée, puis ≈ 5 min de rattrapage toutes les 11 min ; réduire l'air pendant la poussée réduirait la chute et la remontée
- limites : une partie de la chute vient de la porte ouverte et du wagon froid ; manquent débit d'air, O₂ fumées et gaz par centrale ; vitesse mini d'air à fixer avec le constructeur CMI
- essai proposé avant achat : fermer partiellement en manuel le registre d'air d'une centrale pendant la poussée (≈ 1 min 30 s) sur quelques poussées ; comparer chute et temps de retour ; si la chute diminue nettement, comparer le gaz four sur 24 h à cadence égale

---

# 6. Rapports journaliers 30/09 → 15/10/2026

## Structure
- Postes : P1 13h-21h, P2 21h-05h, P3 05h-13h ; articles B12, B8, PL8, H16, H19 (production en wagons)
- Production verte (séchoir) et rouge (four) : wagons, tonnage, gaz (Nm3), ratio (th/t, PCS 10,099) ; F.C. 3,7544 jusqu'au 02/10, 3,5822 à partir du 03/10
- Ligne électrique : Jour / Pointe jour / Pointe soir / Nuit (kWh) ; total, ratio verte, ratio rouge, ratio total
- À partir du 03/10, valeurs en rouge = conso séchoir puis four en Nm3 ; « consommation sur PC » = électricité 24 h lue sur WinCC

## Données (verte P1/P2/P3 ; t ; gaz ; ratio || rouge ; t ; gaz ; ratio four ; ratio total || élec J/PJ/PS/N ; total ; ratios V/R/T ; PC)
- 30/09 : V B12 9/12,67/7=28,67 ; 123/174/96=393 t ; 1633/2478/1490=5602 ; 132/143/155→144 || R B12 8,33+B8 1,67/12/7 ; 128/152/88=368 t ; 3968/4310/3030=11308 ; 310/284/343→310 ; 442/427/498→454 || 5984/2339/1/7242 ; 15566 ; 30/10/42
- 01/10 : V 18,33/16,67/4=39 ; 245/223/54=522 ; 3841/3004/830=7674 ; 156/135/155→148 || R 14/15/12=41 ; 172/185/148=505 ; 4930/5294/4381=14605 ; 286/287/297→292 ; 442/421/451→441 || 5984/2339/1/7242 (identique au 30/09) ; 15566 ; 23/7/31
- 02/10 : V 17/16,33/6=39,33 ; 228/219/80=527 ; 3172/2718/1130=7021 ; 139/124/141→135 || R 13/14/11=38 ; 160/172/135=468 ; 5155/5305/4092=14552 ; 322/308/302→314 ; 461/432/443→449 || 6951/2701/0/8448 ; 18100 ; 28/8/39
- 03/10 : V 2/14,67/8,33=25 ; 27/196/112=335 ; 340/3138/1802=5280 (5323) ; 127/160/162→159 || R 5/9/11=25 ; 62/111/135=308 ; 2751/3571/3983=10306 (9044) ; 447/322/294→338 ; 574/482/456→497 || 2267/1290/0/10848 ; 14405 ; 32/12/47 ; PC 14145
- 04/10 : V 14/16,33/6=36,33 ; 187/219/80=487 ; 3052/2884/1447=7383 (7426) ; 163/132/180→153 || R 12/14/12=38 ; 148/172/148=468 ; 4528/4922/4711=14160 (13234) ; 306/286/319→306 ; 469/417/499→459 || 3163/0/0/13905 ; 17068 ; 28/8/36 ; PC 16805
- 05/10 : V 15,67/13/13=41,67 ; 210/174/174=558 ; 2497/2242/2250=6989 (7028) ; 119/129/129→126 || R 11/13/14=38 ; 135/160/172=468 ; 4134/4958/4875=13967 (13165) ; 305/310/283→301 ; 424/439/412→428 || 8421/2275/1/7631 ; 18328 ; 26/8/39 ; PC 17885
- 06/10 : V 16/14/4,33=34,33 ; 214/187/58=460 ; 2690/2529/817=6036 (6007) ; 126/135/141→133 || R 14/14/8=36 ; 172/172/98=443 ; 4986/4994/3525=13505 (12409) ; 289/290/358→308 ; 415/425/499→440 || 6560/2537/0/8274 ; 17371 ; 30/8/39 ; PC 17302
- 07/10 : V 9/17,67/0,67=27,33 ; 121/237/9=366 ; 1959/2791/0=4750 (4771) ; 163/118/0→131 || R 10/13/8=31 ; 123/160/98=382 ; 3865/5054/3654=12574 (11507) ; 314/316/371→333 ; 477/434/371→464 || 4632/2237/0/7105 ; 13974 ; 28/9/37 ; PC 13692
- 08/10 : V 19,33/17,33/8=44,67 ; 259/232/107=598 ; 2945/3296/1497=7738 (7748) ; 114/142/140→131 || R 13/13/14=40 ; 160/160/172=492 ; 4578/4850/5008=14436 (13864) ; 286/303/291→296 ; 400/445/430→427 || 7261/2508/0/7745 ; 17514 ; 23/7/36 ; PC 17394
- 09/10 : V 8,67/20/17=45,67 ; 116/268/228=612 ; 1956/3600/3260=8816 (8859) ; 168/134/143→146 || R 7/14/14=35 ; 86/172/172=431 ; 3138/4764/4918=12821 (11967) ; 364/276/285→300 ; 533/411/429→446 || 6742/2450/0/8501 ; 17693 ; 23/8/41 ; PC 17360
- 10/10 : V B12 6+B8 7,33 / B12 13,33+B8 5,67 / B12 7 (B12 26,33, B8 13) ; 191/264/94=549 ; 2733/3281/1171=7186 (7293) ; 143/124/125→132 || R 14/14/14=42 ; 172/172/172=517 ; 5757/5151/5191=16098 (15465) ; 334/299/301→314 ; 477/423/426→447 || 2969/2578/0/11586 ; 17133 ; 25/7/33 ; PC 17217
- 11/10 : V 19/18/0,67=37,67 ; 254/241/9=504 ; 2812/2859/0=5671 (5366) ; 111/119/0→114 || R B12 5+B8 8 / B12 10+B8 5 / B12 14 (B12 29, B8 13) ; 171/192/172=535 ; 4890/5105/4825=14820 (14256) ; 286/267/280→280 ; 396/385/280→393 || 3298/0/0/14043 ; 17341 ; 27/7/32 ; PC 17127
- 12/10 : V B12 8+PL8 1,33 / 18,33 / 15,33 (B12 41,67, PL8 1,33) ; 131/245/205=582 ; 999/3138/3009=7146 (7075) ; 76/128/147→124 || R 13/13/12=38 ; 160/160/148=468 ; 4861/4428/4091=13380 (12124) ; 304/277/277→289 ; 380/404/423→413 || 8020/1998/1/8550 ; 18569 ; 26/8/40 ; PC 17847
- 13/10 : V 17/15,33/2=34,33 ; 228/205/27=460 ; 2468/2282/0=4750 (4986) ; 108/111/0→104 || R B12 12,67+PL8 1,33 / 15 / 15 (B12 42,67, PL8 1,33) ; 178/185/185=547 ; 5244/4739/5166=15149 (14112) ; 295/257/280→280 ; 403/368/280→384 || 5838/2771/0/7824 ; 16433 ; 28/7/30 ; PC 16356
- 14/10 : V 9,67/19,67/11,33=40,67 ; 130/263/152=545 ; 1802/3339/2088=7229 (7157) ; 139/127/138→134 || R 11/14/15=40 ; 135/172/185=492 ; 3980/4904/4954=13838 (13282) ; 294/285/268→284 ; 433/411/406→418 || 7069/2528/0/9115 ; 18712 ; 28/7/38 ; PC 18433
- 15/10 : V B12 3+B8 9,67 / B12 14+B8 3 / B12 17,33 (B12 34,33, B8 12,67) ; 186/233/232=651 ; 2121/2869/2937=7927 (« - ») ; 114/123/127→123 || R 13 / 14 / B12 7,67+B8 5,33 (B12 34,67, B8 5,33) ; 160/172/167=500 ; 4592/4868/4650=14110 (« - ») ; 287/282/278→285 ; 401/406/404→408 || 8514/2532/0/7975 ; 19021 ; 25/5/38 ; PC 18455

## Qualité et argile
- Qualité B12 : dégraissant 31 (30/09) puis 30 ; porosité 7,2 (7,4 du 08 au 11/10, 7,2 le 12/10) ; casse 0,5 ; poids 5850 (30/09), 5700 (01-07/10), 5650 (08-10/10), poids B8 3740 (11/10), « 5,6 » (12/10)
- 13-14/10 : dégraissant 30, porosité 7,2, casse 0,5, poids 5,6 ; 15/10 : porosité 6,8
- Voyages argile/jour (Zeramdine ; Amira) : 30/09 —;14 · 04/10 32;— · 05/10 12;1 · 06/10 —;9 · 09/10 —;20 · 10/10 —;18 · 12/10 11;16 · 13/10 —;9 · 14/10 —;10 · 15/10 —;18
- Voyages total/10 jours : 30/09 103;64 · 04/10 32;— · 05/10 44;1 · 06-08/10 44;10 · 09/10 44;30 · 10/10 44;48 · 12/10 11;16 · 13/10 11;25 · 14/10 11;35 · 15/10 11;53

## Fiches labo (mouleuse : poids, pression, A, coupes, dimensions, dégraissant / séchoir : poids, % séchage, T avant, T arrière, dimensions, % retrait / four : poids, perte %, dimensions, % retrait, poussée, porosité)
- 12/10 : mouleuse 09h 7360/22,5/405/6/320×210×160/30 ; 13h 7350/21/390/6/320×210×160/31 · séchoir 09h 6450/14,1/120/66/304×202×151/5,26 ; 13h 6300/17,5/125/69/304×202×151/5,26 · four 09h 5570/29,3/300×200×100/1,33/12/7,2
- 14/10 : mouleuse 08h 7360/22/410/6/320×210×160/31 ; 12h 4800/25/375/6/320×210×110/31 · séchoir 10h 6300/16,8/120/66/304×202×151/5,26 ; 15h 4150/15,7/80/70/304×202×102/5,26 · four 09h 5650/30/300×200×100/1,33/12/7,1
- 15/10 : mouleuse 08h 7380/23/410/6/320×210×160/31 ; 12h 7360/22/405/6/320×210×160/31 · séchoir 09h 6460/14,2/128/64/304×202×151/5,26 ; 10h 6400/15,3/128/67/304×202×102/5,26 ; 12h 6350/16,2/125/67/304×202×102/5,26 · four 09h 5700/29/300×200×150/1,33/11/6,8 ; 12h 3730/29/300×200×100/1,33/12/7

## Production sortie four
- 10/10/2026 : B12 42 wagons, 90 720 briques, somme 56 246 400 ; tonnage 517 ; prix 109
- Cumul 1-10 octobre : somme 487 468 800 ; prix moyen rouge 109 ; tonnage moyen rouge 448 ; recette moyenne 48 746 880 ; 100 % B12

---

# 7. Facture STEG MT 09/2026

- N° 81096146, mois 09/2026, district Monastir ; consommateur BRIQUETERIE JEMMEL, RTE Zeramdine Jemmel ; payeur STE Briquetterie Jem-mel, Z-I Teboulba 5080 ; code payeur 8810134, référence 591300, UR 81
- Échéance 25/10/2026 ; net à payer 133 269,466 DT ; impayés antérieurs 54 483,719 DT
- Index phases : PH1 9 659 174→9 785 967 (126 793 kWh) ; PH2 9 379 440→9 501 894 (122 454) ; PH3 8 952 226→9 072 583 (120 357) ; total 369 604
- Postes : Jour 9 388 179→9 517 973 (129 794 kWh) ; Pointe 3 418 847→3 459 693 (40 846) ; Nuit 14 394 081→14 593 040 (198 959) ; total 369 599 kWh
- Réactif : 7 333 580→7 463 882 (130 302 kvarh) ; cos φ 0,94 ; K 0,0200
- Puissances : souscrite 1200 kW partout ; installée 1600 ; max appelé réduite 1201, pointe hiver 1045, jour 1207 ; dépassement facturé 1 (réduite)
- Calcul : Jour 129 794 × 0,290 = 37 640,260 ; Pointe 40 846 × 0,377 = 15 398,942 ; Nuit 198 959 × 0,222 = 44 168,898 ; sous-total 97 208,100 ; bonification −1 944,162 → Total 1 = 95 263,938
- Total 2 = 13 690,366 : prime de puissance 13 200,000 ; dépassement 39,600 ; frais 6,134 + 57,000 + 300,000 + 87,632
- Total 3 = 24 315,162 : TVA conso 18 100,148 ; TVA redevance 2 515,524 ; RTT 3,500 ; surtaxe municipale 3 695,990

---

# 8. Rapport électrique septembre 2026 (jours 10 à 30)

- Rapport Excel « Rapport de consommation d'énergie électrique » (logo BJ) ; colonnes : rouge, vert, J, PJ, PS, N, total, PV (= total − 3600), coût HT (millimes), ratio PV, PR, total, total2
- 10 : 0, 302, 20378, 7683, 1782, 24345, 54188, 50588, 15 189 835, 168, -, 168, 0
- 11 : 278, 448, 5090, 1822, 0, 8613, 15525, 11925, 4 147 960, 27, 13, 40, 56
- 12 : 379, 489, 2122, 1762, 0, 12644, 16528, 12928, 4 157 102, 26, 9, 36, 44
- 13 : 531, 590, 2566, 0, 0, 15213, 17779, 14179, 4 121 426, 24, 7, 31, 34
- 14 : 569, 658, 9463, 2845, 0, 7485, 19793, 16193, 5 592 305, 25, 6, 31, 35
- 15 : 556, 736, 9884, 2486, 0, 8628, 20998, 17398, 5 818 438, 24, 6, 30, 38
- 16 : 581, 529, 8332, 2660, 0, 10603, 21595, 17995, 5 879 366, 34, 6, 40, 37
- 17 : 109, 96, 5195, 854, 0, 3501, 9550, 5950, 2 639 890, 62, 33, 95, 87
- 18 : 356, 352, 7639, 1045, 0, 8063, 16747, 13147, 4 441 061, 37, 10, 47, 47
- 19 : 499, 526, 4243, 2739, 0, 12093, 19075, 15475, 5 057 279, 29, 7, 37, 38
- 20 : 291, 325, 3693, 0, 0, 12671, 16364, 12764, 3 883 932, 39, 12, 52, 56
- 21 : 430, 430, 5540, 2801, 0, 8066, 16407, 12807, 4 565 269, 30, 8, 38, 38
- 22 : 404, 265, 4402, 2572, 0, 6247, 13221, 9621, 3 735 938, 36, 9, 45, 33
- 23 : 446, 581, 8445, 2677, 0, 8584, 19706, 16106, 5 471 007, 28, 8, 36, 44
- 24 : 556, 645, 9473, 2772, 0, 8611, 20856, 17256, 5 814 736, 27, 6, 33, 38
- 25 : 455, 430, 5141, 2010, 4, 9009, 16164, 12564, 4 330 566, 29, 8, 37, 36
- 26 : 468, 581, 2250, 2536, 1, 13546, 18333, 14733, 4 717 601, 25, 8, 33, 39
- 27 : 531, 622, 5036, 0, 0, 14568, 19604, 16004, 4 694 536, 26, 7, 33, 37
- 28 : 543, 581, 8632, 2665, 0, 7922, 19219, 15619, 5 373 269, 27, 7, 34, 35
- 29 : 505, 428, 5198, 1668, 0, 7274, 14140, 10540, 3 817 804, 25, 7, 32, 28
- 30 : 368, 393, 5984, 2339, 1, 7242, 15566, 11966, 4 318 824, 30, 10, 40, 42
- Totaux : rouge 8855 t, vert 10004 t, J 138 706, PJ 45 936, PS 1788, N 214 928, total 401 358 kWh, PV 325 758, coût 107 768 144
- Moyennes : rouge 295, vert 333, J 4624, PJ 1531, PS 60, N 7164, total 13 379 kWh/j, PV 10 859, coût 3 592 271/j, ratio PV 33, PR 12, total 45, total2 45
- Estimation facture (au 30) : sous-total1 107 768 144 ; sous-total2 13 370 000 ; autres 4 875 805 ; TVA 20 475 947 ; total 146 489 896 (version au 27 : sous-total1 94 258 247, TVA 17 909 067, total 130 413 119 ; totaux au 27 : 352 433 kWh, rouge 7438, vert 8602)

---

# 9. Rapports gaz septembre 2026 (jours 10 à 27)

- Conversion : Nm3 = m3 × F.C. 3,7544 ; thermies = Nm3 × PCS 10,099

## Four — jour : prod t, article, total m3, four m3, Nm3, thermies, ratio four, ratio global
- 10 : 0, B12, 3940, 2138, 8027, 81064, 0, 226
- 11 : 278, B13, 5775, 3231, 12130, 122506, 441, 656
- 12 : 379, B12, 5480, 3070, 11526, 116401, 307, 494
- 13 : 531, B12, 6270, 3950, 14830, 149767, 282, 431
- 14 : 569, B12, 5920, 3967, 14894, 150412, 265, 377
- 15 : 556, B12, 6535, 4088, 15348, 154999, 279, 405
- 16 : 581, B12, 6548, 4206, 15791, 159473, 274, 442
- 17 : 109, B8, 1509, 1387, 5207, 52589, 481, 529
- 18 : 356, B8-B12, 4780, 2743, 10298, 104003, 292, 512
- 19 : 499, B12, 6196, 3729, 14000, 141388, 283, 461
- 20 : 291, B12, 4418, 2517, 9450, 95434, 328, 550
- 21 : 430, B12, 5510, 3403, 12776, 129027, 300, 486
- 22 : 404, B12, 4823, 3357, 12604, 127283, 315, 524
- 23 : 446, B12, 6211, 3513, 13189, 133198, 298, 475
- 24 : 556, B12, 6435, 4305, 16163, 163227, 294, 419
- 25 : 455, B12, 5070, 3830, 14379, 145217, 319, 429
- 26 : 468, B12, 5785, 3773, 14165, 143056, 306, 437
- 27 : 531, B12, 6455, 4160, 15618, 157729, 297, 437
- Totaux : prod 7438 t ; total 97 660 m3 (366 655 Nm3, 3 702 846 th) ; four 61 367 m3 (230 396 Nm3, 2 326 772 th) ; moyennes 275 t, 3617 / 2273 m3, 8533 Nm3, 86 177 th
- Ratio moyen four 313 ; global 473 ; estimation gaz four TTC 195 204 527 ; gaz total TTC 316 650 253 ; max : tonnage 581, conso 4305, ratio 481

## Séchoir — jour : tonnage vert, m3, Nm3, thermies, ratio
- 10 : 302, 1802, 6765, 68324, 226
- 11 : 448, 2544, 9551, 96458, 215
- 12 : 489, 2410, 9048, 91377, 187
- 13 : 590, 2320, 8710, 87964, 149
- 14 : 658, 1953, 7332, 74049, 112
- 15 : 736, 2447, 9187, 92780, 126
- 16 : 529, 2342, 8793, 88799, 168 (B12-B8)
- 17 : 96, 122, 458, 4626, 48 (B12-B8)
- 18 : 352, 2037, 7648, 77234, 219
- 19 : 526, 2467, 9262, 93538, 178
- 20 : 325, 1901, 7137, 72078, 222
- 21 : 430, 2107, 7911, 79888, 186
- 22 : 265, 1466, 5504, 55584, 210
- 23 : 581, 2698, 10129, 102297, 176
- 24 : 645, 2130, 7997, 80760, 125
- 25 : 430, 1240, 4655, 47015, 109
- 26 : 581, 2012, 7554, 76286, 131
- 27 : 622, 2295, 8616, 87016, 140
- Totaux : 8602 t ; 36 293 m3 ; 136 258 Nm3 ; 1 376 074 th ; moyennes 319 t, 1344 m3, 5047 Nm3, 50 966 th ; ratio 160 ; estimation TTC 115 445 726
- Max du mois : tonnage 736, conso 2698, ratio 226 ; mois précédent : tonnage max 581 / min 302, conso max 6834 / min 2030

---

# 10. Audit énergétique 2016 (CRA2E / ANME)

## Identification
- BRIQUE JEMMAL (BJ), SA créée en 2001 (fondateur Bouraoui Mlayah), zone industrielle route de Zeramdine, 5020 Jemmal, gouvernorat de Monastir ; responsable cité en 2016 : Mohamed Ali Mlayah ; 90 emplois
- produits : B12, B8, plâtrière, hourdis ; capacité 225 000 t/an
- audit énergétique approfondi 2016 (3e audit), CRA2E (Tunis), cahier des charges ANME ; mesures 14-16/03/2016 ; 1er audit 2006 (actions réalisées : système de gestion d'énergie, revêtement wagons, optimisation régulation four et séchoir)

## Production et consommations
- production : 2013 = 157 325 t ; 2014 = 171 105 t ; 2015 = 171 988 t (76 % capacité) ; baisse récurrente en juillet
- électricité : 2013 = 6 223 420 kWh ; 2014 = 6 097 418 ; 2015 = 6 122 033 kWh (1 733 TEP, 970 683 DT HT)
- gaz : 2013 = 8 226 014 Nm3 ; 2014 = 7 795 622 ; 2015 = 7 309 186 Nm3 (6 578 TEP, 2 741 405 DT HT)
- total 2015 : 8 311 TEP (79 % gaz, 21 % élec), 3 712 088 DT HT ; 0,048 TEP/t ; 21,6 DT/t
- ratio électrique : 39,6 kWh/t (2013), 35,6 (2014 et 2015) ; référence 35
- ratio thermique : 470,6 th PCI/t (2013), 410,0 (2014), 382,5 (2015) ; référence 350 ; moyenne mondiale four tunnel 250
- élec 2015 par tranche : jour 34,4 %, pointe 12,0 %, soir 2,1 %, nuit 51,4 %
- cos φ moyen 2015 = 0,93 (bonification 11 329 DT) ; puissance max 2015 = 1 121 kW pour 1 200 souscrits (8 DT/kW/mois)

## Installations
- MT 30 kV STEG ; 2 transfos SACEM 630 kVA 30 kV/400 V, Ucc 4 %, Dyn11, en parallèle ; groupe 1 250 kVA ; compensation 605 kVAR
- départs TGBT : préparation, fabrication, séchoir, four, manutention wagon, empileuse, dépileur, compresseur, atelier, administration, éclairage
- préparation : 2 doseurs 6/1200 (2×(4+5,5) kW), désagrégateur 110 kW, concasseur 45 kW, broyeur à marteaux ARSAN 2×164 kW, laminoir dégrossisseur 10/8 (45+75 kW), 2 doseurs 8/1500 (2×5,5 kW)
- fabrication : mouilleur mélangeur 55 kW, cylindre finisseur 75+160 kW, groupe d'étirage malaxeur 55 kW + mouleuse type 650 316 kW, pompe à vide 26 kW (22+4)
- séchoir rapide à balancelles : 82 m × 6,35 m, 64 balancelles, air chaud 2×165 000 m3/h (2×55 kW), recyclage 2×180 000 m3/h (2×90 kW), générateur 3 500 th/h, tirage final 3×165 000 m3/h (3×30 kW, variateur), brassage 11 kW, appoint récupération 15 kW
- four tunnel EUROIMPIANTI ARIS COMPACT 46 : 110,2 m, largeur 4,6 m, 26 wagons, 9 centrales de 10 brûleurs gaz ; tirage 38,5 kW avec variateur (85 000 m3/h), récupération vers séchoir 110 000 m3/h / 44 kW, 2 ventilateurs recyclage 11 kW hors service, refroidissement rapide, sous-wagons, contre-pression ; cuisson 850-900 °C
- gaz : poste détente 20→5 bar, débit souscrit 12 500 th PCI/h ; compteur séchoir fonctionnel, celui du four non (2016)
- air comprimé : compresseur 90 kW en service ; 2 Atlas Copco GA15 15 kW et 1 Chicago Pneumatic CPC 600 45 kW à l'arrêt ; 2 sécheurs (FD110, CPX225) ; 4 ballons 2 000 L
- horaires : préparation/fabrication/séchoir 20 h/j 300 j/an ; four 24 h/j 365 j/an

## Mesures audit (mars 2016)
- jour d'audit : 520,4 t de B12, 19 243 kWh (37,0 kWh/t), 20 821 Nm3 gaz (360,1 th/t : séchoir 65,6, four 294,5)
- puissances moyennes : préparation 81,5 kW, fabrication 405,3 kW (min 71, max 479), séchage 218,1 kW, cuisson 87,6 kW, air comprimé 60 kW, divers 30,5 kW ; total 882,9 kW
- transfo : U 383-408 V, I moy ~670 A/phase, PF moy 0,908, THDi moy ~11 % (max 21 %), P moy ~802 kW, charge 70 %
- fabrication : étirage 221 kW, finisseur 140, mouilleur 33, pompe à vide 12 ; séchage : recyclage 100, air chaud 45, air humide 40, récupération 15, balancelle 8,1 ; cuisson : récupération 24,7, tirage 22,3, air combustion 14,8, contre-pression 9,9, sous-wagons 5,9, recyclage 4,9
- compresseur : charge 83 kW / décharge 49 kW, 159 Wh/m3 à 7,5 bar
- séchoir : 5,5 coupes/min × 32 pièces, cycle 3,4 h, 33 134 kg/h cru → 27 799 kg/h sec, 5 335 kg/h d'eau ; gaz 158 Nm3/h = 1 706 th/h ; air de récupération 237 °C, 96 260 m3/h, 3 584 th/h (65,7 % de l'apport) ; 991,7 th/t eau (objectif 835) ; rendement 57,1 %
- four : poussée 12 min, 2 340 pièces/wagon, cycle 15,6 h, 23 166 kg/h sec → 21 684 kg/h cuit ; gaz 709 Nm3/h = 6 381 th/h ; sorties : récupération 58,8 % (255 °C, 99 657 m3/h), décarbonatation 18,2 %, fumées 10,6 % (76 °C, 52 502 m3/h), évaporation 6,6 %, parois 4,0 % ; 294 th/t cuit ; rendement 25,6 %

## Plan d'actions 2016 (2016-2019)
- projet 1 : régulation du mélange air récupération four / air secondaire au séchoir (3 volets motorisés + sondes) → suppression gaz séchoir 1 706 th/h = 1 023,8 TEP/an, 426 672 DT/an, invest. 34 000 DT
- projet 2 : remplacer la centrale n°2 (préchauffage four) par brûleurs Turbo → 5 %, 279,5 TEP/an, 116 473 DT/an, invest. 50 000 DT
- projet 3 : contrôle d'humidification de l'argile → 51,2 TEP/an, 21 334 DT/an, invest. 35 000 DT
- projet 4 : système de gestion d'énergie (5 compteurs élec, 2 compteurs gaz, acquisition + supervision) → 83,1 TEP/an, 37 121 DT/an, invest. 71 000 DT
- total : 1 437,6 TEP/an, 601 600 DT/an, investissement 190 000 DT
