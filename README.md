# Machine Learning Models with Explainable AI for Preoperative Frailty Risk Prediction

This repository contains the implementation and methodology for the research study:

> **"Machine Learning Models with Explainable AI for Preoperative Frailty Risk Prediction in Elderly Patients with Hepatocellular Carcinoma"**
> Published in IEEE Xplore.

<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/c12f42de-e194-4325-8dd2-72b96c7406ec" />

---

## Overview

This study addresses the problem of predicting preoperative frailty risk in elderly patients diagnosed with hepatocellular carcinoma (HCC). Frailty assessment is a critical factor in surgical decision-making, yet traditional approaches often fail to capture patient-specific risk profiles.

To address this limitation, we developed and evaluated a machine learning framework for identifying high-risk patients using structured clinical data from a tabular dataset (`Frailty Dataset.xlsx`). We benchmarked multiple machine learning models across different configurations and incorporated SHAP-based explainable AI to ensure clinical interpretability of predictions.

---

## Key Contributions

### Machine Learning Pipeline
- End-to-end preprocessing and modeling pipeline
- IQR-based outlier capping for continuous clinical features
- One-hot encoding for nominal features; ordinal encoding for categorical features
- Feature scaling using `StandardScaler`
- 70/30 stratified train-test split

### Feature Selection
- Recursive Feature Elimination (RFE) using a `RandomForestClassifier` base estimator
- Models evaluated both with and without RFE-selected features

### Model Benchmarking
- 8 classifiers evaluated across 4 configurations (vanilla vs. tuned × without RFE vs. with RFE) — **32 model experiments** in total
- Models: Logistic Regression, SVM, k-Nearest Neighbors, Random Forest, XGBoost, LightGBM, Naive Bayes, Decision Tree
- Hyperparameter tuning via `GridSearchCV` with 5-fold cross-validation, optimizing for F1-score

### Explainable AI (XAI)
- SHAP analysis (`shap.TreeExplainer`) applied to the best-performing model: **LightGBM with RFE-selected features**
- Waterfall plots for individual low-risk and high-risk case explanations
- Global feature importance via SHAP bar and beeswarm plots

---

## Tech Stack

- **Language:** Python
- **Machine Learning:** Scikit-learn, XGBoost, LightGBM
- **Explainable AI:** SHAP
- **Data:** `Frailty Dataset.xlsx` (tabular clinical data)
- **Environment:** Jupyter Notebook (tested on Google Colab)

---

## Installation

Install dependencies:

```bash
pip install pandas seaborn matplotlib numpy scikit-learn xgboost lightgbm shap openpyxl
```

The notebook also includes a cell that automatically checks for and installs any missing packages on first run.

---

## Publication

The full paper is available on IEEE Xplore:
[https://doi.org/10.1109/AIMLA67915.2026.11522435](https://doi.org/10.1109/AIMLA67915.2026.11522435)

---

## Notes

- This repository reflects the methodology described in the published study.
- The dataset (`Frailty Dataset.xlsx`) is not included in this repository due to privacy restrictions.
- Some preprocessing details may differ slightly from the paper due to anonymization requirements.
