# WOA–FCM–CNN–WNN–Informer for Photovoltaic Power Forecasting

**Publication:** WOA-FCM-CNN-WNN-informer: An advanced hybrid deep learning model for ultra-accurate PV power forecasting in electric mobility  
**Journal:** Intelligent Systems with Applications (2026)  
**DOI:** https://doi.org/10.1016/j.iswa.2026.200630

## Method

The predictive chain integrates fuzzy C-means regime memberships, convolutional local features, wavelet-based representations and Informer-style temporal attention. Whale Optimization Algorithm search is available for hyperparameter selection.

The project includes chronological data preparation, model fitting, optional hyperparameter selection, evaluation metrics and graphical diagnostics. The architecture family and training parameters are configured in [config.json](config.json).

## Input data

The training script accepts a time-ordered multivariate CSV with a numeric `target` column. The target in this study is **photovoltaic power**. Dataset columns and evaluation assumptions are discussed in [data/README.md](data/README.md). Source data must be obtained from the study's experimental dataset and should be kept distinct from the synthetic software check.

## Installation and execution

```bash
python -m venv .venv
pip install -r requirements.txt
pytest -q
python train.py --smoke --epochs 2 --out outputs/smoke
```

With measured time-series data:

```bash
python train.py --csv path/to/measurements.csv --target target --time-col time --epochs 40 --out outputs/experiment
```

The program saves training history, test predictions, error metrics, and a fitted checkpoint under the chosen output directory. Optional parameter search is supported through `--search paper --trials N`, subject to the method-specific qualifications below.

## Evaluation notes

The sparse-attention module is a reduced Informer-style implementation. Full optimizer search budgets and paper-specific feature selection must be audited before reproducing the published performance.

The test interval is chronological. Normalization statistics must be estimated on training data, and all reported comparisons should specify the time span, forecast horizon, seed, target units and metric definitions. [REPRODUCIBILITY.md](REPRODUCIBILITY.md) records the implementation boundaries and outstanding experimental checks.
