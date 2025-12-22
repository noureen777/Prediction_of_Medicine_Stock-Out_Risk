🏥 Project Overview: Medicine Stock-Out Risk Prediction
Problem Statement

Medicine shortages pose a serious risk to patient care, especially when pharmacies are unable to anticipate stock-outs in advance. These shortages lead to delayed treatments, increased costs, and compromised healthcare quality.
This project aims to predict medicine stock-out risk early using both structured (tabular) and unstructured (textual) data to support proactive inventory decision-making.

Data Description

The project uses two data modalities:

Tabular Data:
Pharmacy-level and medicine-level operational features, including stock levels, demand patterns, supplier reliability, lead times, and historical shortage indicators.

Text Data:
Unstructured text reports related to medicine availability, risk descriptions, and contextual signals, enriched with engineered features such as sentiment, keyword frequency, and risk scores.

All data was cleaned, preprocessed, and split chronologically to prevent data leakage.

Modeling Approach

Each team member independently trained models on each data type to allow fair comparison and evaluation.

1️⃣ Tabular Model – LightGBM

Model: LightGBM Classifier

Why: Handles non-linear relationships, class imbalance, and structured healthcare data effectively

Techniques Used:

Time-based train/validation/test split

Class imbalance handling using class weights

Feature engineering inspired by healthcare supply chain research

2️⃣ Text Model – TF-IDF + Logistic Regression

Model: TF-IDF Vectorizer + Logistic Regression

Why: Strong baseline for text classification with interpretability and efficiency

Techniques Used:

Text cleaning and normalization

TF-IDF feature extraction

Binary classification for stock-out risk
