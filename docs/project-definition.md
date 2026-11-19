# Définition du projet

## 1. Titre du projet

Développement d’un outil cartographique d’aide à la recherche d’établissements et à la consultation des informations sur leur accessibilité en fauteuil roulant à Sherbrooke.

## 2. Contexte et besoin

Une personne en fauteuil roulant peut avoir besoin de connaître les conditions d’accès à un établissement avant de s’y rendre. Lorsque les informations sont absentes ou imprécises, il devient difficile de préparer sa visite.

Dans ce projet, je développerai un outil cartographique simple pour aider les utilisateurs à rechercher des établissements à Sherbrooke et à consulter les informations disponibles sur leur accessibilité. Je proposerai une carte, des filtres et une fiche d’information pour chaque établissement.

J’utiliserai OpenStreetMap comme source principale des données géographiques et des informations d’accessibilité. Je construirai le prototype pour qu’il puisse fonctionner uniquement avec ces données.

Je pourrai utiliser Kéroul comme source complémentaire pour documenter ou comparer les informations de certains établissements, si je trouve des fiches pertinentes et si leurs conditions d’utilisation le permettent. Je ne ferai pas dépendre la réalisation du prototype de l’accès aux données de Kéroul.

Mon objectif sera de faciliter la préparation d’une visite en présentant clairement les informations disponibles, leur source et leurs limites. Je ne présenterai pas mon outil comme une certification officielle et je ne garantirai pas les conditions réelles d’accès à un établissement.

## 3. Problématique

Comment puis-je développer un outil cartographique simple pour aider les personnes en fauteuil roulant à rechercher des établissements à Sherbrooke et à consulter les informations disponibles sur leur accessibilité afin de mieux préparer leurs visites ?

## 4. Objectifs

- Objectif général :

  Je développerai un prototype cartographique permettant de rechercher des établissements à Sherbrooke et de consulter leurs informations d’accessibilité en fauteuil roulant. J’indiquerai les sources utilisées et les limites des données.

- Objectifs spécifiques :

  - Je constituerai un jeu de données sur les établissements du secteur choisi à partir d’OpenStreetMap, puis j’organiserai les informations nécessaires au prototype.
  - Je créerai une interface permettant de rechercher les établissements par nom, de les filtrer et de consulter leurs informations sur une carte et dans une liste.
  - Je testerai le fonctionnement de l’outil et je vérifierai un sous-échantillon d’informations à l’aide de sources complémentaires ou d’observations, selon leur disponibilité.

## 5. Périmètre

- Territoire :

  Je travaillerai sur un secteur de Sherbrooke que je choisirai après avoir examiné les données disponibles. Pour cette première version, je ne chercherai pas à couvrir toute la ville.

- Période :

  J’utiliserai les données disponibles au moment de leur extraction. Je conserverai la date d’extraction et les dates de consultation des sources complémentaires. Je ne prévois pas de mise à jour en temps réel ni d’analyse historique.

- Éléments inclus :

  - Je travaillerai sur un échantillon de 20 établissements ouverts au public.
  - Je retiendrai deux catégories d’établissements après l’exploration initiale.
  - Je conserverai le nom, l’identifiant OSM, la localisation, le type d’établissement, l’adresse lorsqu’elle est disponible et les informations d’accessibilité.
  - J’inclurai des établissements avec ou sans attribut `wheelchair`, afin de rendre visibles les informations non renseignées.
  - Je créerai une seule interface Streamlit contenant une carte interactive Folium, une liste de résultats et une fiche d’information par établissement.
  - Je proposerai une recherche par nom et des filtres par catégorie d’établissement et par valeur d’accessibilité renseignée.
  - J’ajouterai des informations complémentaires lorsqu’elles seront disponibles et que leur utilisation sera autorisée.
  - Je vérifierai que les données OSM des 20 établissements sont correctement affichées dans l’application.
  - Je sélectionnerai 5 établissements pour une comparaison avec des sources complémentaires, si je trouve les informations nécessaires.
  - Je n’ajouterai pas de fonctionnalités supplémentaires à ce stade. Si les données ne me permettent pas de respecter ce périmètre, je discuterai d’un ajustement avec l’enseignant.

- Éléments exclus :

  - Je ne réaliserai pas de certification de l’accessibilité des établissements.
  - Je ne chercherai pas à couvrir tous les établissements de Sherbrooke.
  - Je ne calculerai pas d’itinéraires accessibles entre le domicile et les établissements.
  - Je ne réaliserai pas d’analyse détaillée des trottoirs, des pentes et de l’ensemble du parcours de déplacement.
  - Je ne déduirai pas l’accessibilité d’une entrée à partir du seul centre géométrique d’un bâtiment.
  - Je ne développerai pas d’application mobile native.
  - Je ne mettrai pas en place de mise à jour automatique en temps réel.
  - Je ne modifierai pas automatiquement les données d’OpenStreetMap.
  - Je ne collecterai pas de données personnelles sur les utilisateurs.

## 6. Résultats attendus

### Prototype et fonctionnalités

Je réaliserai un prototype dans lequel l’utilisateur pourra :

1. Consulter les établissements du secteur étudié sur une carte et dans une liste.
2. Rechercher un établissement par son nom.
3. Filtrer les résultats selon la catégorie d’établissement et les informations d’accessibilité renseignées.
4. Sélectionner un établissement pour consulter ses informations.
5. Repérer les informations absentes, les limitations signalées et les cas nécessitant une confirmation.

Dans la fiche de chaque établissement, j’afficherai les éléments suivants, lorsqu’ils seront disponibles :

- Le nom et le type d’établissement.
- L’adresse.
- La valeur de l’attribut `wheelchair` dans OpenStreetMap.
- Les renseignements complémentaires sur l’accès.
- La source de chaque information et la date d’extraction ou de consultation.
- Une mention indiquant si j’ai pu effectuer une vérification indépendante.
- Un avertissement en cas d’information absente, de divergence ou d’incertitude.

### Présentation des informations d’accessibilité

J’utiliserai des libellés qui précisent que les informations proviennent d’OpenStreetMap et qu’elles ne constituent pas une garantie donnée par mon application :

| Valeur de `wheelchair` | Texte affiché à l’utilisateur |
|---|---|
| `yes` | Accessible selon les données OSM |
| `limited` | Accessibilité limitée selon les données OSM |
| `no` | Indiqué comme non accessible dans OSM |
| Attribut absent | Information non renseignée dans OSM |
| `designated` | Autre valeur OSM : designated |

Pour toute autre valeur, j’afficherai « Autre valeur OSM : [valeur] » et je la conserverai séparément. Je ne la regrouperai pas automatiquement avec `yes`.

Je ne considérerai pas l’absence d’information comme une absence d’accessibilité. J’indiquerai les sources et les dates d’extraction ou de consultation dans les fiches.

J’accompagnerai la couleur des marqueurs d’un libellé textuel.

### Outils de développement envisagés

Je développerai le prototype en Python.

- J’utiliserai Streamlit pour créer l’interface : recherche, filtres, liste des résultats et affichage des informations.
- J’utiliserai Folium pour créer la carte interactive et les marqueurs.
- Je prévois d’utiliser le composant `streamlit-folium` pour intégrer la carte dans Streamlit. Je testerai cette intégration dans une première version simple.

Pour la première version, j’utiliserai un fichier de données préparé à l’avance. Je ne lancerai pas de requête en direct à OpenStreetMap à chaque utilisation de l’application.

### Livrables

À la fin du projet, je fournirai :

- Le code Python du prototype.
- Un jeu de données préparé pour l’application, dans le respect des conditions de réutilisation.
- La requête d’extraction OSM et la date d’extraction.
- Une carte interactive et une liste filtrable des établissements, intégrées dans la même interface.
- Un tableau des informations manquantes ou nécessitant une vérification.
- Un court guide d’utilisation.
- Un bilan des tests, des résultats et des limites.

Si je calcule des indicateurs, je préciserai qu’ils décrivent uniquement mon échantillon. Je ne les présenterai pas comme une mesure de l’accessibilité de tous les établissements de Sherbrooke.

### Méthode de validation

Je vérifierai mon travail selon trois volets.

1. Tests du traitement des données

   Je préparerai un petit jeu de données dont je connais les résultats attendus. Je l’utiliserai pour tester les valeurs `yes`, `limited`, `no`, les valeurs manquantes, les autres valeurs et les doublons.

   Je vérifierai notamment que mon programme ne transforme pas les informations manquantes en `no`, qu’il conserve les autres valeurs séparément et qu’il ne compte pas plusieurs fois le même établissement par erreur.

2. Tests des fonctionnalités

   Je préparerai des scénarios pour vérifier :

   - Que la recherche par nom retourne les établissements attendus.
   - Que les filtres fonctionnent seuls et en combinaison.
   - Que la carte et la liste présentent les mêmes établissements après filtrage.
   - Que chaque fiche correspond au bon établissement.
   - Que les sources et les informations manquantes sont affichées.
   - Que l’interface présente un message clair lorsqu’aucun résultat ne correspond aux critères.

3. Vérification des informations

   Je contrôlerai la bonne restitution des données OSM dans l’application pour les 20 établissements de l’échantillon. Je vérifierai le nom, l’identifiant OSM, la localisation et les informations affichées.

   Parmi ces établissements, j’en sélectionnerai 5 pour une comparaison avec des sources complémentaires, si je trouve des informations pertinentes. Avant toute comparaison, je confirmerai leur identité à partir du nom, de l’adresse et de la localisation.

   Si je peux comparer moins de 5 établissements, j’indiquerai le nombre effectivement vérifié et les raisons de cette limite.

   Lorsque cela sera possible, je comparerai certaines informations avec une fiche Kéroul, une information publiée par l’établissement, une confirmation auprès de celui-ci ou une observation sur place.

   Dans Kéroul, je consulterai le nom, l’adresse, la cote d’accessibilité et les renseignements disponibles sur l’entrée. Je n’utiliserai ces informations que si les conditions le permettent.

   Je comparerai uniquement les caractéristiques qui peuvent réellement l’être. Je conserverai les informations de chaque source séparément et je ne considérerai pas automatiquement une cote globale comme une information concernant seulement l’entrée.

   Je documenterai les divergences sans supposer automatiquement qu’une source est correcte et l’autre erronée.

   Si je ne peux pas effectuer de vérification indépendante, je préciserai que l’information provient d’OpenStreetMap et qu’elle n’a pas été vérifiée indépendamment. Cela n’empêchera pas le fonctionnement du prototype.

Si j’en ai la possibilité, je proposerai un essai à une personne concernée ou à un organisme local pour recueillir des commentaires sur l’utilité et la compréhension de l’interface. Je ne ferai pas dépendre la réalisation du prototype de cet essai.

## 7. Contraintes et questions ouvertes

### Contraintes

Je devrai tenir compte des contraintes suivantes :

- Mon temps est limité et je suis débutant en programmation.
- Je devrai limiter la zone étudiée et le nombre de fonctionnalités.
- Les informations d’accessibilité peuvent être incomplètes, imprécises ou anciennes.
- Je devrai distinguer les établissements, leurs entrées et les éléments de voirie.
- Je pourrai rencontrer des doublons et des difficultés pour retrouver le même établissement dans plusieurs sources.
- Je devrai tenir compte des différences entre les classifications d’accessibilité.
- Je devrai vérifier les conditions d’utilisation, d’attribution et de redistribution des données.
- Je ne pourrai pas garantir les conditions réelles d’accès au moment d’une visite.
- Je ne publierai pas dans mon dépôt GitHub les informations dont la redistribution n’est pas autorisée.

### Hypothèses à vérifier

Je vérifierai les hypothèses suivantes :

- Je peux trouver suffisamment d’établissements dans le secteur retenu pour constituer un prototype pertinent.
- Je peux créer une première base exploitable à partir des données d’OpenStreetMap.
- Je peux réaliser une interface limitée à une carte, une liste, des filtres et des fiches dans le temps disponible.
- Je peux éventuellement enrichir certaines fiches avec des sources complémentaires, sans en faire une condition du fonctionnement de l’outil.

Lors d’une exploration préliminaire, j’ai obtenu 161 éléments OSM : 99 nodes, 59 ways et 3 relations.

J’ai obtenu ce résultat avec une requête recherchant les éléments portant l’attribut `wheelchair` dans la zone de Sherbrooke. Je considère ce résultat comme provisoire et je conserverai la requête ainsi que la date d’extraction pour le documenter.

Je ne considérerai pas ces 161 éléments comme l’ensemble des établissements de Sherbrooke, ni comme 161 établissements distincts ou accessibles. J’examinerai les résultats pour distinguer les établissements, les entrées et les éléments de voirie.

Comme cette requête ne comprend pas les établissements sans attribut `wheelchair`, je réaliserai une extraction complémentaire pour les deux catégories retenues, sans imposer la présence de cet attribut. Je pourrai ainsi inclure des établissements dont l’information d’accessibilité n’est pas renseignée.

### Exemple concret dans OpenStreetMap

Dans les résultats de ma requête à Sherbrooke, j’ai repéré le commerce suivant :

- Nom : Dépanneur Denault
- Type d’objet OSM : node
- Identifiant OSM : 2377034296
- Catégorie : `shop=convenience`
- Adresse renseignée : 1688, Rue Denault
- Information d’accessibilité : `wheelchair=yes`
- Lien vers l’objet OSM : https://www.openstreetmap.org/node/2377034296
- Date de consultation : 18 novembre 2026

Cet exemple m’a permis de repérer une information d’accessibilité en fauteuil roulant dans les données OSM consultées pour un établissement à Sherbrooke.

Dans mon prototype, j’afficherai cette valeur avec le libellé « Accessible selon les données OSM ». Je ne la présenterai pas comme une certification ni comme une vérification indépendante des conditions réelles d’accès.

### Questions ouvertes

Je dois encore préciser les points suivants :

- Quel secteur de Sherbrooke et quelles catégories d’établissements vais-je retenir ?
- Quels critères vais-je utiliser pour identifier les établissements et traiter les doublons ?
- Combien d’établissements disposent d’informations utiles pour mon prototype ?
- Quelles informations complémentaires puis-je utiliser et publier ?
- L’intégration de Folium dans Streamlit me permettra-t-elle de réaliser les interactions prévues avec un niveau de complexité adapté à mon projet ?
- Quels libellés seront les plus clairs pour présenter les informations sans donner une garantie excessive ?
- Pourrai-je vérifier certains lieux ou obtenir un retour d’un organisme local ?

J’ajusterai le périmètre et les fonctionnalités avec l’enseignant après l’exploration initiale des données. Ma priorité sera de réaliser un prototype limité, fonctionnel et transparent sur les informations que je présenterai.
