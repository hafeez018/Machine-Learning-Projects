# Airbnb Stock Price Prediction

Forecast Airbnb's next trading-day closing price from information available by the end of the current trading day.

## Overview

This project is a focused, reproducible regression case study. The notebook covers data checks, meaningful exploratory analysis,, leakage-safe preprocessing, a dummy baseline, cross-validated model comparison, untouched holdout evaluation and model interpretation.

## Problem statement

- **Task:** Regression
- **Target:** `next trading day's closing price`
- **Primary metric:** MAE
- **Goal:** Forecast Airbnb's next trading-day closing price from information available by the end of the current trading day.

## Dataset

- **Availability:** Included: `ABNB.csv`
- **Recorded source:** [https://www.kaggle.com/datasets/whenamancodes/airbnb-inc-stock-market-analysis](https://www.kaggle.com/datasets/whenamancodes/airbnb-inc-stock-market-analysis)
- **Target:** `next trading day's closing price`

Dataset licensing and usage conditions remain with the original publisher. Large or externally hosted data is intentionally not duplicated here.

## Project workflow

```text
Data validation
      ↓
Focused EDA
      ↓
Train / holdout split
      ↓
Pipeline-based preprocessing
      ↓
Baseline and cross-validation
      ↓
Holdout evaluation
      ↓
Error analysis and interpretation
```

## Modelling decisions

- Chronological holdout and TimeSeriesSplit replace the original random split.
- Lag and rolling features are shifted so they cannot see the prediction target.

### Models compared

- Naive previous close
- Ridge Regression
- Random Forest

## Evaluation

The notebook evaluates MAE, RMSE and R², supported by residual diagnostics.

## Verified results

The refurbished notebook was executed successfully against the dataset currently committed in this project. The untouched holdout produced:

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Previous-close baseline | 3.0605 | 3.8005 | 0.8594 |
| Ridge Regression | 3.7332 | 4.7025 | 0.7847 |

The learned Ridge model did **not** beat the previous-close baseline on the chronological holdout. That negative result is important: this feature set does not justify a stronger forecasting claim.

These values are a reproducibility record for the current data and dependency range, not a production benchmark.

## Repository structure

```text
├── airbnb_stock_price_prediction.ipynb
├── README.md
└── ABNB.csv
```

## How to run

From this project directory:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r ../requirements.txt
jupyter lab 'airbnb_stock_price_prediction.ipynb'
```

If the dataset is not included, download it from the recorded source and use the exact filename shown above. Run notebook cells from top to bottom.

## Technologies

- Python
- Pandas and NumPy
- Scikit-learn
- Matplotlib and Seaborn
- Jupyter

## Future improvements

- Validate on a newer or independently collected dataset.
- Add domain-specific error costs and decision thresholds.
- Track data drift and subgroup performance before deployment.
- Package the fitted pipeline only after data and licensing checks.
