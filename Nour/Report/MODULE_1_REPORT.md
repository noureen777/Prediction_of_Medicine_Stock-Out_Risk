# Pharmacy Stockout Prediction System
### Module 1: Tabular Data

## 1. Project Overview
* **Objective:** To build a Machine Learning model capable of predicting pharmacy stockouts (**Critical** vs. **Safe**) based on inventory logs and sales data.
* **Dataset:** `numerical_tabular.csv` (1,000 entries).
* **Model Selected:** CatBoost Classifier.

## 2. Preprocessing
The dataset contains historical records of stock levels, sales velocity, and lead times.

### Feature Selection
* **The Columns We Kept:** `current_stock_level`, `avg_weekly_sales`, `lead_time_days`, `medicine_category`, etc.
* **Dropped:** `record_id` and `date` (because this model predicts the current state, not bsaed on time-series).

### Categorical Handling
Features like `medicine_category` and `pharmacy_location_code` were identified as categorical. Instead of creating hundreds of new columns for every single category (One-Hot Encoding), i used CatBoost's built-in ability to handle text. It automatically converts category names like 'Antibiotic' or 'Cairo' into meaningful numbers based on how often they historically lead to stockouts. This keeps our dataset small and makes the model much faster.
## 3. Model Architecture: Why CatBoost?
### Why CatBoost?

* **Handles Categories Naturally:** It reads text columns (like "Antibiotic") directly, avoiding the mess and information loss of manual One-Hot Encoding.
* **Smarter Training (Gradient Boosting):** Instead of one big guess, it builds thousands of small corrections sequentially, allowing it to "reverse-engineer" our complex logic perfectly.
* **Speed & Efficiency:** It uses Symmetric Trees (balanced structures), making it faster and more stable than traditional Random Forests.
  
## 4. Performance & Results
The model achieved perfect performance metrics on the unseen Test Set (20% split).

| Metric | Score | Notes |
| :--- | :--- | :--- |
| **Accuracy** | **100% (1.00)** | Perfect classification |
| **Precision** | **1.00** | No False Positives |
| **Recall** | **1.00** | No False Negatives |
| **Log Loss** | **0.0005** | Dropped from 0.47|

## 5. Is 100% Accuracy Overfitting?
A score of 100% often suggests overfitting (memorizing noise) in real-world data. However, extensive analysis proves this model is **not overfitted**, but rather successfully **Function Learned**.

### Evidence #1: Deterministic Nature of Data
The target variable (`target_stockout`) was generated using a strict mathematical rule (`IF Stock < 20...`). Since there is no probabilistic noise (human error/randomness) in the data, a powerful model like CatBoost is expected to "reverse-engineer" this rule perfectly.

### Evidence #2: Feature Importance Analysis
The Feature Importance chart confirms the model focused only on the causal variables:
* **Top Predictors:** `avg_weekly_sales` (35%), `lead_time_days` (34%), `current_stock_level` (28%).
* **Zero-Impact Features:** `pharmacy_id` (0.00%), `medicine_id` (0.00%).

**Conclusion:** If the model were overfitting, it would have used `pharmacy_id` to memorize specific rows. The fact that it assigned 0.0 importance to IDs proves it ignored the noise and learned the general logic.

## 6. Conclusion
The CatBoost model successfully learned exactly how the pharmacy supply chain works. It gives us reliable and accurate stockout predictions, and it handles both numbers and text data easily.
