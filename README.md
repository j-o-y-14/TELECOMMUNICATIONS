# Telecom Customer Churn Prediction

**Tagline:** Predicting Which Customers Will Leave, So Telecom Companies Can Keep Them.

## 🔗 Links

- **Dataset:** Telco_customer_churn.xlsx


---

## Overview

Customer churn is one of the biggest revenue risks for telecom companies. Acquiring a new customer costs far more than retaining an existing one, so knowing who is likely to leave is valuable.

This project builds a machine learning pipeline that analyzes customer demographics, services, contract details, and billing information to predict whether a customer will churn. It covers data exploration, preprocessing, class balancing, model training, evaluation, and error analysis.

## Problem Statement

Telecom companies lose customers every month, but the reasons are often hidden in the data. Without a predictive system, retention efforts are reactive and untargeted.

**Goal:** Build and compare classification models that identify customers at risk of churning, and understand which factors drive that decision.

## Research Questions

1. What proportion of customers churn, and is the dataset balanced?
2. How do tenure, monthly charges, and total charges relate to each other and to churn?
3. Which features are the strongest predictors of churn?
4. Do linear or nonlinear models perform better on this data?
5. Where do the models make mistakes, and why?

---

## Dataset

- **Source file:** `Telco_customer_churn.xlsx`
- **Content:** Customer demographics, location, services subscribed, contract type, billing, and churn information.
- **Target variable:** `Churn Value` (1 = churned, 0 = stayed)

---

## System Design

### 1. Data Loading & Inspection
- Loaded the dataset with pandas.
- Inspected shape, data types, missing values, and summary statistics using `head()`, `tail()`, `info()`, `describe()`, and `isnull().sum()`.
- Built a reusable `check_data()` function for a full data summary.

**Tools:** pandas, numpy

### 2. Exploratory Data Analysis (EDA)
- **Heatmap:** Checked multicollinearity between numeric variables.
- **Scatter plot:** Examined the relationship between Tenure Months and Monthly Charges.
- **Histograms:** Examined the distribution of numeric features.
- **Boxplots:** Identified outliers.
- **Countplot:** Checked churn class balance.
- **Pairplot:** Explored relationships between multiple numeric variables.
- **Bar plot:** Compared monthly charges by contract type and churn.

**Tools:** matplotlib, seaborn

### 3. Data Preprocessing
1. **Dropped unneeded columns:** CustomerID, Count, Country, State, City, Zip Code, Lat Long, Latitude, Longitude, Churn Label, Churn Score, Churn Reason.
2. **Fixed data types:** Converted `Total Charges` to numeric and filled missing values with the median.
3. **Handled outliers with Winsorization:** Capped the bottom and top 5% of Tenure Months, Monthly Charges, Total Charges, and CLTV.
4. **Encoded categorical features:** Used Label Encoding on all object columns.
5. **Balanced classes with SMOTE:** Generated synthetic minority-class samples to fix class imbalance, with before/after visualization.
6. **Scaled features:** Applied StandardScaler.
7. **Split the data:** 80% training and 20% testing.

**Tools:** scipy, scikit-learn, imbalanced-learn

### 4. Predictive Modeling

**Linear Models**
- Logistic Regression
- Linear SVM

**Nonlinear Models**
- Decision Tree
- Random Forest
- Gradient Boosting

### 5. Model Evaluation & Diagnostics
- **Metrics:** Accuracy, Precision, Recall, F1 Score, ROC-AUC
- **Confusion matrix** for prediction breakdown
- **Model comparison chart** across all five models
- **ROC curves** for all models on one plot
- **Feature importance** (Random Forest)
- **Correlation matrix** after preprocessing
- **Cross-validation** (5-fold)
- **Validation curve** (Random Forest, `n_estimators`)

### 6. Error Analysis
- Identified misclassified samples.
- Split errors into False Positives and False Negatives.
- Compared feature averages between correct and misclassified predictions.
- Visualized error distribution by Tenure Months.
- Generated a full classification report.

---

## Model Comparison

| Model | Type | Strength |
|---|---|---|
| Logistic Regression | Linear | Simple, interpretable baseline |
| Linear SVM | Linear | Effective with clear class separation |
| Decision Tree | Nonlinear | Easy to visualize, captures interactions |
| Random Forest | Nonlinear | Robust, handles nonlinear relationships |
| Gradient Boosting | Nonlinear | High accuracy through sequential learning |



---

## Project Pipeline

```
Raw Data (Telco_customer_churn.xlsx)
        ↓
Data Loading & Inspection
        ↓
Exploratory Data Analysis (EDA)
        ↓
Preprocessing (Drop Columns → Winsorization → Encoding → SMOTE → Scaling → 80/20 Split)
        ↓
Modeling (2 Linear + 3 Nonlinear Models)
        ↓
Evaluation (Metrics, ROC, Cross-Validation, Validation Curve, Feature Importance)
        ↓
Error Analysis
```

## Tech Stack

- **Language:** Python
- **Data:** pandas, numpy, scipy
- **Visualization:** matplotlib, seaborn
- **Machine Learning:** scikit-learn, imbalanced-learn

## Target Audience

**Telecom Retention & Marketing Teams**
- Why: Target at-risk customers with offers before they leave.
- Needs: Clear churn predictions and the key factors behind them.

**Business & Product Managers**
- Why: Understand which contracts, services, and pricing drive churn.
- Needs: Insights to guide pricing and service decisions.

**Data Scientists & Students**
- Why: A reproducible example of a full classification workflow, from EDA to error analysis.
- Needs: Clean, well-structured, easy-to-follow code.

---

## How to Run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn scipy openpyxl
```

1. Place `Telco_customer_churn.xlsx` in the project folder.
2. Open the notebook in Jupyter.
3. Run the cells in order.
