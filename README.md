# Hi, I'm Tianrun Liao

I build quantitative-research systems at the intersection of machine learning,
time-series modelling, and production data engineering.

- Incoming M.S. in Applied Data Science student at the University of Chicago.
- B.Fin. with a Data Science minor from Fudan University.
- Interested in quantitative finance, state-space models, factor research,
  robust backtesting, and LLM-assisted research tooling.
- Working mainly with Python, PyTorch, pandas, SQL, and DuckDB.

## Selected projects

### [Mamba S6 for Cryptocurrency Exposure Control](https://github.com/tianrunliao/mamba-s6)

Undergraduate thesis project implementing a selective state-space risk gate,
cross-sectional crypto factors, walk-forward training, and cost-aware execution.
The empirical result is deliberately modest: the overlay improved drawdown,
volatility, and turnover in the reported tests, but did not consistently improve
returns.

### [WorldQuant BRAIN Alpha Mining Platform](https://github.com/tianrunliao/worldquant-alpha-mining)

Research platform with nine pluggable alpha search methods (template scan,
neural-surrogate GP, typed-tree GP, MCTS, annealing, TPE, token-level PPO,
MAP-Elites, and economic hypothesis cards) sharing one fail-closed pipeline for
simulation, IS checks, correlation audit, submission, and ACTIVE verification.
Submitted alphas and platform data are not published.

### [Kaggriculture Simulation Agents](https://github.com/tianrunliao/kaggriculture-agents)

Agents for a two-player farm-economy Kaggle simulation competition, ranked
1,026th of 10,148 teams. The final agent adds opponent identification and
reactive layers to a public Apache-2.0 chassis, validated on paired
head-to-head panels; a second agent is a self-built numpy production and sales
planner.

### [Batch Normalization in VGG Networks](https://github.com/tianrunliao/Deep-Learning-Project2)

CIFAR-10 study comparing VGG training with and without BatchNorm across learning
rates, optimisers, losses, gradient statistics, and loss landscapes.

### [NumPy Neural Networks on MNIST](https://github.com/tianrunliao/Deep-Learning-Project-1)

From-scratch MLP/CNN components and a 576-configuration model study, with a
small Flask interface for interactive experiments.

### [Social Network Spam Detection](https://github.com/tianrunliao/Social-Network-Mining-Group-Assignment)

Graph and profile-feature pipeline comparing class-balanced classifiers and
threshold tuning on an imbalanced labelled network dataset.

### [Spotify Playlist Recommendation](https://github.com/tianrunliao/Music_Recommendation)

Team project combining audio-feature clustering and weighted logistic
regression to generate personalised, diversity-aware song recommendations.

## Current focus

I am especially interested in research infrastructure that turns an idea into a
reproducible experiment: causal feature construction, leakage-resistant
validation, scalable backtests, and clear model diagnostics.

