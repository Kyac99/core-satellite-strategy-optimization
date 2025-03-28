# Analyse et Optimisation d'une Stratégie Core-Satellite

Ce projet vise à développer, analyser et optimiser une stratégie d'investissement Core-Satellite, combinant un noyau passif et des satellites actifs pour optimiser le ratio rendement/risque.

## Structure de la Stratégie Core-Satellite

L'approche Core-Satellite est une stratégie d'investissement qui combine :
- Un **noyau (core)** : Composé principalement d'investissements passifs (ETF, fonds indiciels) visant à répliquer le marché avec des frais réduits
- Des **satellites** : Composés d'investissements actifs ciblés pour générer de l'alpha (surperformance par rapport au marché)

![Core-Satellite Structure](./docs/images/core-satellite-structure.png)

## Objectifs du Projet

1. Concevoir un portefeuille Core-Satellite optimisé
2. Déterminer les pondérations optimales entre le noyau et les satellites
3. Comparer les performances avec des approches purement passives ou actives
4. Développer des outils d'aide à la décision pour ajuster la stratégie

## Organisation du Repository

```
├── data/                  # Données de marché et historiques
├── docs/                  # Documentation du projet
│   ├── images/            # Images et diagrammes
│   └── research/          # Articles et recherches
├── models/                # Modèles d'optimisation
│   ├── core_allocation/   # Modèles pour l'allocation du core
│   └── satellite/         # Modèles pour la sélection des satellites
├── notebooks/             # Jupyter notebooks pour l'analyse
├── reports/               # Rapports générés
├── src/                   # Code source
│   ├── data_processing/   # Scripts de traitement de données
│   ├── optimization/      # Algorithmes d'optimisation
│   ├── backtesting/       # Module de backtesting
│   └── visualization/     # Outils de visualisation
└── tests/                 # Tests unitaires et d'intégration
```

## Méthodologie

1. **Collecte et préparation des données** : Extraction et nettoyage des données de marché
2. **Conception du noyau (core)** : Sélection d'ETF et de fonds indiciels optimaux
3. **Sélection des satellites** : Identification d'opportunités actives
4. **Optimisation des pondérations** : Utilisation de modèles mathématiques (Markowitz, Black-Litterman)
5. **Backtesting** : Simulation des performances historiques
6. **Analyse des risques** : Évaluation des différentes mesures de risque et stress tests
7. **Construction d'outils d'aide à la décision** : Développement d'interfaces pour ajuster la stratégie

## Technologies Utilisées

- **Python** : Principal langage de programmation
- **Pandas, NumPy** : Manipulation et analyse des données
- **SciPy, PyPortfolioOpt** : Optimisation de portefeuille
- **Matplotlib, Seaborn, Plotly** : Visualisation des données
- **Jupyter Notebooks** : Analyses interactives
- **Yahoo Finance, Alpha Vantage API** : Sources de données

## Installation et Utilisation

```bash
# Cloner le repository
git clone https://github.com/Kyac99/core-satellite-strategy-optimization.git
cd core-satellite-strategy-optimization

# Créer un environnement virtuel
python -m venv venv
source venv/bin/activate  # Sur Windows: venv\Scripts\activate

# Installer les dépendances
pip install -r requirements.txt

# Exécuter les notebooks
jupyter notebook
```

## Planification du Projet

- **Phase 1** (1 mois) : Définition des critères et collecte de données
- **Phase 2** (2 mois) : Construction du modèle et optimisation
- **Phase 3** (1 mois) : Backtesting et validation des résultats
- **Phase 4** (1 mois) : Rédaction du rapport final et présentation

## Licence

MIT

## Contact

Pour toute question concernant ce projet, veuillez contacter [votre équipe]
