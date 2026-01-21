# 📉 Customer Churn Prediction – Food Delivery Platform

## 🚀 Project Overview
Customer churn is a critical challenge for online food delivery platforms, especially when customer engagement drops after discounts or promotions end.

This project simulates an **internal applied machine learning initiative** to **predict customers likely to churn in the next 30 days**, enabling proactive retention strategies such as personalized offers, loyalty rewards, or engagement nudges.

The solution is built using **publicly available transactional data** and **domain-driven feature engineering**, closely mirroring real-world industry practices.

---

## 🎯 Business Problem
> How can we identify customers who are at high risk of churning so that retention actions can be applied before they stop ordering?

### Why this matters
- Acquiring new customers is more expensive than retaining existing ones
- Early churn prediction helps improve:
  - Customer Lifetime Value (CLV)
  - Repeat order rate
  - Loyalty program effectiveness

---

## 📌 Churn Definition
A customer is considered **churned** if:
They place ZERO orders in the next 30 days
This definition is:
- Simple and realistic
- Commonly used in consumer platforms
- Easy to operationalize in production systems

---

## 📊 Dataset
- Source: Public food delivery / transactional datasets from Kaggle
- Data type: Customer-level order and engagement data
- Data is anonymized and used only for learning and demonstration purposes

### Key Data Fields
| Category | Examples |
|--------|----------|
| Customer | customer_id |
| Orders | order_date, order_value |
| Engagement | order_frequency, days_since_last_order |
| Promotions | coupon_usage |
| Loyalty | points_earned, points_redeemed |

> **Note:** Churn labels are **engineered**, not provided directly — reflecting real-world ML workflows.

---

## 🧠 Feature Engineering
Features are designed based on **product and domain knowledge** rather than blindly using raw data.

### Behavioral Features
- Orders in last 30 / 60 / 90 days
- Average order value
- Days since last order

### Loyalty & Promotion Features
- Loyalty points earned
- Loyalty points redeemed
- Coupon usage rate

### Engagement Signals
- Order frequency trends
- Weekend vs weekday ordering behavior

These features help capture **customer intent and engagement decay**.

---

## 🧪 Modeling Approach
Three models are trained and compared:

1. **Logistic Regression** – baseline model
2. **Random Forest** – captures non-linear relationships
3. **XGBoost / Gradient Boosting** – performance-focused model

### Why multiple models?
- Establish a baseline
- Compare interpretability vs performance
- Avoid overfitting to a single approach

---

## 📈 Evaluation Metrics
Churn prediction is an **imbalanced classification problem**, so accuracy alone is misleading.

Primary metrics:
- **ROC-AUC** – overall model discrimination
- **Recall (Churn Class)** – ability to catch at-risk customers
- **Precision–Recall trade-off** – cost-sensitive evaluation

> In churn prediction, missing a churner is more expensive than flagging a false positive.

---

## 📂 Project Structure

    churn-prediction/
    │
    ├── data/
    │   ├── raw/                 # Original dataset (unchanged)
    │   └── processed/           # Cleaned & feature-engineered data
    │
    ├── notebooks/
    │   ├── 01_eda.ipynb         # Exploratory Data Analysis
    │   ├── 02_feature_engineering.ipynb
    │   └── 03_modeling.ipynb
    │
    ├── src/
    │   ├── preprocessing.py    # Data cleaning & feature logic
    │   ├── train.py            # Model training pipeline
    │   └── evaluate.py         # Model evaluation & metrics
    │
    ├── README.md
    └── requirements.txt

---

## 💼 Business Impact & Use Case
The model output can be used to:
- Identify top X% high-risk customers
- Trigger targeted retention campaigns
- Optimize loyalty rewards distribution
- Reduce customer churn proactively

Example:
> Retaining even 5–10% of high-risk customers can significantly improve revenue and customer lifetime value.

---

## ⚠️ Assumptions & Limitations
- Dataset is a proxy for real production data
- Predictions are generated in batch mode
- External factors (competition, delivery delays) are not included
- 
---

## 🔮 Future Improvements
- Add time-based features using rolling windows
- Integrate customer feedback or ratings
- Deploy the model as a REST API
- Add monitoring and retraining pipeline (MLOps)

---

## 🧠 Key Learnings
- Real-world ML problems rarely come with clean labels
- Feature engineering often has more impact than model choice
- Business context is critical for model evaluation

---

## 📬 Contact
**Parthiban Subbaiyan**  
Applied Machine Learning Engineer  
🔗 LinkedIn: https://www.linkedin.com/in/parthiban-subbaiyan/

---

⭐ If you find this project useful, feel free to explore or connect.
