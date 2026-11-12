# Customer Lifetime Value Prediction

Estimate customer lifetime value for retention prioritization while separating prediction from causal impact.

## Why this project matters

This is a portfolio-ready supervised-learning workflow built around a current business use case. It shows how to move from a documented data contract to a baseline, a validated model, honest holdout evaluation, and responsible interpretation.

## Problem framing

- **Learning type:** Supervised regression
- **Primary methods:** ridge regression and random forests
- **Evaluation:** MAE, RMSE, and R²
- **Decision boundary:** Predictions support prioritization and review; they do not replace domain judgment.

## Data

The notebook creates a deterministic, domain-shaped demonstration dataset locally. This keeps the project executable and avoids publishing private or questionably licensed data. The schema, target, caveats, and migration path to real data are documented in the notebook.

## Workflow

1. Reproducible environment and seed
2. Data contract and quality checks
3. Exploratory analysis
4. Leakage-safe or chronological split
5. Baseline and candidate-model comparison
6. Holdout metrics and diagnostics
7. Explainability or operational interpretation
8. Limitations, monitoring, and next steps

## Results

The notebook is committed with executed outputs. Open [customer_lifetime_value.ipynb](customer_lifetime_value.ipynb) to inspect the actual model comparison, plots, holdout metrics, diagnostics, and sample predictions generated from the reproducible demo data.

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r ../requirements.txt
jupyter lab "customer_lifetime_value.ipynb"
```

Run cells from top to bottom. Use the recorded package versions and replace the demo data only after matching the documented schema.

## Technologies

- Python
- pandas and NumPy
- scikit-learn
- Matplotlib and Seaborn
- Jupyter Notebook

## Limitations and next steps

- Demo metrics are not production benchmarks.
- Validate on licensed, representative, time-appropriate data.
- Audit leakage, calibration, subgroup behavior, drift, and business error costs.
- Add human-review, monitoring, retraining, and rollback policies before deployment.
