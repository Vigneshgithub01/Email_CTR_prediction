# 📧 Email Campaign Click-Through Rate (CTR) Prediction

## 📌 Project Overview

This project focuses on analyzing and improving an **email marketing campaign** for an e-commerce company. The goal is to **predict which users are most likely to click on a link inside the email**, and suggest a smarter way of targeting them in future campaigns.

> 🔍 From raw data to insights, from modeling to impact — this project demonstrates end-to-end data science in action.

---

## 🎯 Business Problem

The marketing team has run an email campaign announcing a new feature. The team now wants to:

1. Understand **what percentage of users opened and clicked** the email.
2. Build a **predictive model** to identify users who are most likely to click.
3. Estimate how much **CTR can improve** by targeting only the top users.
4. Find **interesting patterns** across user segments (country, weekday, time, etc.).

---

## 🧾 Dataset Details

The project uses **three datasets**:

| Dataset               | Description                                      |
|-----------------------|--------------------------------------------------|
| `email_table.csv`     | Base data of users with email attributes         |
| `email_opened_table.csv` | Subset of users who opened the email        |
| `link_clicked_table.csv` | Subset of users who clicked the link         |

From these, two key target columns are engineered:
- `opened`: Whether the user opened the email (1/0)
- `clicked`: Whether the user clicked the link (1/0) → **Target variable**

---

## 🔧 Tech Stack

- **Language**: Python  
- **Tools**: Jupyter/Colab, Pandas, Scikit-learn, XGBoost, Matplotlib, Seaborn  
- **Libraries**: imbalanced-learn, GridSearchCV, SMOTE  

---

## 🧠 Key Steps Performed

### 1. 🔍 Exploratory Data Analysis (EDA)
- Visualized click rate across categorical features (e.g., content type, weekday)
- Analyzed distributions and outliers in numeric features (e.g., send hour, past purchases)
- Checked **class imbalance** (clicked: very few 1s)
- Correlation matrix and boxplots to understand feature impact

### 2. 📊 Preprocessing
- One-hot encoded categorical variables
- Scaled numeric columns
- Used `ColumnTransformer` + `Pipeline` for clean preprocessing

### 3. 🤖 Model Building & Comparison
Models used:
- **Logistic Regression**
- **Random Forest**
- **XGBoost**

Each model was trained with:
- Original imbalanced data
- Oversampled data (SMOTE)
- Undersampled data (RandomUnderSampler)

### 4. 🔧 Hyperparameter Tuning
- Used `GridSearchCV` to fine-tune model parameters
- Evaluated F1 score as scoring metric

### 5. 🧮 Threshold Tuning
- Adjusted threshold from 0.5 → 0.1 for **Logistic Regression**
- Compared how precision, recall, F1 changed
- Found 0.3 threshold to offer best **balance of recall and false positives**

### 6. 📈 CTR Improvement Analysis
- Sorted test users by predicted probability
- Calculated actual CTR for **top 10%, 20%, 30%** most likely users
- Compared this to overall CTR
- Result: **CTR improved up to 80%** when targeting top users only!

---

## 📊 Evaluation Metrics

Each model was evaluated on:
- **Accuracy**
- **Precision**
- **Recall**
- **F1 Score**
- **ROC AUC Score**
- **Confusion Matrix**
- **Threshold-based performance**

All results were stored in dataframes and visualized for comparison.

---

## ✅ Final Results

- **Best Model**: Logistic Regression (SMOTE + tuned + threshold 0.3)
- **CTR Improvement**:  
  - Top 10% Users: CTR ↑ ~80%  
  - Top 20% Users: CTR ↑ ~60%  
  - Top 30% Users: CTR ↑ ~40%
- **Business Impact**: Instead of emailing everyone, the company can now **target fewer users with higher ROI**.

---


