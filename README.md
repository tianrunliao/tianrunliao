# Tianrun Liao

M.S. in Applied Data Science at the **University of Chicago**.
B.Fin. with a Data Science minor from **Fudan University**.

I build research systems for quantitative finance, combining machine learning
for time series, factor research and backtesting. I care about the
engineering that makes results trustworthy: leakage-safe validation,
fail-closed automation, deterministic tests, and code that other people can
run.

**Python** · **PyTorch** · **pandas / NumPy** · **SQL (SQLite, DuckDB)** ·
**ruff · mypy · pytest · GitHub Actions**

---

## WorldQuant BRAIN Alpha Mining Platform

[**tianrunliao/worldquant-alpha-mining**](https://github.com/tianrunliao/worldquant-alpha-mining)
[![CI](https://github.com/tianrunliao/worldquant-alpha-mining/actions/workflows/ci.yml/badge.svg)](https://github.com/tianrunliao/worldquant-alpha-mining/actions/workflows/ci.yml)

This is an end-to-end research platform for discovering alpha expressions on
WorldQuant BRAIN. It is about 26k lines of Python.

**Design.** Nine interchangeable search strategies propose candidate
expressions:

1. Typed-tree genetic programming
2. MAP-Elites quality-diversity search
3. MCTS
4. Multi-chain simulated annealing
5. Bayesian optimisation (TPE)
6. Token-level PPO with type-masked actions
7. Neural-surrogate template expansion
8. Template scanning
9. A hypothesis-driven search that budgets explore, validate and refine work
   across economically motivated "cards"

The strategies only write candidates to a queue. A single shared pipeline
then runs:

1. Simulation, with re-authentication and rate-limit back-off.
2. IS checks.
3. A correlation audit against every live alpha.
4. Submission.
5. Polling until the platform confirms the alpha is `ACTIVE`.

Because this logic exists exactly once, every search method is judged by
identical rules. An architecture test fails the build if a strategy reaches
past its boundary.

**Engineering.**

1. **Fail-closed by default.** If live PnL cannot be fetched or aligned, the
   candidate is not submitted.
2. **Sequential submission.** Submission is sequential, so two correlated
   candidates cannot both pass.
3. **Versioned scoring.** The score is versioned and every component is
   logged.
4. **Unified history.** JSONL ledgers and an idempotent SQLite ledger are
   merged under one identity, (normalised expression, settings), with
   claim/release semantics for concurrent workers.
5. **Quality gates.** The core package is mypy-clean, 276 unit tests run on
   Python 3.10 and 3.12 in CI, and ruff and pre-commit enforce style.

**Outcome.** Of my 67 alphas that are ACTIVE on BRAIN, 53 were submitted end
to end by this pipeline (platform snapshot, October 2026). The repository
publishes the code only; submitted alphas and platform data stay private.

---

## Mamba S6 Market Timing for Crypto Factor Strategies

[**tianrunliao/mamba-s6**](https://github.com/tianrunliao/mamba-s6)
[![CI](https://github.com/tianrunliao/mamba-s6/actions/workflows/ci.yml/badge.svg)](https://github.com/tianrunliao/mamba-s6/actions/workflows/ci.yml)

This is my undergraduate thesis, *Market Timing for Financial Assets Based on
State Space Models*. A selective state-space model (Mamba S6) acts as a
portfolio-level risk gate on top of cross-sectional factor strategies for 12
Binance perpetuals.

**Method.**

1. Minute bars are reduced to daily microstructure factors, and the factors
   are weighted by rolling ICIR.
2. A two-block Mamba network reads a 40-day window of portfolio-state
   features. It outputs a target exposure and a regime (trend, balanced or
   risk-off).
3. The model is trained on drawdown-aware path-quality labels with a
   multi-task loss, then fine-tuned walk-forward every 42 days.
4. Execution is simulated open-to-open with a turnover cap, adaptive
   rebalance bands, maker-limit fills with taker fallback, fees and slippage.

**Engineering.**

1. The code is a typed `src/` package with a YAML-configured CLI
   (`mamba-timing download | factors | backtest | report | run`).
2. Golden characterization tests pin every pipeline stage to the original
   implementation on deterministic synthetic data.
3. mypy runs in strict mode and CI runs on Python 3.10 and 3.12.

**Result, reported honestly.** The tests cover 2022-04 to 2026-04 out of
sample. On both books, the overlay cut maximum drawdown (−32.0% → −28.4% and
−66.5% → −57.4%), volatility and turnover. It did not consistently improve
returns. The thesis claims risk shaping, not alpha.

---

## Other work

| Project | Summary |
|---|---|
| [kaggriculture-agents](https://github.com/tianrunliao/kaggriculture-agents) | Kaggle *Kaggriculture* simulation competition, ranked 1,026th of 10,148 teams. Includes the agents and the paired head-to-head evaluation tooling. |

**Undergraduate coursework:**
[numpy-cnn-mnist](https://github.com/tianrunliao/numpy-cnn-mnist) ·
[vgg-batchnorm-cifar10](https://github.com/tianrunliao/vgg-batchnorm-cifar10) ·
[social-spam-detection](https://github.com/tianrunliao/social-spam-detection) ·
[spotify-playlist-recommendation](https://github.com/tianrunliao/spotify-playlist-recommendation)
