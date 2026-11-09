# Experimental reproducibility

**Study:** WOA-FCM-CNN-WNN-informer: An advanced hybrid deep learning model for ultra-accurate PV power forecasting in electric mobility  
**DOI:** https://doi.org/10.1016/j.iswa.2026.200630

## Scope of implementation

The implementation couples fuzzy atmospheric-regime encoding, wavelet-oriented convolutional features, sparse temporal attention and WOA parameter selection for photovoltaic power prediction.

The Informer component uses a compact sparse-attention approximation. Replication requires an audit of WOA objective, search budget, full attention architecture and PV data partitioning.

## Data handling and evaluation

Measured data are supplied as an external time-ordered CSV rather than packaged with the source code. Normalization statistics and fuzzy-regime parameters, where used, must be fitted on training observations only. Input windows must not include future target values.

The default training workflow uses chronological partitions for model development, residual calibration (when applicable), validation and final evaluation. Multiple cities, sites, meteorological regimes or horizons need separately documented holdout protocols; a successful single-series run is not evidence of generalization.

## Reporting requirements

A repeatable experiment records the source dataset and its license, feature definitions, sampling period, target units, forecast horizon, random seeds, optimizer budget, train/test boundaries and all metric definitions. The software check `python train.py --smoke` uses simulated signals and serves only to validate execution.

Paper-level numerical agreement has not been independently established. The results of new runs should be reported as new experiments, with explicit comparison settings rather than attributed to the published results.
