# Predicting Late Deliveries in E-Commerce (Olist Dataset)

## 📌 Overview

Late deliveries negatively impact customer satisfaction and operational efficiency in e-commerce.

This project aims to:
- Predict whether an order will be delivered late
- Understand key drivers behind delivery delays
- Explore trade-offs between recall and precision in real-world decision-making

---

## 📊 Dataset

- Source: Brazilian E-Commerce Public Dataset by Olist (https://www.kaggle.com/datasets/enzoschitini/brazilian-e-commerce-public-dataset-by-olist)
- ~95,000 orders after preprocessing
- Aggregated to **order-level** (one row per order)

---

## ⚙️ Approach

### Data Preparation
- Converted multi-item orders into single order-level records
- Cleaned and processed timestamp features

### Feature Engineering
Key features include:
- `approval_time_hours` → processing delay before shipment
- `estimated_delivery_days` → expected delivery window
- `freight_ratio` → proxy for shipping complexity
- `delivery_pressure` → tightness of delivery timeline
- `is_peak_month` → seasonality indicator

---

## 🤖 Modeling

Models evaluated:
- Logistic Regression (baseline)
- Random Forest
- XGBoost (final model)

| Model                | ROC-AUC |
|---------------------|--------|
| Logistic Regression | ~0.74  |
| Random Forest       | ~0.77  |
| XGBoost             | ~0.78  |

Tree-based models significantly outperformed linear models, indicating non-linear relationships in the data.

---

## 📈 Results

Final model: **XGBoost**

- ROC-AUC: ~0.79
- Precision (late): ~0.33 (at threshold 0.70)
- Recall (late): ~0.36

The model performs better as a **risk ranking tool** rather than a strict classifier.

---

## 🎯 Threshold Strategy

Instead of using the default threshold (0.5), we tuned the decision threshold.

At threshold ≈ 0.70:
- Reduced false positives significantly
- Maintained usable recall
- Produced more actionable predictions

---

## 🔍 Key Insights

- Delivery delays are strongly influenced by **seasonality (month)**
- Tight delivery windows increase delay risk
- Logistic complexity (freight, product size) contributes to delays
- Feature engineering had more impact than model selection in early stages

---

## ⚠️ Limitations

- No geographic distance data
- No carrier-level performance data
- Limited seller behavioral features

These factors likely constrain model performance.

---

## 🚀 Future Work

- Incorporate external data (e.g., holidays, geographic distance)
- Improve seller-level historical features (without leakage)
- Deploy model as a real-time risk scoring system

---

## 🧠 Key Takeaway

This project highlights that:

> Data science is not about perfect predictions,  
> but about making better decisions under uncertainty.

---

## 📂 Repository Structure
