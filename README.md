# projet-web-2-dynamique-world-comparator
Application web interactive permettant de comparer la qualité de vie entre deux pays selon 8 métriques pondérées par l'utilisateur.

# Description
Ce projet implémente un pipeline ETL (Extract-Transform-Load) complet qui récupère des données de qualité de vie depuis plusieurs sources ouvertes, les normalise, puis les affiche via une interface web interactive.

L'utilisateur peut :

Classer les 8 métriques par ordre d'importance (coefficients de 4 à 0.5)
Sélectionner deux pays à comparer
Visualiser les résultats via des graphiques radar et barres (Chart.js)

# Les 8 Métriques
| Métrique | Source | Description |
| :--- | :--- | :--- |
| **Santé** | Our World in Data | Espérance de vie |
| **Éducation** | Our World in Data | Années de scolarité moyennes |
| **Universités** | Shanghai Ranking ARWU | Nombre d'universités dans le Top 1000 |
| **Sécurité** | DataPandas | Indice de sécurité mondial |
| **Pouvoir d'achat** | Our World in Data | PIB par habitant |
| **Emploi** | Our World in Data | Taux d'emploi (inverse du chômage) |
| **Bonheur** | Our World in Data | Indice de bonheur (Cantril Ladder) |
| **Liberté** | Our World in Data | Indice des droits humains (V-Dem) |

### Architecture du Projet

```text
projet-web-2-dynamique-world-comparator/
├── index.html
├── styles.css
├── run_pipeline.py       # script ETL tout-en-un
├── etl/
│   ├── extract.py
│   ├── transform.py
│   └── load.py
└── data/
    ├── raw_*.csv         # données brutes extraites
    ├── norm_*.csv        # données normalisées
    └── pays.json         # données finales pour le frontend

## Exécution

### Prérequis

* Python 3.x
* Bibliothèques : `pandas`, `requests`, `lxml`

### Installation des dépendances

```bash
pip install pandas requests lxml

# option 1 : script tout-en-un
python run_pipeline.py

# option 2 : scripts séparés
python etl/extract.py
python etl/transform.py
python etl/load.py
