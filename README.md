Automated Essay Scoring (AES)

🚀 An implementation of Automated Essay Scoring using a hybrid approach that combines transformer-based embeddings (DeBERTa-v3) with gradient boosting models (LightGBM, XGBoost, CatBoost).
The system predicts essay scores automatically and achieves strong agreement with human raters.

📌 Overview

Essay scoring is a subjective and time-consuming task for educators. This project leverages state-of-the-art NLP models to evaluate essays with high reliability.
The workflow integrates:

DeBERTa-v3-base embeddings for rich contextual essay representation.

Gradient boosting models (LightGBM, XGBoost, CatBoost) for robust regression-based scoring.

Ensemble learning to boost performance and reduce variance.

🛠️ Features

Preprocessing pipeline for essay text.

Transformer-based feature extraction (DeBERTa-v3).

Gradient boosting models for regression on essay scores.

Evaluation using Quadratic Weighted Kappa (QWK), the standard metric in AES tasks.

Achieved QWK ≈ 0.8331 on benchmark dataset.

📊 Results

Metric: Quadratic Weighted Kappa (QWK)

Best Score: ~0.8331

Demonstrates strong alignment with human grading.
