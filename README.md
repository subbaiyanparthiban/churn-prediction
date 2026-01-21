# 📉 Customer Churn Prediction – Food Delivery Platform  
*(Using Food Delivery Order History Dataset)*

---

## 🚀 Project Overview
Customer churn is a critical challenge for online food delivery platforms, especially when customers gradually reduce engagement after promotions or discounts expire.

This project simulates an **internal applied machine learning initiative** to **predict customers likely to churn in the next 30 days**, using historical food order transaction data.

The solution is built using the **Food Delivery Order History Dataset** from Kaggle and follows **industry-standard churn modeling practices**, including time-based label creation and behavioral feature engineering.

---

## 🎯 Business Problem
> How can we proactively identify customers who are likely to stop ordering so that targeted retention actions can be applied?

### Business Value
- Improves customer lifetime value (CLV)
- Enables personalized offers and loyalty campaigns
- Reduces cost of customer acquisition
- Supports data-driven retention strategies

---

## 📌 Churn Definition
A customer is considered **churned** if:
They place ZERO completed orders in the next 30 days
- The churn label is **derived**, not provided directly
- This mirrors how churn is defined in real production systems

---

## 📊 Dataset Description

### Dataset Source
- **Food Delivery Order History Dataset** (Kaggle)
- Total records: **21,321 orders**
- Granularity: **Order-level data**

### Key Columns Used

| Category | Columns |
|--------|--------|
| Customer | `Customer ID` |
| Order | `Order ID`, `Order Placed At`, `Order Status` |
| Location | `City`, `Subzone` |
| Financial | `Bill subtotal`, `Total`, `Packaging charges` |
| Discounts | `Restaurant discount`, `Gold discount`, `Brand pack discount` |
| Engagement | `Items in order`, `Delivery`, `Distance` |
| Experience | `Rating`, `Review`, `Customer complaint tag` |
| Operations | `KPT duration`, `Rider wait time` |

> ⚠️ Some fields (ratings, reviews, complaints) are sparsely populated and handled carefully during EDA.

---

## 🧠 Feature Engineering Strategy

Features are engineered at the **customer level** using historical order data.

### Behavioral Features
- Total orders per customer
- Orders in last 30 / 60 / 90 days
- Days since last order (recency)
- Average bill amount
- Average number of items per order

### Discount & Pricing Features
- Average discount amount
- Discount usage frequency
- Ratio of discounted orders
- Net spend vs gross bill amount

### Experience & Service Features
- Average delivery time
- Rider wait time statistics
- Order cancellation rate
- Average customer rating (if available)

These features help capture **engagement decay**, **price sensitivity**, and **service experience**, which are strong churn indicators.

---

## 🧪 Modeling Approach

The churn prediction problem is framed as a **binary classification task**.

### Models Used
1. **Logistic Regression** – baseline, interpretable model
2. **Random Forest** – captures non-linear behavior
3. **Gradient Boosting (XGBoost / LightGBM)** – performance-focused model

Multiple models are compared to balance **interpretability vs predictive power**.

---

## 📈 Evaluation Metrics

Churn prediction is an **imbalanced classification problem**, so accuracy alone is not sufficient.

### Primary Metrics
- **ROC-AUC** – overall discrimination ability
- **Recall (Churn = 1)** – ability to identify at-risk customers
- **Precision–Recall trade-off** – cost-sensitive evaluation

> Missing a churner is typically more expensive than targeting a non-churner.

---

## 📂 Project Structure

- **data/**
  - **raw/** – Original dataset (unchanged)
  - **processed/** – Cleaned and feature-engineered data
- **notebooks/**
  - **01_eda.ipynb** – Exploratory Data Analysis
  - **02_feature_engineering.ipynb** – Feature creation
  - **03_modeling.ipynb** – Model training and evaluation
- **src/**
  - **preprocessing.py** – Data cleaning and transformations
  - **train.py** – Model training pipeline
  - **evaluate.py** – Model evaluation and metrics
- **README.md** – Project documentation
- **requirements.txt** – Python dependencies

---

## 💼 Business Use Case

The model output can be used to:
- Identify high-risk customers proactively
- Trigger personalized retention offers
- Optimize loyalty and discount strategies
- Improve repeat order rate

Example:
> Retaining even a small percentage of high-risk users can significantly improve revenue and platform engagement.

---

## ⚠️ Assumptions & Limitations
- Dataset is a proxy for production data
- Predictions are generated in batch mode
- External factors (competitor offers, app UX changes) are not included
- Some engagement signals are sparsely populated

These limitations are documented to keep the project **transparent and interview-safe**.

---

## 🔮 Future Improvements
- Add rolling time-window features
- Incorporate customer lifecycle stages
- Deploy model as an API
- Add monitoring and retraining pipeline (MLOps)

---

## 🧠 Key Learnings
- Churn labels often need to be engineered
- Behavioral features outperform raw demographics
- Business context is essential for evaluation

---

## 📬 Contact
**Parthiban Subbaiyan**  
Applied Machine Learning Engineer  
🔗 LinkedIn: https://www.linkedin.com/in/parthiban-subbaiyan/

---

⭐ Feel free to explore the notebooks and reach out for discussion.
