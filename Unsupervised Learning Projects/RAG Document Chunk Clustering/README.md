# RAG Document Chunk Clustering

Group retrieval chunks into coherent themes to inspect coverage, redundancy, and indexing quality in RAG systems.

## Project status

- **Portfolio decision:** New
- **Learning type:** Unsupervised learning
- **Core method:** TF-IDF, K-Means, cosine similarity, and SVD
- **Execution:** Notebook executed successfully with outputs committed

## Problem statement

The project demonstrates how patterns, similarities, communities, or anomalies can be discovered without using a prediction target during model fitting. Results are interpreted as exploratory signals rather than ground truth.

## Dataset

A deterministic domain-shaped text corpus is generated inside the notebook. Hidden generator topics are used only for post-hoc diagnostics.

The notebook documents its data contract, reproducible seed, quality checks, and any synthetic proxy labels used only for retrospective diagnostics.
## Key Results

- **Corpus Representation:** Vectorized **300 document chunks** into a **300 × 500** sparse matrix using sublinear TF-IDF (`ngram_range=(1, 2)`, `min_df=2`)[cite: 4].
- **Optimal Cluster Selection:** Swept `k = 2` to `6` using cosine Silhouette Score, identifying **`k = 4`** as optimal (**0.1421** peak cosine silhouette, **240.64** inertia)[cite: 4].
- **Stability & Retrospective Alignment:** Achieved **1.0000 Adjusted Rand Index (ARI)** across independent random seeds (`random_state=42` vs. `7`) and against hidden ground-truth topic partitions (`access_control`, `data_pipeline`, `model_serving`, `evaluation`)[cite: 4].
- **Query Routing & Retrieval:** Verified cosine-similarity inference by routing incoming text probes to the target cluster and retrieving the **top-5 nearest context chunks** (up to **0.4644** cosine similarity)[cite: 4].
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
├── rag_document_chunk_clustering.ipynb
└── README.md
```

## How to run

From the repository root:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r "Unsupervised Learning Projects/requirements.txt"
jupyter lab "Unsupervised Learning Projects/RAG Document Chunk Clustering/rag_document_chunk_clustering.ipynb"
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
