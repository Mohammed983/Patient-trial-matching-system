# patient-trial-matching-system

## Overview
Built a graph-based machine learning system to match patients with relevant clinical trials using real-world healthcare datasets. The system models relationships between patients, diseases, and trials to improve ranking quality over traditional keyword-based approaches.

## Problem
Clinical trial recruitment is a major bottleneck in healthcare, often relying on manual screening or simple keyword matching. These approaches fail to capture semantic relationships and do not scale effectively across large datasets.

## Approach

### Data Sources
- MIMIC-IV (patient records)
- ClinicalTrials.gov (trial data)
- SIGIR 2016 benchmark dataset (evaluation)

### System Pipeline
EHR Data → Preprocessing → PubMedBERT Embeddings → Graph Construction → GNN Training → Ranking

### Graph Design
- Nodes: Patients, Diseases, Trials  
- Edges:
  - Patient ↔ Disease ("has")
  - Trial ↔ Disease ("mentions")

### Modeling
- Embeddings: PubMedBERT  
- Graph Neural Networks:
  - R-GCN (SAGEConv)
  - Heterogeneous Graph Transformer (HGT)
- Training:
  - Link prediction objective
  - Dynamic negative sampling
  - Binary cross-entropy loss

### Evaluation
- Ranking metrics:
  - NDCG@10
  - Precision@10
- Compared performance across architectures and configurations

## Results
- Evaluated using ranking metrics (NDCG@10, Precision@10)
- HGT models achieved higher training AUROC compared to R-GCN, at the cost of increased computational overhead
- Demonstrated end-to-end pipeline for patient–trial matching using graph-based learning

## Key Insights
- Data preprocessing and dataset alignment had a significant impact on model performance
- Graph-based methods provide a scalable alternative to LLM-based approaches for structured reasoning tasks
- Performance is sensitive to embedding quality and graph design choices

## My Contributions
- Built MIMIC-IV preprocessing pipeline and patient feature generation
- Trained and tuned HGT-based graph neural network models
- Implemented link prediction and ranking evaluation workflow
- Contributed to system design and experimental analysis

## Tech Stack
Python, PyTorch Geometric, PubMedBERT, Graph Neural Networks

## Note
This project was developed as part of a team effort. The original repository is private.
