# Collecte et interprétation de données

Jeux de données et carnets Jupyter du cours **Collecte et interprétation de données**
(Techniques de l'informatique, 3<sup>e</sup> année).

## Démarrage rapide

### Option 1 : Google Colab (aucune installation)

Cliquez sur le lien « Ouvrir dans Colab » de chaque carnet dans le tableau plus bas.
Modèle de lien à utiliser (remplacez les valeurs) :

```
https://colab.research.google.com/github/<UTILISATEUR>/<DEPOT>/blob/main/notebooks/<NOM-DU-CARNET>.ipynb
```

Dans Colab, les données se chargent directement depuis GitHub (voir la section [Charger les données](#charger-les-données)).

### Option 2 : En local

```bash
# 1. Cloner le dépôt
git clone https://github.com/<UTILISATEUR>/<DEPOT>.git
cd <DEPOT>

# 2. Créer un environnement virtuel
python -m venv .venv
source .venv/bin/activate        # Windows : .venv\Scripts\activate

# 3. Installer les dépendances
pip install -r requirements.txt

# 4. Lancer Jupyter
jupyter lab
```

**Prérequis** : Python 3.10 ou plus récent.

---

## Structure du dépôt

```
.
├── README.md
├── requirements.txt
├── notebooks/
│   ├── 01_intro_numpy.ipynb
│   ├── 02_intro_pandas.ipynb
│   ├── 03_profilage_des_donnees.ipynb
│   ├── 04_nettoyage_valeurs_manquantes_doublons.ipynb
│   ├── 05_valeurs_aberrantes.ipynb
│   ├── 06_transformation_types_encodage_normalisation.ipynb
│   ├── 07_restructuration_merge_groupby_pivot.ipynb
│   ├── 08_eda_univariee.ipynb
│   ├── 09_eda_bivariee_multivariee.ipynb
│   ├── 10_pieges_d_interpretation.ipynb
│   └── 11_atelier_guide.ipynb
├── data/
│   ├── raw/            # données brutes, jamais modifiées
│   ├── processed/      # données nettoyées produites par les carnets
│   ├── README.md       # expliquer les colonnes des datasets 
└── images/             # schémas utilisés dans les carnets
```

**Règle d'or** : les fichiers de `data/raw/` ne se modifient jamais. Tout le travail se fait sur une copie en mémoire, et les résultats vont dans `data/processed/`.



## Carnets Jupyter

| # | Carnet | Concepts abordés |
|---|---|---|
| 01 | `01_intro_python_numpy` | Introduction à la librairie numpy : `array` création des ndarray, manipulation des éléments, sélection, opération statistiques et mathématiques |
| 02 | `02_intro_python_pandas` | Intro à pandas : `read_csv`, sélection, filtrage, `DataFrame` et `Series` |
| 03 | `03_profilage_des_donnees` | `shape`, `info()`, `describe()`, `isna()`, types de données, dictionnaire de données |
| 04 | `04_nettoyage_valeurs_manquantes_doublons` | Causes des valeurs manquantes, suppression, imputation (moyenne, médiane, mode), indicateur de manque, doublons, casse et espaces, formats de dates |
| 05 | `03_valeurs_aberrantes` | Méthode IQR, z-score, « erreur de saisie ou cas réel ? » |
| 06 | `06_transformation_types_encodage_normalisation` | `astype`, `to_datetime`, variables dérivées, encodage one-hot et ordinal, normalisation min-max, standardisation | 
| 07 | `07_restructuration_merge_groupby_pivot` | Jointures (`inner`, `left`, `outer`), `groupby`, `pivot_table`, `melt`, tidy data |
| 08 | `08_eda_univariee` | Histogramme, boîte à moustaches, forme d'une distribution, moyenne vs médiane |
| 09 | `09_eda_bivariee_multivariee` | Nuage de points, corrélation, matrice de corrélation, graphiques par groupe |
| 10 | `10_pieges_d_interpretation` | Corrélation vs causalité, variable confondante, paradoxe de Simpson, axe tronqué, biais d'échantillonnage |
| 11 | `11_atelier_guide` | Projet intégrateur sur un jeu de données réel |



## Jeux de données


| Fichier | Description | Source | Utilisé dans |
|---|---|---|---|
| `data/raw/<requetes_311>.csv` | Requêtes 311 de la Ville de Montréal (extrait) | [Données ouvertes de Montréal](https://donnees.montreal.ca) | 01 à 09 |
| `data/raw/<collisions>.csv` | Collisions routières (extrait) | [Données ouvertes de Montréal](https://donnees.montreal.ca) | 05, 07, 09 |
| `data/raw/<bixi>.csv` | Déplacements BIXI (extrait) | [BIXI Montréal](https://bixi.com/fr/donnees-ouvertes) | 04, 05, 09 |
| `data/raw/<jeu_pedagogique_sale>.csv` | Jeu **fictif** avec défauts volontaires (manquants, doublons, casse, dates mixtes, aberrations) | Généré pour le cours | 02, 03 |

> Les noms de fichiers entre `< >` sont des **espaces réservés** : remplacez-les par vos fichiers réels.

### Licences et sources

- Chaque jeu de données conserve **la licence de sa source**. Vérifiez et indiquez la licence exacte de chaque fichier dans `data/README.md`, ainsi que la date de téléchargement.


### Données personnelles (Loi 25)

Les jeux de données du dépôt **ne doivent contenir aucun renseignement personnel**. Si vous ajoutez des données, retirez ou anonymisez toute information permettant d'identifier une personne. En cas de doute, ne publiez pas le fichier.

### Charger les données

**En local**

```python
import pandas as pd

df = pd.read_csv("../data/raw/<requetes_311>.csv")
```

**Dans Colab, depuis GitHub**

```python
import pandas as pd

URL = "https://raw.github.com/<UTILISATEUR>/<DEPOT>/main/data/raw/<requetes_311>.csv"
df = pd.read_csv(URL)
```



`scikit-learn` sert aux démonstrations de normalisation, d'encodage et de séparation train/test.


## Consignes

1. **Faites une copie** du carnet avant de le modifier (Colab : *Fichier → Enregistrer une copie dans Drive*). Ne travaillez pas sur l'original.
2. **Exécutez les cellules dans l'ordre**, de haut en bas. Au besoin, utilisez *Redémarrer et tout exécuter*.
3. **Justifiez vos décisions** dans des cellules Markdown : pourquoi supprimer, imputer ou conserver ?
4. **Titrez vos graphiques** et indiquez les unités et les axes.
5. Essayez les exercices **avant** de consulter le dossier `solutions/`.
6. Gardez un carnet **reproductible** : quelqu'un d'autre doit pouvoir le relancer et obtenir les mêmes résultats.
