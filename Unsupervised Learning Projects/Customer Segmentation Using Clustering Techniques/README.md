# Customer Segmentation Using Clustering Techniques

A reproducible RFM-style customer segmentation project with internal metrics, stability checks, and interpretable profiles.

## Project status

- **Portfolio decision:** Refurbished — non-portable Kaggle path and incomplete execution replaced
- **Learning type:** Unsupervised learning
- **Core method:** K-Means and agglomerative clustering with robust preprocessing
- **Execution:** Notebook executed successfully with outputs committed

## Problem statement

The project demonstrates how patterns, similarities, communities, or anomalies can be discovered without using a prediction target during model fitting. Results are interpreted as exploratory signals rather than ground truth.

## Dataset

A deterministic domain-shaped demo dataset replaces the unavailable external-only dataset so the workflow executes end to end. Results are demo evidence only.

The notebook documents its data contract, reproducible seed, quality checks, and any synthetic proxy labels used only for retrospective diagnostics.

## Workflow

```text
Data validation
      ↓
Feature representation and scaling
      ↓
Unsupervised model comparison
      ↓
Internal metrics and stability checks
      ↓
Interpretation, visualization, and limitations
```

## Evaluation

The notebook uses method-appropriate evidence such as silhouette score, Davies-Bouldin index, cluster stability, retrieval similarity, graph structure, anomaly-score diagnostics, and post-hoc synthetic checks. No demo result is presented as a production benchmark.

## Repository structure

```text
├── Customer Segmentation using Clustering Algorithms.ipynb
└── README.md
```

## How to run

From the repository root:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r "Unsupervised Learning Projects/requirements.txt"
jupyter lab "Unsupervised Learning Projects/Customer Segmentation Using Clustering Techniques/Customer Segmentation using Clustering Algorithms.ipynb"
```

Run the notebook from top to bottom. Saved outputs are included for review.

## Technologies

- Python
- Pandas and NumPy
- Scikit-learn
- Matplotlib and Seaborn
- Jupyter

## Responsible use

Discovered groups and anomaly flags do not establish identity, intent, causality, risk, or business impact. Production use requires domain review, representative data, privacy controls, monitoring, and decision-specific evaluation.