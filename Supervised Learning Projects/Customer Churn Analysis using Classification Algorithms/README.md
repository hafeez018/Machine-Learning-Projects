# Customer Churn Classification

Compare linear and tree-based classifiers for telecom customer churn.

## Overview

This project is a focused, reproducible classification case study. The notebook covers data checks, meaningful exploratory analysis, leakage-safe preprocessing, a dummy baseline, cross-validated model comparison, untouched holdout evaluation and model interpretation.

## Problem statement

- **Task:** Classification
- **Target:** `Churn`
- **Primary metric:** Macro F1
- **Goal:** Compare linear and tree-based classifiers for telecom customer churn.

## Dataset

- **Availability:** Included: `churn.csv`
- **Recorded source:** Dataset file is included in this project.
- **Target:** `Churn`

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

- The split is stratified and seeded.
- Categorical encoding and numeric scaling are learned only from training folds.

### Models compared

- Logistic Regression
- Decision Tree
- Random Forest

## Evaluation

The notebook evaluates macro F1 and accuracy, with class-level precision/recall and a confusion matrix.

## Verified results

The refurbished notebook was executed successfully against the dataset currently committed in this project. The untouched holdout produced:

| Selected model | Accuracy | Macro F1 |
|---|---:|---:|
| Logistic Regression | 0.8055 | 0.7376 |

These values are a reproducibility record for the current data and dependency range, not a production benchmark.

## Repository structure

```text
├── customer_churn_classification.ipynb
├── README.md
└── churn.csv
```

## How to run

From this project directory:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r ../requirements.txt
jupyter lab 'customer_churn_classification.ipynb'
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
