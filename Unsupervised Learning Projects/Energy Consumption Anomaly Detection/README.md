# Energy Consumption Anomaly Detection

Identify unusual energy intervals from demand, temperature, occupancy, reactive power, load factor, and peak ratio.

## Project status

- **Portfolio decision:** New
- **Learning type:** Unsupervised learning
- **Core method:** Isolation Forest and Local Outlier Factor with robust scaling and PCA
- **Execution:** Notebook executed successfully with outputs committed

## Problem statement

The project demonstrates how patterns, similarities, communities, or anomalies can be discovered without using a prediction target during model fitting. Results are interpreted as exploratory signals rather than ground truth.

## Dataset

A deterministic normal-behavior dataset with rare injected stress cases is generated inside the notebook. Scenario flags are excluded from training.

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
├── energy_consumption_anomaly_detection.ipynb
└── README.md
```

## How to run

From the repository root:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r "Unsupervised Learning Projects/requirements.txt"
jupyter lab "Unsupervised Learning Projects/Energy Consumption Anomaly Detection/energy_consumption_anomaly_detection.ipynb"
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