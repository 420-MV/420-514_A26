# Dictionnaire des données

Description des colonnes des fichiers de `data/raw/`. Ces fichiers ne se modifient jamais.

| Fichier | Contenu | Lignes = |
|---|---|---|
| [alphabet_stock_data.csv](#alphabet_stock_datacsv) | Cours boursier d'Alphabet (Google) | une journée de bourse |
| [blood.csv](#bloodcsv) | Pression artérielle avant/après traitement | un patient |
| [HousePrices.csv](#housepricescsv) | Ventes de maisons (région de Seattle, WA) | une vente |
| [music.csv](#musiccsv) | Genre musical préféré selon l'âge et le sexe | une personne |
| [property.csv](#propertycsv) | Propriétés avec valeurs manquantes volontaires | une propriété |
| [Social_Network_Ads.csv](#social_network_adscsv) | Réaction à une publicité sur un réseau social | un utilisateur |
| [titanic.csv](#titaniccsv) | Passagers du Titanic (version complète) | un passager |
| [titanic_0.csv](#titanic_0csv) | Passagers du Titanic (version simplifiée) | un passager |
| [world-population-2020.json](#world-population-2020json) | Démographie des pays en 2020 | un pays |

---

## alphabet_stock_data.csv

| Colonne | Type | Description |
|---|---|---|
| `Date` | date (AAAA-MM-JJ) | Jour de bourse |
| `Open` | numérique | Prix à l'ouverture (USD) |
| `High` | numérique | Prix le plus haut de la journée (USD) |
| `Low` | numérique | Prix le plus bas de la journée (USD) |
| `Close` | numérique | Prix à la fermeture (USD) |
| `Adj Close` | numérique | Prix de fermeture ajusté (dividendes et fractionnements d'actions) |
| `Volume` | entier | Nombre d'actions échangées |

## blood.csv

| Colonne | Type | Description |
|---|---|---|
| `patient` | entier | Identifiant du patient |
| `sex` | catégorielle | Sexe (`Male`, `Female`) |
| `agegrp` | catégorielle ordinale | Groupe d'âge (ex. `30-45`) |
| `bp_before` | entier | Pression systolique avant le traitement (mm Hg) |
| `bp_after` | entier | Pression systolique après le traitement (mm Hg) |

## HousePrices.csv

| Colonne | Type | Description |
|---|---|---|
| `date` | date et heure | Date de la vente |
| `price` | numérique | Prix de vente (USD) |
| `bedrooms` | numérique | Nombre de chambres |
| `bathrooms` | numérique | Nombre de salles de bain (les demi-valeurs comptent les salles d'eau) |
| `sqft_living` | entier | Surface habitable (pi²) |
| `sqft_lot` | entier | Surface du terrain (pi²) |
| `floors` | numérique | Nombre d'étages |
| `waterfront` | binaire (0/1) | 1 = propriété en bord de l'eau |
| `view` | ordinale (0 à 4) | Qualité de la vue |
| `condition` | ordinale (1 à 5) | État général de la maison |
| `sqft_above` | entier | Surface hors sous-sol (pi²) |
| `sqft_basement` | entier | Surface du sous-sol (pi²), 0 = pas de sous-sol |
| `yr_built` | entier | Année de construction |
| `yr_renovated` | entier | Année de rénovation, 0 = jamais rénovée |
| `street` | texte | Adresse (rue) |
| `city` | catégorielle | Ville |
| `statezip` | texte | État et code postal (ex. `WA 98133`) |
| `country` | catégorielle | Pays |

## music.csv

| Colonne | Type | Description |
|---|---|---|
| `age` | entier | Âge de la personne |
| `gender` | binaire (0/1) | Sexe encodé numériquement |
| `genre` | catégorielle | Genre musical préféré (ex. `HipHop`) |

## property.csv

Jeu volontairement « sale » : valeurs manquantes sous plusieurs formes (cellule vide, `--`, `n/a`, etc.).

| Colonne | Type | Description |
|---|---|---|
| `PID` | entier | Identifiant de la propriété |
| `ST_NUM` | entier | Numéro civique |
| `ST_NAME` | texte | Nom de la rue |
| `OWN_OCCUPIED` | binaire (`Y`/`N`) | Occupée par son propriétaire |
| `NUM_BEDROOMS` | numérique | Nombre de chambres |
| `NUM_BATH` | numérique | Nombre de salles de bain |
| `SQ_FT` | numérique | Superficie (pi²) |

## Social_Network_Ads.csv

| Colonne | Type | Description |
|---|---|---|
| `User ID` | entier | Identifiant de l'utilisateur |
| `Gender` | catégorielle | Sexe (`Male`, `Female`) |
| `Age` | entier | Âge |
| `EstimatedSalary` | entier | Salaire annuel estimé (USD) |
| `Purchased` | binaire (0/1) | 1 = a acheté le produit après la publicité (variable cible) |

## titanic.csv

| Colonne | Type | Description |
|---|---|---|
| `PassengerId` | entier | Identifiant unique de chaque passager. |
| `Survived` | binaire (0/1) | 1 = a (oui) survécu (variable cible) et 0 = non |
| `Pclass` | ordinale (1, 2, 3) | Classe du billet (1 = première) |
| `Name` | texte | Nom (format `Nom, Titre. Prénoms`) |
| `Sex` | catégorielle | Sexe (`male`, `female`) |
| `Age` | numérique | Âge en années (valeurs manquantes) |
| `SibSp` | entier | Nombre de frères, sœurs ou conjoints à bord |
| `Parch` | entier | Nombre de parents ou enfants à bord |
| `Ticket` | texte | Numéro du billet |
| `Fare` | numérique | Prix payé pour le billet |
| `Cabin` | texte | Numéro de cabine (très souvent manquant) |
| `Embarked` | catégorielle | Port d'embarquement (`C` = Cherbourg, `Q` = Queenstown, `S` = Southampton) |


## titanic_0.csv

Version simplifiée de `titanic.csv` : pas d'identifiant, de billet, de cabine ni de port, et le nom est écrit `Titre. Prénoms Nom`.

| Colonne | Type | Description |
|---|---|---|
| `Survived` | binaire (0/1) | 1 = a survécu |
| `Pclass` | ordinale (1, 2, 3) | Classe du billet |
| `Name` | texte | Nom complet |
| `Sex` | catégorielle | Sexe (`male`, `female`) |
| `Age` | numérique | Âge en années |
| `Siblings/Spouses Aboard` | entier | Équivalent de `SibSp` |
| `Parents/Children Aboard` | entier | Équivalent de `Parch` |
| `Fare` | numérique | Prix payé pour le billet |

## world-population-2020.json

Tableau JSON d'objets. **Toutes les valeurs sont des chaînes** (virgules de milliers, `%`, etc.) : une conversion de type est nécessaire avant tout calcul.

| Clé | Description |
|---|---|
| `position` | Rang du pays selon la population |
| `country` | Nom du pays |
| `population` | Population en 2020 |
| `yearly_change` | Variation annuelle (%) |
| `net_change` | Variation nette annuelle (nombre d'habitants) |
| `density_per_square_km` | Densité (hab./km²) |
| `land_are_in_square_km` | Superficie terrestre (km²) ; la clé est écrite ainsi dans le fichier |
| `migrants_net` | Solde migratoire net |
| `fertility_rate` | Indice de fécondité (enfants par femme) |
| `median_age` | Âge médian |
| `urban_population` | Part de la population urbaine (%) |
| `world_share` | Part de la population mondiale (%) |
