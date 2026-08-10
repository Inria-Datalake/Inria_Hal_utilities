# Constructeur et visualisation des données de l'API HAL utilisant les facettes avec pivots
Mode d’emploi

Documentation de référence : https://api.archives-ouvertes.fr/docs/search/?#facet (section « Facettes avec pivots)
Liste des champs pour l’API de HAL : https://api.archives-ouvertes.fr/docs/search/?schema=fields#fields

## Qu’est-ce qu’une interrogation à facettes avec pivots ?

L’interrogation avec facettes à pivot permet de combiner 2 champs de HAL dans la réponse.
Par exemple : combien d’articles et de communications dans un congrès sont déposés dans le portail « Hal » chaque année.
L’API comporte 2 parties : 
1. les critères de recherche (sections q= et fq=) « portail Hal » (instance_s :hal), « année de publication de 2023 à 2026 » (publicationDateY_ :[2023 TO 2026]) et on restreint au types de documents « articles ou communications dans un congrès » (docType_s :(ART OR COMM))
2. les champs à combiner pour afficher le résultat : « année de publication » (publicationDateY_i ) et « type de document » (docType_s).
On obtient un tableau qui montre, pour chaque type de document le nombre de dépôts présents dans le portail hal chaque année entre 2023 et 2026.
<img width="719" height="207" alt="image" src="https://github.com/user-attachments/assets/2514b396-9f49-423a-9f3f-a80f7e9b7ba4" />

## Comment utiliser le formulaire ?

Deux méthodes possibles : copier une API déjà construite (A) ou la construire à l'aide du formulaire (B).

### A. Saisir l’url de l’API complète
Coller une API déjà construite, par exemple : 
Par exemple : https://api.archives-ouvertes.fr/search/?q=instance_s%3Ahal&fq=publicationDateY_i%3A%5B2023+TO+2026%5D&fq=docType_s%3A%28ART+OR+COMM%29&rows=0&indent=true&facet=true&facet.pivot=publicationDateY_i%2CdocType_s&facet.sort=publicationDateY_i&wt=json
<img width="1802" height="120" alt="image" src="https://github.com/user-attachments/assets/4e2c43d5-7f8e-4afe-b99c-dad6c5dad57f" />

Cliquer sur "Charger les données"

### B. Construire la requête et définir les pivots
1. Définir les critères de recherche (4 maximum)
- Un Critère principal et trois critères optionnels (filtres) sont proposés avec un liste par défaut pour trois sur quatre.
- Le quatrième critère optionnel « Champ personnalisé » est un champ de votre choix dans la liste proposée par l’API (https://api.archives-ouvertes.fr/docs/search/?schema=fields#fields). S’il est le seul critère renseigné, il sera le critère principal de l’API q=)

Exemple simple :

<img width="765" height="263" alt="image" src="https://github.com/user-attachments/assets/58a32cf7-bf65-42f8-beb6-bf76f79c1562" />

Note : pour une requête plus élaborée (avec exclusions, par exemple), il est possible de recopier l'URL générée à partir d'une requête "simple", de la modifier de son côter et la copier dans la premère boîte de saisie en suivant la méthode A.

2. Définir les pivots (champs à utiliser pour l’affichage du tableau)
-	Lignes : indiquer le nom du champ Hal pour les lignes
-	Colonnes : indiquer le nom du champ pour les colonnes
 
<img width="936" height="126" alt="image" src="https://github.com/user-attachments/assets/50c9eaa0-6f98-46d3-aa27-3eef25b2ceeb" />

3.	Cliquer sur « Construire l’API et charger les données

<img width="323" height="55" alt="image" src="https://github.com/user-attachments/assets/720b257f-9924-4128-87a8-7cdacb0eca6e" />

Au dessous s’affichent :
- l’API complète si on a défini chaque champ
- le rappel des champs choisis pour les lignes et les colonnes du tableau
- des boutons pour calculer les totaux pour toutes les lignes ou seulement quelques lignes du tableau et/ou faire un export CSV.
- Le tableau de résultat

<img width="1804" height="634" alt="image" src="https://github.com/user-attachments/assets/d5908818-a1d6-43f9-831c-84f362e8e325" />



