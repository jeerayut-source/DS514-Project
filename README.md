# Retail Transaction Analysis & Price Prediction (Regression Project)

This project analyzes a retail transaction dataset and builds a Regression model to predict the purchase amount for each transaction. The analysis focuses on how product categories, discount usage, quantity, and payment methods influence transaction value, using only the actual features available in the dataset (no synthetic or invented data).

---

## 📌 1. Project Overview

This project performs:

- Data Cleaning  
- Exploratory Data Analysis (EDA)  
- Feature Engineering (lightweight, only from real columns)  
- Regression modeling to predict transaction price  
- Business interpretation of model outputs  

The objective is to understand **what factors drive transaction value** and **how each input variable affects customer spending behavior**.

---

## 📌 2. Dataset Description

The dataset contains retail transactions with the following usable columns:

### **Available Features**
- **Category** – Product category (e.g., Clothing, Shoes, Accessories)  
- **Price** – Total amount of the transaction → *used as the target variable*  
- **Quantity** – Number of items purchased in that transaction  
- **Discount Flag** – Whether the transaction used a discount (Yes/No)  
- **Payment Method** – Payment type used (e.g., Cash, Card, Wallet)

### **What the dataset does NOT include**
- No customer ID  
- No timestamps or dates  
- No discount percentage  
- No repeat customer behavior  

All analysis and modeling respect these limitations without fabricating missing data.

---

## 📌 3. Project Goal

### 🎯 **Predict transaction price using Regression.**

By predicting the purchase amount, the project aims to answer:

- Which factors increase or decrease transaction value?  
- Does using a discount correspond to higher or lower spending?  
- Which product categories are associated with high-value transactions?  
- Do different payment methods correlate with different spending levels?  

Linear Regression was chosen due to:
- Interpretability  
- Simplicity  
- Appropriateness for small-to-medium datasets  
- Clear coefficient meaning for business insights  

---

## 📌 4. Features & Target

### 🎯 **Target Variable**
- `Price` (continuous numeric value)

### 🧱 **Features Used**
| Feature | Type | Reason |
|--------|------|--------|
| Category | Categorical (one-hot) | Strong determinant of price |
| Quantity | Numeric | Influences total price directly |
| Discount_Flag | Binary (0/1) | Indicates promotional behavior |
| Payment_Method | Categorical (one-hot) | May correlate with customer purchasing power |

These features come **directly from the dataset** with no artificial fields.

---

## 📌 5. Methodology

### **1. Data Cleaning**
- Handling missing values  
- Converting categorical fields into machine-readable format  
- Converting discount flag to binary (0 = No, 1 = Yes)

### **2. Exploratory Data Analysis**
- Price distribution  
- Category vs. average price  
- Effect of discount usage  
- Relationship between payment methods and price  

### **3. Feature Engineering**
- One-hot encoding for categorical variables  
- Minimal transformations to preserve original data integrity

### **4. Modeling**
- Linear Regression (baseline model)  
- Train/Test split  
- Model evaluation using:
  - MAE (Mean Absolute Error)  
  - RMSE  
  - R² Score  
  - Residual plots

### **5. Business Interpretation**
- Coefficient analysis to identify variables with the strongest impact on price  
- Comparison between discount vs. non-discount transactions  
- Category-level price sensitivity insights  

---

## 📌 6. Key Insights from Analysis

- **Clothing** contributes the majority of total sales volume.  
- **Accessories** show higher average prices compared to other categories.  
- **Discount usage does not increase transaction value** — customers who do *not* use discounts often spend more.  
- **Payment methods show minimal price differences**, suggesting channel neutrality.  
- No strong seasonality was detected since the dataset contains no date information.  

These insights support pricing strategy optimization and discount policy evaluation.

---

## 📊 7. Model Performance — Logistic Regression

A Logistic Regression classifier was trained to predict customer membership status  
(Member = 1, Not Member = 0).  
Below are the evaluation results obtained from the final model.

---

### ✔ Overall Accuracy
- **Accuracy:** **83%**

This indicates that the model correctly predicts membership status for **83% of all transactions**.

---

## 📌 Classification Report

| Class | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| **0 – Not Member** | 1.00 | 0.76 | 0.86 | 558 |
| **1 – Member**     | 0.62 | 0.99 | 0.76 | 222 |

- **Macro Avg F1-score:** 0.81  
- **Weighted Avg F1-score:** 0.83  

---

### 🔍 Interpretation of Metrics

**Class 0 – Not Member**  
- Precision = **1.00** → Every time the model predicts “Not Member,” it is always correct.  
- Recall = **0.76** → The model identifies 76% of actual non-members.

**Class 1 – Member**  
- Precision = **0.62** → Some “Member” predictions are incorrect (false positives).  
- Recall = **0.99** → Almost all real members are detected (very few false negatives).  

📌 **Implication:**  
- The model is **excellent at detecting actual Members** (high recall).  
- But it occasionally predicts Member when the person is actually Not Member (lower precision).

This behavior is common when the model prioritizes finding positives (members) instead of avoiding false alarms.

---

## 📌 Confusion Matrix Interpretation

The confusion matrix below summarizes prediction performance:

| Actual ↓ / Predicted → | Not Member (0) | Member (1) |
|------------------------|----------------|------------|
| **Not Member (0)**     | 424            | 134        |
| **Member (1)**         | 2              | 220        |

### ✔ Key Insights

- **424** Not Members correctly classified  
- **220** Members correctly classified  
- **134** Not Members misclassified as Members  
- Only **2** actual Members were missed by the model (excellent)

📌 The model shows **very low false negatives** for Members → useful if “missing a Member” is costly.

---

## ⭐ Overall Performance Summary

Logistic Regression achieved:  
- Strong recall for Member detection  
- Perfect precision for Not Member  
- Balanced F1-scores across classes  
- Solid overall accuracy (83%)  

This makes it a reliable baseline model for membership prediction, especially in scenarios where detecting actual members is more important than avoiding occasional false-positive predictions.


---
