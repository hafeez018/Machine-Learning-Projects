# LLM Token Cost Anomaly Detection

Detect expensive or looping LLM requests from tokens, latency, tool calls, retries, context ratio, and estimated cost.

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
## Key Results

- **Dataset & Features:** Evaluated across **1,000 telemetry windows** (960 normal, 40 injected stress scenarios) tracking 6 operational features: `input_tokens`, `output_tokens`, `latency_seconds`, `tool_calls`, `retry_count`, and `estimated_cost_usd`[cite: 2].
- **Model Comparison (Retrospective Diagnostics):**
  - **Isolation Forest** (`n_estimators=240`, `contamination=0.04` with `RobustScaler`): Achieved **1.0000** Precision, Recall, F1-score, and ROC-AUC[cite: 2].
  - **Local Outlier Factor** (`n_neighbors=35`, `contamination=0.04`): Achieved **0.1941** ROC-AUC (`0.0000` F1), highlighting how dense burst anomalies evade local neighborhood density checks[cite: 2].
- **Root-Cause Attribution:** Median Absolute Deviation (MAD) scoring ranked top drivers per alert, isolating `retry_count` spikes up to **27.84x robust deviation** above baseline medians[cite: 2].
  
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
├── llm_token_cost_anomaly_detection.ipynb
└── README.md
```

## How to run

From the repository root:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r "Unsupervised Learning Projects/requirements.txt"
jupyter lab "Unsupervised Learning Projects/LLM Token Cost Anomaly Detection/llm_token_cost_anomaly_detection.ipynb"
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
