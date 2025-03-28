# Analyse et Optimisation d'une Stratégie Core-Satellite

Ce projet vise à développer, analyser et optimiser une stratégie d'investissement Core-Satellite, combinant un noyau passif et des satellites actifs pour optimiser le ratio rendement/risque.

## Structure de la Stratégie Core-Satellite

L'approche Core-Satellite est une stratégie d'investissement qui combine :
- Un **noyau (core)** : Composé principalement d'investissements passifs (ETF, fonds indiciels) visant à répliquer le marché avec des frais réduits
- Des **satellites** : Composés d'investissements actifs ciblés pour générer de l'alpha (surperformance par rapport au marché)

![Core-Satellite Structure](./docs/images/core-satellite-structure.png)

## Fonctionnalités Implémentées

### 1. Traitement des Données (`src/data_processing`)
- Chargement des données financières via yfinance
- Calcul des rendements et des statistiques d'actifs
- Analyse de corrélation entre actifs

### 2. Optimisation Core-Satellite (`src/optimization`)
- Optimisation du portefeuille core avec modèle moyenne-variance
- Optimisation des satellites pour générer de l'alpha
- Détermination du ratio optimal entre core et satellites
- Optimisation sous contraintes (min/max par classe d'actifs)

### 3. Visualisation (`src/visualization`)
- Frontière efficiente pour core et satellites
- Allocation des poids du portefeuille (pie charts, treemaps)
- Structure core-satellite avec vis. imbriquées
- Contribution au risque par actif
- Performance et métriques de risque

### 4. Backtesting (`src/backtesting`)
- Simulation de la stratégie sur données historiques
- Rebalancement périodique (trimestriel, mensuel, annuel)
- Calcul des métriques de performance
- Comparaison avec des benchmarks (core-only, satellite-only)

## Exemples d'Utilisation

Vous trouverez un exemple complet d'utilisation dans le notebook `notebooks/01_Core_Satellite_Examples.ipynb`. Ce notebook démontre :

```python
# Exemple d'utilisation basique
from src.data_processing.data_loader import DataLoader
from src.optimization.core_satellite import CoreSatelliteOptimizer

# Charger les données
data_loader = DataLoader(start_date='2018-01-01', end_date='2023-12-31')
prices, returns = data_loader.get_asset_data(['SPY', 'QQQ', 'EFA', ...], ['AAPL', 'MSFT', ...])

# Optimiser le portefeuille core-satellite
optimizer = CoreSatelliteOptimizer(returns[core_tickers], returns[satellite_tickers])
metrics, weights = optimizer.get_optimal_portfolio(risk_aversion=2.0, min_core=0.3, max_core=0.9)

# Backtest de la stratégie
backtest = CoreSatelliteBacktest(prices, lookback_window=252, rebalance_freq='Q')
results = backtest.run_backtest(CoreSatelliteOptimizer, core_tickers, satellite_tickers)
```

## Organisation du Repository

```
├── data/                  # Données de marché et historiques (non incluses dans le repo)
├── docs/                  # Documentation du projet
├── models/                # Modèles d'optimisation
├── notebooks/             # Jupyter notebooks pour l'analyse
│   └── 01_Core_Satellite_Examples.ipynb  # Exemple complet
├── reports/               # Rapports générés
├── src/                   # Code source
│   ├── data_processing/    # Scripts de traitement de données
│   │   └── data_loader.py   # Chargement et préparation des données
│   ├── optimization/       # Algorithmes d'optimisation
│   │   └── core_satellite.py  # Optimiseur Core-Satellite
│   ├── backtesting/        # Module de backtesting
│   │   └── core_satellite_backtest.py  # Backtesting de la stratégie
│   └── visualization/      # Outils de visualisation
│       └── portfolio_visualizer.py  # Visualisation des résultats
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
- **SciPy** : Optimisation de portefeuille
- **Matplotlib, Seaborn** : Visualisation des données
- **Jupyter Notebooks** : Analyses interactives
- **Yahoo Finance** : Source de données financières

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

## Résultats et Perspectives

Les résultats préliminaires montrent que la stratégie Core-Satellite peut offrir un meilleur compromis risque-rendement qu'une stratégie purement passive ou active. En particulier :

- **Diversification améliorée** : Combinaison optimale d'exposition au marché et d'opportunités de croissance
- **Réduction des coûts** : La majeure partie du portefeuille reste dans des investissements à faible coût
- **Meilleure gestion du risque** : Réduction de la volatilité et des drawdowns par rapport à un portefeuille tout-satellite

Les extensions futures de ce projet pourraient inclure :
- Intégration de modèles de prévision pour l'allocation dynamique
- Incorporation de contraintes ESG dans l'optimisation
- Développement d'une interface utilisateur pour le pilotage de la stratégie

## Licence

MIT

## Contact

Pour toute question concernant ce projet, n'hésitez pas à me contacter.
