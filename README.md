# 📦 Predicting Medicine Stock-Out Risk Using Multimodal Machine Learning

## 🔍 Project Overview
Medicine shortages pose a serious risk to patient safety, healthcare continuity, and operational efficiency in pharmacies.  
This project aims to **predict medicine stock-out events** by leveraging **tabular operational data** and **textual risk reports**, using multiple machine learning models and comparing their performance.

The project follows a **multimodal learning approach**, where different models are trained on different data types to identify the most effective predictors of stock-outs.

---

## 🎯 Problem Statement
Medicine stock-outs occur due to a combination of supply chain disruptions, demand variability, supplier delays, and contextual risk factors.  
Traditional rule-based systems fail to capture the **complex interactions** between these variables.

**Objective:**  
> Predict whether a medicine will experience a stock-out using historical inventory data and textual risk indicators.

---

## 🧠 Approach
We trained **separate models for each data type**, following our instructor’s guidance, then compared their performance:

- **Tabular data** → classical ML models
- **Text data** → NLP-based models
- **Evaluation** → Accuracy, F1-score, Recall, ROC-AUC

Each team member implemented independent models to ensure fair comparison and robustness.

---

## 📊 Data Description

### 1️⃣ Tabular Data
The tabular dataset simulates pharmacy-level operational data inspired by findings from WHO, FDA, and EAHP reports.

**Key features include:**
- Inventory levels & demand
- Supplier reliability
- Lead times & reorder quantities
- Economic and capacity constraints
- Engineered research-based indicators (e.g. shortage history, demand volatility)

**Target Variable:**
- `target_stockout`  
  - `1` → Stock-out occurred  
  - `0` → No stock-out

---

### 2️⃣ Text Data
The text dataset represents **shortage-related risk narratives**, such as:
- Supplier delays
- Regulatory issues
- Manufacturing problems
- Sudden demand spikes

Each text sample is paired with a stock-out outcome label.

---

## 🧪 Data Simulation Methodology
Due to the lack of publicly available, granular pharmacy-level datasets, the data was **synthetically generated** based on:

- WHO technical consultations on medicine shortages
- FDA strategic plans on drug shortage mitigation
- EAHP survey statistics on European medicine shortages
- Peer-reviewed studies identifying stock-out risk factors

Simulation was designed to:
- Preserve realistic feature distributions
- Avoid deterministic rules
- Introduce noise and overlap between classes
- Prevent trivial 100% accuracy models

⚠️ **Note:**  
This dataset is for **research and educational purposes only** and does not represent real patient data.

---

## 🤖 Models Used

### 🔢 Tabular Data Models
| Model | Accuracy | F1-Score | ROC-AUC |
|------|----------|----------|---------|
| Logistic Regression | **0.891** | **0.939** | **0.957**|
| Random Forest | _TBD_ | _TBD_ | _TBD_ |
| XGBoost | _TBD_ | _TBD_ | _TBD_ |
| LightGBM | **0.932** | **0.964** | **0.893** |
| CatBoost | _TBD_ | _TBD_ | _TBD_ |

---

### 📝 Text Data Models
| Model | Accuracy | F1-Score |
|------|----------|----------|
| TF-IDF + Logistic Regression | **0.93** | **0.93** |
| TF-IDF + SVM | _TBD_ | _TBD_ |
| DistilBERT | **0.693** | **0.683**|
| BERT | _TBD_ | _TBD_ |
| RoBERTa | _TBD_ | _TBD_ |

---

## 📈 Key Findings
- Gradient boosting models (especially **LightGBM**) performed best on structured data.
- Text-based models successfully captured shortage risk patterns from unstructured reports.
- Class imbalance significantly impacts recall and must be handled carefully.
- Multimodal analysis provides richer insights than single-source prediction.

---

## 🚀 Future Work
- Fuse tabular and text embeddings into a unified multimodal model
- Apply attention mechanisms for feature importance
- Validate on real-world pharmacy datasets (if available)
- Deploy as a decision-support tool for pharmacists

---

## 🧑‍💻 Team Contributions
Each team member independently:
- Preprocessed one data type
- Trained multiple models
- Evaluated and compared performance
- Documented findings

---

## 📚 References
- World Health Organization (WHO)
- U.S. Food and Drug Administration (FDA)
- European Association of Hospital Pharmacists (EAHP)
- Peer-reviewed medicine shortage studies

---

## 📌 Disclaimer
This project is intended for **academic research and competition purposes only**.  
No real patient or pharmacy data was used.


