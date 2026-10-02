# À lire avant de lancer le code

Bienvenue ! :) 

Ce dépôt contient mon projet de machine learning réalisé dans le cadre du DESU : **prédire le CO₂ émis par habitant d'un pays à partir de son profil socio-économique**.

Ce fichier explique comment installer l'environnement et exécuter le notebook!

---

## Contenu du dépôt

| Fichier | Rôle |
|---|---|
| `Climat_DM_clean.ipynb` | **Le notebook du projet** : c'est lui qu'il faut ouvrir et exécuter. |
| `global_climate_co2_anomalies.csv` | Données climatiques Kaggle (https://www.kaggle.com/datasets/mohankrishnathalla/global-climate-and-co-anomalies-19902024/data) |
| `view_cabinet.csv` | Données politiques ParlGov (gouvernements et score gauche-droite). |
| `identifying_ideologues.tab` | Données politiques Global Leader Ideology (orientation des chefs de gouvernement). |
| `requirements.txt` | Liste des bibliothèques Python et de leurs versions. |

---

## Procédure

### Récupérer le projet

```bash
git clone https://github.com/julietteboron/DESU_projet.git
cd DESU_projet
```

### Créer l'environnement et installer les bibliothèques

Dans un terminal, depuis le dossier `DESU_projet` :

```bash
conda create -n desu_climat python=3.12
conda activate desu_climat
pip install -r requirements.txt
```

> ⚠️ Gardez bien les versions de `requirements.txt`, en particulier `numpy==1.26.4` : TensorFlow essaie sinon d'installer numpy 2.x, qui est incompatible avec la version de scipy utilisée et fait planter scikit-learn.

### Ouvrir le notebook avec le bon environnement

1. Ouvrez `Climat_DM_clean.ipynb` dans VS Code.
2. Sélectionnez le kernel **`desu_climat`** (en haut à droite dans VS Code : *Select Kernel* → *Python Environments* → `desu_climat`).

### Exécuter

Lancez **Run All** (*Exécuter tout*) et exécutez les cellules **dans l'ordre** : chaque partie réutilise les variables des parties précédentes.

> ⏱️ **La première exécution est longue** : les recherches d'hyperparamètres Optuna (200 et 1000 essais) et l'entraînement du LSTM prennent du temps. Les résultats Optuna sont ensuite sauvegardés dans un dossier `cache_optuna/` et simplement rechargés lors des exécutions suivantes.
> Si vous modifiez les données ou les réglages d'Optuna, supprimez `cache_optuna/` pour relancer les recherches.

---


## Sources des données politiques

- **ParlGov** : Döring, H., Huber, C. & Manow, P. *ParlGov database* — https://www.parlgov.org
- **Global Leader Ideology** : Herre, B. (2023). *Identifying Ideologues: A Global Dataset on Political Leaders, 1945–2020*. British Journal of Political Science.
- **Régimes politiques (V-Dem)** : Our World in Data, d'après V-Dem / Lührmann et al., *Regimes of the World* — https://ourworldindata.org/grapher/political-regime

---

## En cas de problème

- **`FileNotFoundError` sur un fichier `.csv` ou `.tab`** : le notebook n'est pas exécuté depuis le dossier `DESU_projet`.
- **`ModuleNotFoundError`** : le kernel sélectionné n'est pas `desu_climat`, ou l'installation de l'étape 3 n'a pas abouti.
- **Erreur liée à numpy ou scipy** (par ex. `numpy.core.multiarray failed to import`) : réinstallez les versions exactes avec `pip install -r requirements.txt`, puis redémarrez le kernel.
- **Erreur dans la cellule V-Dem** : vérifiez la connexion internet.

Bonne exploration !

Juliette 
