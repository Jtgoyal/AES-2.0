# Automated Essay Scoring Project

This project presents a robust solution for the Automated Essay Scoring 2 Kaggle competition. The approach combines a deep learning model (Deberta) with a traditional gradient boosting model (LightGBM) to achieve high-performance essay scoring.

## 📦 Deliverables

* **Jupyter Notebook (`0-818-deberta-v3-large-lgbm-baseline.ipynb`):** The primary deliverable, containing the full code for data processing, model training, and inference.
* **Submission File (`submission.csv`):** The final output file with essay IDs and their predicted scores, ready for submission to the competition.
* **Trained Models:** The script generates and saves trained LightGBM models for each cross-validation fold.

## 📈 Methodology & Results

The project follows a multi-stage process to build and ensemble the models. The methodology focuses on extracting meaningful features from the text and leveraging the strengths of both neural networks and traditional machine learning algorithms.

### Process Flow

1.  **Data Preprocessing:**
    * The `full_text` data is cleaned by converting it to lowercase, removing HTML tags, numbers, and multiple spaces.
    * Sentences and paragraphs are segmented for feature engineering.

2.  **Feature Engineering:**
    * **Paragraph-level Features:** The number of paragraphs, their length, word count, sentence count, and spelling errors are calculated.
    * **Sentence-level Features:** The length and word count of sentences are computed.
    * **Word-level Features:** The length of each word and the count of words with specific lengths are calculated.

3.  **Vectorization:**
    * **TfidfVectorizer:** Used to capture the importance of n-grams (3 to 6 words) in the text.
    * **CountVectorizer:** Used to count the occurrences of specific n-grams (2 to 3 words).

4.  **Model Integration:**
    * **Deberta Model:** A pre-trained Deberta-v3-large model is fine-tuned and its predictions are used as meta-features for the LightGBM model. This allows the LightGBM model to leverage the deep semantic understanding of the neural network.
    * **LightGBM Model:** An LGBMRegressor is trained using the engineered features and the Deberta predictions. A custom objective function (Quadratic Weighted Kappa) is used to optimize the model directly for the competition metric.

5.  **Training & Cross-Validation:**
    * A 15-fold Stratified K-Fold cross-validation strategy is employed to train multiple LightGBM models, ensuring the model's robustness and preventing overfitting.

### Performance Breakdown

| Stage | LB Score |
| :--- | :---: |
| Deberta Ensemble | 0.807 |
| LGBM with Features | 0.811 |
| LGBM + Deberta (as features) | 0.811 |
| LGBM + Deberta + CountVectorizer | 0.812 |
| LGBM + Deberta + TfidfVectorizer + CountVectorizer | 0.816 |
| LGBM + Deberta + TfidfVectorizer + CountVectorizer + more features | **0.818** |
