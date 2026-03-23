# E-Commerce Recommendation System — Collaborative + Content Hybrid

## Overview
A hybrid recommendation engine combining collaborative filtering and content-based approaches for e-commerce product recommendations. Evaluated on ranking quality metrics and served from Redis for real-time lookups.

## Architecture
- **Collaborative Filtering**: Alternating Least Squares (ALS) matrix factorization on user-item interaction matrix
- **Content-Based**: Sentence-transformer embeddings of product descriptions + cosine similarity
- **Hybrid Model**: Weighted ensemble combining collaborative and content-based scores, with weights tuned per user segment
- **Evaluation**: NDCG@K, MAP@K, Hit Rate@K, Coverage, Diversity — not just RMSE
- **Serving**: Daily batch generation via Airflow, pre-computed recommendations stored in Redis keyed by user_id
- **Cold Start**: Content-based fallback for new users/products with no interaction history

## Tech Stack
- Python 3.11+, implicit (ALS), sentence-transformers
- scikit-learn, NumPy, SciPy
- Redis (recommendation serving)
- MLflow (experiment tracking)
- Apache Airflow 2.x
- PostgreSQL
- Docker & Docker Compose

## What This Demonstrates
- Multiple recommendation paradigms and their tradeoffs
- Ranking metric evaluation (beyond RMSE)
- Cold start problem handling
- Embedding-based content similarity
- Low-latency serving with pre-computation
- Daily recommendation refresh pipeline

## Status
🚧 In Development

## Project Structure
├── dags/
│   └── recommendation_dag.py
├── src/
│   ├── collaborative/
│   ├── content_based/
│   ├── hybrid/
│   └── evaluation/
├── notebooks/
├── tests/
├── docker-compose.yml
└── README.md
