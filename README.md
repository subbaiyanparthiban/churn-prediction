# 📉 Customer Churn Prediction – Food Delivery Platform

---

## 🚀 Project Overview
Customer churn is a major challenge for online food delivery platforms, where a large portion of users place only one or two orders and then become inactive.

This project simulates an **internal Applied Machine Learning initiative** to **predict customers likely to churn in the next 30 days**, enabling proactive retention strategies such as targeted offers, loyalty rewards, and engagement nudges.

The solution is built using a real-world **Food Delivery Order History Dataset** and follows **industry-standard ML practices**, including time-based labeling, feature engineering, imbalance handling, and business-aware threshold tuning.

---

## 🎯 Business Problem
> How can we identify customers who are at high risk of churn so that retention actions can be applied before they stop ordering?

### Business Value
- Improves customer lifetime value (CLV)
- Reduces cost of reacquisition
- Enables personalized loyalty and discount strategies
- Supports data-driven decision-making for retention teams

---

## 📌 Churn Definition
A customer is considered **churned** if:
- Churn labels are **engineered**, not provided directly
- Only **successfully delivered orders** are considered to avoid operational noise

This definition mirrors real-world churn modeling practices in consumer platforms.

---

## 📊 Dataset Description

### Dataset Source
- **Food Delivery Order History Dataset** (Kaggle)
- Total records: ~21,000 orders
- Granularity: Order-level transactional data

### Key Columns Used
| Category | Columns |
|--------|--------|
| Customer | `Customer ID` |
| Order | `Order ID`, `Order Placed At`, `Order Status` |
| Location | `City`, `Subzone` |
| Pricing | `Bill subtotal`, `Total`, `Packaging charges` |
| Discounts | `Gold discount`, `Brand pack discount`, `Restaurant discounts` |
| Operations | `KPT duration`, `Rider wait time`, `Distance` |

Highly sparse columns (ratings, reviews, complaints, cancellation metadata) were intentionally dropped during EDA.

---

## 🔍 Exploratory Data Analysis (EDA)

Key findings from EDA:
- >99% of orders are successfully delivered → churn modeling is restricted to delivered orders
- Customer behavior is highly skewed:
  - Median orders per customer = 1
  - Small group of power users
- Churn rate ≈ **74%**, confirming a strongly imbalanced classification problem
- Recency and engagement decay are stronger churn signals than raw spend

EDA guided:
- Feature selection
- Imbalance-aware modeling
- Metric choice (Recall, ROC-AUC over Accuracy)

---

## 🧠 Feature Engineering

All features are engineered at the **customer level** using historical data only (no leakage).

### Behavioral Features
- Total orders
- Orders in last 30 / 60 / 90 days
- Recency (days since last order)
- Customer tenure
- Average order value
- Total spend

### Discount & Price Sensitivity
- Average discount amount
- Discount usage rate
- Net spend behavior

### Operational Experience
- Average kitchen preparation time (KPT)
- Average rider wait time
- Average delivery distance (normalized to km)

Distance values with mixed formats (e.g. `"3 km"`, `"850 m"`, `"<1 km"`) were normalized using a robust parser.

---

## 🧪 Modeling Approach

The problem is framed as a **binary classification task** with heavy class imbalance.

### Models Trained
1. **Logistic Regression**
   - Baseline model
   - Interpretable coefficients
   - `class_weight="balanced"`

2. **Random Forest**
   - Captures non-linear customer behavior
   - Feature importance analysis
   - Lightweight hyperparameter tuning using `RandomizedSearchCV`

3. **XGBoost (Final Model)**
   - Best performance on structured tabular data
   - Handles feature interactions effectively
   - Uses `scale_pos_weight` to address class imbalance

---

## 📈 Evaluation Strategy

Because churn prediction is imbalanced, **accuracy is not used**.

### Primary Metrics
- **Recall (Churn = 1)** – minimize missed churners
- **ROC-AUC** – overall discrimination
- **Precision–Recall trade-off** – business cost awareness

### Threshold Tuning
Instead of using the default 0.5 threshold:
- A **business-constrained threshold** is selected:
  - Recall ≥ 80%
  - Precision ≥ 30%

This avoids the trivial (and useless) solution of predicting everyone as churn.

---

## 🏆 Final Model Selection

**XGBoost with a business-optimized decision threshold** is selected as the final model due to:
- Highest recall with acceptable precision
- Strong ROC-AUC
- Robust handling of non-linear patterns and imbalance

---

## 📂 Project Structure

- **data/**
  - **raw/** – Original dataset (unchanged)
  - **processed/** – Model-ready customer-level features
- **notebooks/**
  - **01_eda.ipynb** – Exploratory Data Analysis
  - **02_feature_engineering.ipynb** – Feature creation
  - **03_modeling.ipynb** – Modeling, tuning, and evaluation
- **README.md**
- **requirements.txt**

---

## ⚠️ Assumptions & Limitations
- Dataset is a proxy for production data
- Predictions are generated in batch mode
- External factors (competitor offers, UI changes) are not included
- Real-time deployment is out of scope

These are documented intentionally to keep the project transparent and interview-safe.

---

## 🔮 Future Improvements
- Add time-series features (trend in engagement)
- Introduce customer lifecycle stages
- Deploy model as a REST API
- Add monitoring and retraining pipeline (MLOps)

---

## 🧠 Key Takeaways
- Real-world ML problems rarely come with clean labels
- Feature engineering and business context matter more than model choice
- Threshold tuning is essential for operational usefulness

---

## 📬 Contact
**Parthiban Subbaiyan**  
Applied Machine Learning Engineer  
🔗 LinkedIn: https://www.linkedin.com/in/parthiban-subbaiyan/

---

⭐ This project represents a realistic, business-driven churn prediction workflow.
