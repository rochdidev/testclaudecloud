# BRIQUETERIE JEMMEL
## Guide des bonnes pratiques de gestion énergétique
### Séchoir, four, électricité

**Document interne de la société Briqueterie Jemmel** — Zone industrielle, route de Zeramdine, Jemmel, gouvernorat de Monastir
Édition 1 — 23 octobre 2026 — établie dans le cadre du projet de régulation du séchoir et du four (produit B12)

| | |
|---|---|
| **Émetteur** | Briqueterie Jemmel — Direction technique |
| **Destinataires** | Direction, chefs de four et de séchoir, électricien-automaticien, responsable qualité, chefs de poste |
| **Objet** | Règles de conduite, de réglage et de suivi pour baisser le gaz et l'électricité à cadence et qualité égales |
| **Documents liés** | Projet de régulation B12 V1 du 19/10/2026 et son annexe programmes ; dossier consolidé du 23/10/2026 ; audit énergétique 2016 |
| **Révision** | Document vivant, mis à jour après chaque essai et chaque palier |

---

## Sommaire

1. À qui s'adresse ce guide et comment s'en servir
2. Les dix principes directeurs
3. Mesurer avant de régler
4. Le séchoir
5. Le four
6. L'électricité
7. L'automatisation : ce qu'une bonne régulation doit respecter
8. La conduite et l'organisation
9. Essais et mesure des gains
10. La qualité comme contrainte
11. Les erreurs fréquentes et comment les éviter
12. Check-lists (quotidienne, hebdomadaire, mensuelle, avant tout changement)
13. Repères chiffrés

---

## 1. À qui s'adresse ce guide et comment s'en servir

Ce guide s'adresse à ceux qui conduisent, règlent ou font évoluer une ligne de briqueterie : responsable d'usine, chef de four, chef de séchoir, électricien-automaticien, responsable qualité, opérateurs de poste. Il ne remplace ni le projet de régulation (qui dit **quoi** programmer) ni les recettes de conduite (qui disent **à quelle valeur** régler) : il dit **comment travailler** pour que les économies soient réelles, durables et sans dégradation de la qualité.

Chaque section se termine par des règles numérotées. Les check-lists de la section 12 sont faites pour être affichées en salle de contrôle.

---

## 2. Les dix principes directeurs

1. **Ce qui n'est pas mesuré n'est pas géré.** Un compteur faux ou absent vaut une décision prise au hasard. La première dépense utile est toujours un capteur ou un compteur fiable.
2. **La chaleur gratuite avant la chaleur achetée.** Dans une briqueterie, le four rejette plus de chaleur que le séchoir n'en consomme. L'ordre des sources est : récupération du four, puis brûleur modulant, puis brûleurs d'appoint tout-ou-rien.
3. **La qualité est une contrainte, pas une variable.** On optimise l'énergie **à l'intérieur** des limites de qualité (humidité, températures, pression, courbe de refroidissement), jamais en les déplaçant.
4. **Le juste besoin, pas le maximum.** Un ventilateur, un brûleur, un compresseur réglés « au cas où » coûtent toute l'année. Leur consigne doit suivre la charge réelle (cadence, humidité, pression).
5. **La régularité est une économie.** Une poussée régulière, une cadence stable, un cycle de séchage constant consomment moins que la même production obtenue par à-coups, parce que chaque transitoire se paie en gaz de rattrapage.
6. **Un arrêt doit coûter zéro.** Pendant un arrêt de production, rien ne sèche et rien ne cuit : brûleurs d'appoint à l'arrêt, ventilateurs au minimum de sécurité, four en ralenti.
7. **L'automate décide, l'opérateur surveille.** Une consigne tenue à la main n'est jamais tenue la nuit, ni pendant les changements de poste, ni quand la récupération varie. Les boucles vivent dans l'automate, pas dans la supervision ni dans la tête d'une personne.
8. **Un changement à la fois, mesuré.** Toute modification (consigne, matériel, programme) se fait seule, pendant une durée connue, avec un avant et un après chiffrés dans la même unité.
9. **Raisonner en unités physiques, puis en dinars.** Nm³, kWh, thermies par tonne ou par wagon d'abord ; la conversion en dinars vient ensuite, avec le prix réel de chaque tranche horaire.
10. **Écrire ce qu'on fait.** Journal des interventions, valeurs de départ, raisons des changements : sans cela, aucune comparaison n'est possible et chaque équipe refait les essais de la précédente.

---

## 3. Mesurer avant de régler

### 3.1 Les mesures indispensables

| Poste | Mesures minimales | Pourquoi |
|---|---|---|
| Gaz | un compteur par consommateur (séchoir, four, chacun avec correction de pression et de température) et un totaliseur usine qui recoupe la somme | sans gaz par consommateur, aucun gain ne peut être attribué |
| Électricité | puissance active, réactive et courant par départ (préparation, fabrication, séchoir, four, compresseur) avec rapports de TC vérifiés | repérer les consommateurs à vide, les anomalies de mesure, le réactif |
| Séchoir | humidité et température de l'air aux points clés (entrée, avant recyclage, recyclage, extraction, cheminée), température de la chambre de mélange et de l'air soufflé, température d'arrivée de la récupération, pressions dans les canaux, cadence réelle de la chaîne | l'humidité est la variable de qualité, la température d'arrivée de la récupération est la variable d'économie |
| Four | températures par centrale, pression de zone, température de fumées, température de refroidissement, vitesse des ventilateurs, signaux de portes et de pousseur, temps de poussée, stock de wagons ; idéalement O₂ des fumées | la pression et la poussée pilotent le gaz ; l'O₂ révèle l'excès d'air |
| Ambiance | température et humidité extérieures | la récupération et le séchage dépendent de l'air aspiré |
| Produit | poids et dimensions en sortie mouleuse, séchoir et four ; humidité résiduelle en étuve ; porosité, retrait, casse | la qualité se mesure sur le produit, pas seulement sur l'air |

### 3.2 Les archives

- Une valeur par 10 s pour les mesures de régulation, par minute pour les consommations ; **sans trou** : une liaison supervision-automate qui décroche rend les essais inexploitables.
- Horloges des automates et de la supervision synchronisées (une dérive de 5 minutes fausse la lecture des événements).
- Export régulier des archives (CSV) vers un stockage hors du poste de supervision ; une archive qui ne garde que les 30 derniers wagons n'est pas une archive.

### 3.3 Les indicateurs

- **Gaz** : Nm³ par wagon et thermies par tonne, séparément pour le séchoir (tonne verte) et le four (tonne rouge), par poste et par jour.
- **Électricité** : kWh par tonne, par départ, avec la répartition par tranche tarifaire ; puissance maximale appelée sur 15 min comparée à la puissance souscrite ; cos φ.
- **Récupération** : température et débit de la gaine, heures de marche du brûleur d'appoint par 24 h (un brûleur d'appoint qui tourne 20 h sur 24 n'est pas un appoint).
- **Transitoires** : nombre et durée des arrêts, nombre de démarrages de brûleur par heure, amplitude des chutes de température à la poussée.

**Règles.** R3.1 Vérifier chaque compteur contre une référence (compteur du fournisseur, pince ampèremétrique) avant de s'en servir. R3.2 Un compteur qui affiche une valeur négative, nulle ou figée est à réparer avant toute analyse. R3.3 Publier les indicateurs chaque jour au même endroit, avec la même méthode de calcul.

---

## 4. Le séchoir

### 4.1 La récupération d'abord

- Le registre de la gaine de récupération est **motorisé et piloté**, ouvert au maximum compatible avec la pression du four ; les entrées d'air frais de la chambre de mélange sont **fermées** tant que la température de la chambre reste sous sa limite.
- La vitesse du ventilateur de récupération est montée **par paliers validés** avec le chef de four, chaque palier étant compensé par la contre-pression pour tenir la pression du four et contrôlé sur la courbe de refroidissement des produits.
- La gaine est **isolée** et ses joints étanches : une gaine qui perd 50-60 °C en surface chauffe le hall, pas les briques.
- Pendant les arrêts du four, la récupération s'effondre en une à deux heures : le séchoir doit le savoir (température d'arrivée mesurée) et anticiper.

### 4.2 L'humidité comme variable de qualité

- La grandeur réglée est **l'humidité de l'air à la fin de la zone de séchage** (ici « avant recyclage »), avec une consigne de travail (12,5 %) sous la limite (14 %) ; le dépassement déclenche une pré-alarme à 13,5 %.
- La consigne de température du brûleur se **calcule** à partir de cette humidité, de la cadence et de la température de récupération ; elle n'est pas choisie à la main.
- Le contrôle final se fait sur le **produit** (humidité résiduelle en étuve) : l'humidité de l'air n'est qu'un indicateur.

### 4.3 Température ou ventilation ?

- Un kWh de chaleur au gaz coûte moins qu'un kWh électrique ; souffler plus d'air oblige aussi à chauffer plus d'air frais. En régime établi, on tient l'humidité **par la température** du brûleur et on garde les ventilateurs **à leur base de cadence**.
- La ventilation sert aux **pointes** : quand l'humidité monte vite, les ventilateurs d'air chaud montent de quelques Hz en quelques dizaines de secondes, puis redescendent quand le brûleur a repris.
- L'extraction est réglée **au minimum qui tient l'humidité du recyclage** : chaque m³ extrait emporte de la chaleur à la cheminée. Un capteur à la cheminée permet de la régler au juste besoin.
- Les ventilateurs sur variateur obéissent à la **loi du cube** : −10 % de vitesse ≈ −27 % de puissance. Les bases de vitesse se fixent par essai à cadence connue, pas à la valeur maximale.

### 4.4 Les arrêts et les reprises

- Un standby **unique** pour tout le séchoir (même temporisation pour le brûleur et tous les ventilateurs), déclenché sur l'arrêt réel de la chaîne, pas sur celui de la mouleuse seulement.
- En standby : brûleurs d'appoint **arrêtés**, registre arrière **fermé**, ventilateurs au minimum compatible avec l'homogénéité (recyclage et extraction réglés sur l'humidité présente), chaleur de récupération maintenue.
- À la reprise : rampe de 10 minutes vers la production, brûleur limité (≤ 115 °C pendant 20 minutes) pour éviter le pic de température de la chambre de mélange.
- Les briques restent dans le séchoir pendant les arrêts : la chaîne ne s'arrête jamais sans raison, et les ventilateurs ne s'arrêtent jamais complètement.

### 4.5 Le brûleur d'appoint

- Le brûleur modulant a son propre régulateur et son calculateur de sécurité : l'automate lui envoie une **consigne** et une **autorisation**, il ne pilote pas la flamme.
- Mode **zéro gaz** : quand la récupération suffit (humidité sous la consigne et demande au plancher pendant 15 minutes), le brûleur s'arrête, avec un temps minimal d'arrêt et de marche pour ne pas cycler.
- Un brûleur qui **pompe** (température de la chambre oscillant de 100 °C avec une période de 8 à 10 minutes) est mal réglé : bande proportionnelle et intégrale du régulateur, ou charge minimale trop haute. On le règle avant d'ajouter des boucles par-dessus.
- Les brûleurs d'appoint tout-ou-rien restent en **dernier recours**, avec hystérésis et temps minimal ; leur part dans le gaz total se mesure par un essai dédié.

### 4.6 Les limites

- Deux limites d'équipement passent avant tout : température de l'air soufflé (≤ 145 °C) et température de la chambre de mélange (≤ 250 °C). Elles sont tenues par des **limiteurs** qui réduisent la consigne, puis par un **arrêt critique** temporisé, et surveillées par des alarmes à trois niveaux.
- Le registre arrière du brûleur n'est **jamais fermé sous son minimum** quand la flamme est présente (air de dilution), et **fermé** quand le brûleur est éteint (air froid).

**Règles.** R4.1 Récupération maximale avant tout gaz. R4.2 Consigne du brûleur calculée, jamais fixée à la main en production. R4.3 Brûleur arrêté pendant le standby. R4.4 Température avant ventilation en régime établi, ventilation pour les pointes. R4.5 Extraction au minimum qui tient l'humidité. R4.6 Un brûleur d'appoint qui dépasse 12 h de marche par jour est un signal d'alarme, pas une normalité.

---

## 5. Le four

### 5.1 La poussée régulière

- Le temps de poussée est la **cadence** du four ; il se calcule à partir de la production prévue et du stock de wagons (détecteurs), avec des variations limitées (≤ 1 min par heure). Il n'est pas changé à la main à chaque poste.
- Chaque poussée fait chuter les centrales de préchauffage (ici −30 à −38 °C) ; le four passe ensuite 5 à 9 minutes à rattraper. Trois leviers : **geler l'intégrale** des PID pendant la poussée, **réduire l'air de combustion** quand le gaz est au minimum (sinon de l'air froid entre pour rien), appliquer un **supplément décroissant** après la poussée plutôt que de laisser le PID sur-réagir.
- Les portes s'ouvrent le moins longtemps possible ; la porte d'entrée (surpression) et la porte de sortie (dépression) ont chacune leur anticipation sur la contre-pression et le tirage, déclenchée par les fins de course.

### 5.2 La pression

- Une pression de zone stable (ici 0,6 mbar ± 0,2) est la condition d'une cuisson homogène et d'une récupération propre : en dépression, le four aspire de l'air froid ; en surpression, il refoule des fumées.
- La contre-pression tient la pression (PI rapide, zone morte, intégrale gelée portes ouvertes) ; le tirage ne fait qu'un recentrage lent de la contre-pression au milieu de sa plage. Deux actionneurs rapides sur la même mesure se battent.
- Chaque ventilateur garde une **réserve** de 5 à 10 % vers le haut ; un ventilateur à sa borne ne régule plus.

### 5.3 L'air de combustion

- L'excès d'air est le gaspillage invisible du four : il chauffe de l'azote qui part à la cheminée. Il se mesure par l'**O₂ des fumées** (cible 3 à 6 % en préchauffage, à fixer avec le constructeur) et se corrige par le rapport air/gaz de chaque centrale.
- Avant tout investissement (variateurs, régulateurs de rapport), un essai manuel de réduction d'air pendant quelques poussées dit si la chute de température diminue.
- Les ventilateurs d'air de combustion conservés après la réduction du nombre de centrales sont à recenser : un ventilateur qui souffle pour une centrale arrêtée consomme pour rien.

### 5.4 La récupération vers le séchoir

- La récupération prélève de l'air dans la zone de refroidissement ; la contre-pression doit compenser le prélèvement. Le couplage se mesure (variation de contre-pression nécessaire pour 2 Hz de récupération) et devient une anticipation.
- Le four reste **maître** : un palier de récupération n'est franchi qu'après validation de la courbe de refroidissement, de la pression et de la qualité, et jamais plus d'un palier par semaine.
- Blocages automatiques : température de départ de gaine trop haute, refroidissement trop bas, contre-pression au maximum ou arrêtée, pression hors plage, défaut de ventilateur. Dans ces cas la récupération revient à son minimum, jamais à zéro (le séchoir ne doit pas être privé).

### 5.5 Les recettes et le ralenti

- Les consignes de zone dépendent de la cadence : une poussée lente demande moins de préchauffage. Des recettes par plage de temps de poussée, validées en qualité, évitent de cuire « comme à pleine cadence » pendant les arrêts.
- Au-delà de 30 minutes sans poussée, le four passe en ralenti automatique (consignes abaissées, contre-pression en standby, air de combustion au minimum), puis revient en rampe à la poussée suivante.

**Règles.** R5.1 Poussée régulière, calculée, rarement modifiée. R5.2 Pression stable avant tout. R5.3 Mesurer l'O₂ avant de régler l'air. R5.4 Récupération par paliers validés, four maître. R5.5 Ralenti automatique au-delà de 30 minutes sans poussée.

---

## 6. L'électricité

### 6.1 Les ventilateurs

- Tout ventilateur dont la charge varie est sur **variateur**, avec une consigne qui suit la charge (cadence, humidité, pression) : la loi du cube rend chaque Hz évité très rentable (ici 141 kW à 50 Hz pour le recyclage, soit ≈ 5 kW par Hz à 40 Hz).
- Les bases de vitesse se fixent par essai, en vérifiant que la qualité ne bouge pas ; les rampes sont lentes (0,1 Hz/s) pour éviter les pics de courant et les à-coups de pression.
- Les ventilateurs sans variateur (brassage, air de combustion, récupération du four vers la gaine) sont examinés un par un : utile ? à quelle vitesse ? combien d'heures ?

### 6.2 Les moteurs à vide

- Une ligne de fabrication à l'arrêt qui consomme 50 à 80 kW et 300 à 500 kVAR est un gaspillage pur. Tout moteur dont l'arrêt ne crée pas de risque procédé est **arrêté réellement** au-delà de 3 minutes d'arrêt de la ligne (convoyeurs, pompes, cylindres), par l'automate.
- Les démarrages fréquents (pics > 260 A sur des dégrossisseurs ou des broyeurs) usent les moteurs et appellent de la puissance : on vérifie les protections et on lisse les cycles.

### 6.3 Le compresseur

- Un compresseur qui consomme la même puissance usine arrêtée et usine en marche a des **fuites** : recherche aux ultrasons, fabrication arrêtée, avant toute autre action (≈ 20 000 DT/an par 10 kW de fuites).
- Ensuite : pression de consigne au besoin le plus exigeant + 0,5 bar, marche à vide réduite, variateur sur le compresseur d'appoint, compresseur de base en charge/décharge.
- Chaque bar de trop coûte 6 à 8 % d'énergie.

### 6.4 Le réactif et la tarification

- Cos φ ≥ 0,95 en marche ; régulateur de batterie réglé pour éviter la surcompensation aux arrêts (PF > 1 signale des gradins restés enclenchés) ; compensation locale sur les départs à cos φ 0,2-0,5 (préparation, fabrication à vide).
- Les variateurs à thyristors génèrent des harmoniques : selfs anti-harmoniques et contrôle du THD avant d'ajouter de la compensation.
- Connaître sa tarification : prix par tranche (jour, pointe, nuit), prime de puissance, dépassement. Placer ce qui peut l'être en heures creuses, lisser la pointe sur 15 minutes, et ne jamais laisser la puissance maximale appelée dépasser la puissance souscrite d'un kW (le dépassement se facture).

**Règles.** R6.1 Variateur et consigne de charge sur tout ventilateur variable. R6.2 Zéro moteur en marche à vide au-delà de 3 minutes. R6.3 Fuites d'air avant variateur. R6.4 Cos φ ≥ 0,95 et surcompensation interdite. R6.5 Puissance appelée ≤ puissance souscrite, toujours.

---

## 7. L'automatisation : ce qu'une bonne régulation doit respecter

1. **Toutes les boucles dans l'automate**, jamais dans des scripts de supervision ; la supervision affiche, archive et permet de modifier les **paramètres**, pas la logique.
2. **Observation avant automatique** : chaque bloc tourne d'abord en mode observation (sorties calculées et archivées, commande existante conservée) pendant au moins 7 jours ; on compare ce qu'il aurait fait à ce qui a été fait.
3. **Reprise sans à-coup** : au passage en automatique, la sortie part de la valeur réelle ; les intégrales sont initialisées pour cela.
4. **Anti-emballement** : les intégrales n'intègrent pas vers une butée, et sont gelées quand la consigne est limitée en aval ou pendant un transitoire connu (poussée, porte, reprise).
5. **Bornes et rampes** sur toutes les sorties : fréquences entre un minimum de sécurité et un maximum validé ; montée limitée, descente rapide quand il s'agit de protéger.
6. **Validité des mesures** : hors échelle, saut brutal, valeur figée depuis 10 minutes ; une mesure invalide fait passer la boucle en repli (dernière valeur ou consigne de sécurité) avec alarme, jamais en action sur une fausse valeur.
7. **Limiteurs avant régulateurs** : les limites d'équipement (températures, pressions) sont des limiteurs qui réduisent la consigne, indépendants des boucles d'économie ; puis un arrêt critique temporisé.
8. **Alarmes à trois niveaux** (pré-alarme, alarme, critique) sur chaque limite, et des alarmes de **cohérence** : brûleur sans flamme en production, brûleur en marche en standby, récupération au maximum et chambre froide, trop de démarrages par heure.
9. **Un seul lieu de paramètres** (un DB par bloc), avec les valeurs de départ, les plages admises et la date du dernier changement.
10. **Les sécurités de flamme, de pression de gaz et des coffrets restent dans leurs organes** : l'automate donne des consignes et des autorisations, il ne remplace pas une chaîne de sécurité.
11. **Modes explicites** : production, attente, standby, reprise, repli ; chaque mode fixe ce que font les brûleurs et les ventilateurs, et les transitions sont temporisées.
12. **Un signal de cadence fiable** : la cadence réelle (ici l'avance de la chaîne des balancelles, comptée par capteurs) remplace les estimations (débit de la mouleuse, cadence du four).

---

## 8. La conduite et l'organisation

- **Règles de l'exploitant écrites** et connues de tous : limites de température, d'humidité, de pression ; ce qui ne se change jamais sans validation ; qui valide quoi.
- **Une consigne = une validation = une trace** : tout changement de consigne, de mode (AUTO/MANU) ou de recette est noté avec l'heure, l'auteur et la raison. Un passage en MANU est temporaire et a une date de retour en AUTO.
- **Le mode MANU n'est pas un mode de conduite** : il sert aux essais et aux dépannages. Un équipement qui tourne en MANU depuis plus de 24 h fait l'objet d'une alarme de gestion.
- **Revue énergétique hebdomadaire** (30 minutes) : indicateurs de la semaine, alarmes, arrêts, interventions manuelles, essais en cours, décision du palier suivant.
- **Formation** : chaque opérateur sait lire les indicateurs du poste, connaît les limites et sait ce qu'il doit faire (et ne pas faire) en cas d'alarme.
- **Les arrêts non programmés** (ici ≈ 5 h/j) sont la première source de surconsommation ; leur réduction (maintenance, approvisionnement, changements de filière planifiés) vaut souvent plus que toute régulation.
- **La production au maximum** sur la mouleuse et le séchoir n'est pas en contradiction avec l'économie : la ligne consomme moins par tonne à pleine charge ; c'est la régularité, pas la lenteur, qui économise.

---

## 9. Essais et mesure des gains

1. **État de référence** : deux semaines sans changement, indicateurs calculés, interventions manuelles notées.
2. **Un changement à la fois**, à cadence comparable, sur une durée qui couvre plusieurs cycles (séchoir : plusieurs tours de chaîne ; four : plusieurs dizaines de poussées) et les trois postes.
3. **Mesurer la même chose avant et après**, dans la même unité (Nm³/wagon, kWh/wagon), avec les mêmes compteurs ; corriger de la production et de la température extérieure si elles ont changé.
4. **Un essai a un mode opératoire écrit** (quoi, combien de temps, quelles mesures, quelle grandeur il fixe) et un résultat écrit, même négatif.
5. **Chiffrer prudemment** : fourchette basse et haute, hypothèses explicites (heures de marche, prix), et ne compter un gain qu'une fois (le gaz économisé par la récupération et par l'excès d'air peut se recouper).
6. **Valider la qualité à chaque palier** : contrôle labo sur quelques wagons avant de franchir le suivant.
7. **Revenir en arrière** sans discussion si la qualité bouge ; l'essai est alors un résultat, pas un échec.

---

## 10. La qualité comme contrainte

- Fixer avec les responsables de production les **bandes** : humidité de l'air en fin de séchage, humidité résiduelle du produit, températures de zone (± 10 °C), température de refroidissement, pression du four, porosité, retrait, poids, casse.
- Les bandes sont dans l'automate sous forme de limiteurs et d'alarmes ; elles ne se modifient que par le responsable qualité.
- Le laboratoire prélève à chaque palier et à chaque changement de recette ; ses résultats sont rapprochés des indicateurs énergétiques du même jour.
- Un gain énergétique obtenu avec une dérive de qualité n'est pas un gain : casse, incuit, surcuit et retours clients coûtent plus que le gaz.

---

## 11. Les erreurs fréquentes et comment les éviter

| Erreur observée | Conséquence | Parade |
|---|---|---|
| Brûleur d'appoint en MANU à consigne fixe, pendant des jours | il chauffe même quand la récupération suffit ; 20 à 23 h de marche par jour | mode AUTO avec consigne calculée ; alarme « MANU > 24 h » |
| Brûleur en marche pendant le standby | gaz brûlé pour un séchoir qui ne sèche pas | standby unique qui coupe le brûleur ; alarme « flamme en standby » |
| Registre d'air du brûleur fermé à la main pour « garder la chaleur » | chambre de mélange à 260-310 °C, pompage, limite dépassée | registre motorisé avec minimum garanti flamme présente |
| Régulation d'humidité par consigne tout-ou-peu (110/120 °C) | oscillation, séchage tantôt excessif (8 %) tantôt insuffisant (> 14 %) | PI continu sur l'humidité avec anticipation |
| Ventilateurs réglés au maximum « pour être tranquille » | électricité en cube, air frais à chauffer | bases par cadence, trims bornés |
| Consignes différentes sur plusieurs pages de supervision | personne ne sait laquelle agit | une page de paramètres, une logique dans l'automate |
| PID activé sur une consigne hors plage (8 % avec butée 46 Hz) | ventilateur en butée permanente | plages admises dans le DB, vérification avant activation |
| Compteur de gaz négatif ou figé utilisé dans les rapports | ratios faux, décisions fausses | contrôle des compteurs, alarme sur valeur aberrante |
| Rapport de TC faux sur un départ électrique | consommateur sous-estimé d'un facteur 3 | recoupement I mesuré / I calculé à la mise en service |
| Archives avec trous, horloges désynchronisées | essais inexploitables | liaison fiable, synchronisation, export régulier |
| Temps de poussée changé à chaque poste | chutes et rattrapages, cuisson irrégulière | poussée calculée, variations limitées |
| Air de combustion plein pendant la poussée | air froid dans le four, chute de 30-38 °C | air réduit avec le gaz, intégrale gelée |
| Ventilateur à sa borne haute (récupération à 45 Hz sur 40-45) | la boucle ne peut que descendre | réserve de 5-10 %, plage élargie après validation |
| Compresseur à 70 kW usine arrêtée | fuites | recherche de fuites avant tout achat |
| Gains annoncés sans état de référence | personne ne peut les prouver | deux semaines de référence, indicateurs par wagon |

---

## 12. Check-lists

### 12.1 Chaque poste (opérateur)

- [ ] Brûleur d'appoint : mode AUTO ? heures de marche du poste cohérentes avec la récupération disponible ?
- [ ] Humidité en fin de séchage dans sa bande ; aucune alarme active non traitée.
- [ ] Températures limites (air soufflé, chambre de mélange) sous leurs pré-alarmes.
- [ ] Pression du four dans sa bande ; poussée au temps calculé ; portes fermées hors poussée.
- [ ] Ventilateurs : aucun en MANU sans raison notée ; aucun à sa borne.
- [ ] Compteurs gaz et électricité : valeurs plausibles (ni nulles, ni négatives, ni figées).
- [ ] Interventions manuelles du poste notées (heure, auteur, raison, retour prévu).

### 12.2 Chaque semaine (responsable énergie)

- [ ] Nm³/wagon et kWh/wagon de la semaine, séchoir et four, comparés à la référence et à la semaine précédente.
- [ ] Heures de marche du brûleur d'appoint par jour ; heures de MANU par équipement.
- [ ] Nombre et durée des arrêts ; causes ; actions.
- [ ] Alarmes critiques de la semaine et leur traitement.
- [ ] Essai en cours : avancement, résultat, décision (palier suivant ou retour).
- [ ] Puissance maximale appelée sur 15 min vs souscrite ; cos φ moyen.
- [ ] Contrôles labo de la semaine rapprochés des indicateurs.

### 12.3 Chaque mois

- [ ] Factures gaz et électricité rapprochées des compteurs internes (écart < 2 %).
- [ ] Ratios mensuels (th/t verte, th/t rouge, kWh/t) et tendance sur 12 mois.
- [ ] Revue des paramètres des blocs (valeurs modifiées, par qui, pourquoi).
- [ ] État des capteurs (étalonnage, encrassement, redondance) et des archives (trous, exports).
- [ ] Mise à jour du plan d'action et des gains mesurés.

### 12.4 Avant tout changement (consigne, matériel, programme)

- [ ] État de référence disponible et daté.
- [ ] Mode opératoire écrit : quoi, durée, mesures, critère de succès, critère de retour arrière.
- [ ] Validation du responsable concerné (four, séchoir, qualité).
- [ ] Un seul changement à la fois.
- [ ] Qui surveille, quand, et comment on revient en arrière.

---

## 13. Repères chiffrés

| Grandeur | Repère | Source |
|---|---|---|
| Ratio thermique global d'une briqueterie à four tunnel | référence 350 th/t ; moyenne mondiale 250 ; usine 2015 : 382 ; septembre 2026 : ≈ 473 (160 séchoir + 313 four) | audit 2016, rapports 2026 |
| Ratio électrique | référence 35 kWh/t ; usine 2015 : 35,6 ; 2026 : ≈ 45 | audit 2016, rapports 2026 |
| Part de la chaleur du séchoir pouvant venir du four | 60 à 100 % selon la saison et la cadence (zéro gaz atteint en été 2021) | audit 2016, mémoire |
| Coût d'un kWh de chaleur au gaz / d'un kWh électrique | ≈ 61 millimes / 222 à 377 millimes selon la tranche | tarifs STEG 2026 |
| Puissance d'un ventilateur sur variateur | proportionnelle au cube de la vitesse : −10 % de vitesse ≈ −27 % de puissance | loi des ventilateurs |
| Consigne du brûleur du séchoir | +1 °C ≈ 5 à 8 Nm³/h ≈ 4 à 6 DT/h ; −0,2 point d'humidité en 3-4 min | V1 §3 |
| Air chaud du séchoir | +1 Hz (deux ventilateurs) ≈ 4,7 kW ≈ 1,3 DT/h plus l'air frais à chauffer | V1 §3 |
| Extraction du séchoir | +1 Hz (trois ventilateurs) ≈ 3,8 kW + ≈ 40 kW de chaleur rejetée | V1 §3 |
| Récupération | 1 °C de température d'arrivée ≈ 9 kW ; un palier de 75 tr/min ≈ 160-180 kW | V1 §2 |
| Chute de température à la poussée | −30 à −38 °C sur la première centrale, retour en 5 à 9 min pour une période de 11-12 min | vidéo 14/10 |
| Pression du four aux portes | −1,1 mbar (sortie), +2,4 mbar (entrée) pour une consigne de 0,6 | courbes 05/10 |
| Fuites d'air comprimé | ≈ 20 000 DT/an par 10 kW de fuites | archive 02/10 |
| Fabrication à vide | 50-80 kW et 330-480 kVAR ; jusqu'à 35 000 DT/an si coupée aux arrêts | archive 02/10 |
| Arrêts non programmés | ≈ 5 h/j, première cause de surconsommation | mémoire |

---

*Briqueterie Jemmel — Guide des bonnes pratiques de gestion énergétique, édition 1 du 23/10/2026. Document vivant : il se met à jour après chaque essai et chaque palier, avec les valeurs mesurées sur l'installation. Toute modification est validée par la direction technique.*
