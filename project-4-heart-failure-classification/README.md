# Project 4: Heart Failure Classification

Predicting patient mortality from clinical records using four classification algorithms (Logistic Regression, Decision Tree, Random Forest, XGBoost) with hyperparameter tuning and model interpretability via ELI5, LIME, and SHAP.

**Authors:** Abigail Keegan, Michelle Ng Du
**Course:** CS 667 Practical Data Science, Pace University

## Overview

This project uses the [Heart Failure Clinical Records dataset](https://archive.ics.uci.edu/dataset/519/heart+failure+clinical+records) (Chicco & Jurman, 2020) to predict the `DEATH_EVENT` outcome from 12 clinical features collected for 299 patients with heart failure.

The workflow:

1. **EDA** with correlation heatmaps, histograms, and boxplots stratified by outcome
2. **Preprocessing**: standard scaling of quantitative features, 80/20 train/test split, stratified 5-fold CV
3. **Modeling**: Logistic Regression, Decision Tree, Random Forest, and XGBoost, each tuned with `GridSearchCV` on `roc_auc`
4. **Interpretability**:
   * ELI5 for the white-box models (Logistic Regression coefficients, Decision Tree feature importances, per-prediction explanations)
   * LIME for the black-box models (Random Forest, XGBoost)
   * SHAP TreeExplainer for XGBoost (force plots and summary plots)
5. **Comparison**: per-sample probability predictions and a final accuracy / precision / AUC-ROC table across all four models

## Results

| Model               | Accuracy | Precision | AUC-ROC |
| ------------------- | -------- | --------- | ------- |
| Logistic Regression | 0.633    | 0.500     | 0.891   |
| Decision Tree       | 0.733    | 0.667     | 0.738   |
| Random Forest       | 0.767    | 0.769     | 0.837   |
| XGBoost             | 0.733    | 0.667     | 0.840   |

*Values reflect the run captured in the committed notebook outputs.*

**Random Forest and XGBoost are the strongest models.** XGBoost has the best AUC-ROC, meaning it ranks patients by death risk more reliably than the others. Across all models the most predictive features were consistently `time` (follow-up period), `serum_creatinine`, and `ejection_fraction`.

## Structure

```
project-4-heart-failure-classification/
├── README.md
├── requirements.txt
├── data/
│   └── heart_failure_clinical_records_dataset.csv
└── notebooks/
    └── heart_failure_classification.ipynb
```

## Setup

From this subfolder:

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/heart_failure_classification.ipynb
```

The notebook loads the dataset with a relative path (`../data/heart_failure_clinical_records_dataset.csv`), so launch Jupyter from this subfolder.

## Dataset citation

Chicco, D., Jurman, G. (2020). *Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone.* BMC Medical Informatics and Decision Making, 20(1), 16. [doi:10.1186/s12911-020-1023-5](https://doi.org/10.1186/s12911-020-1023-5)

The dataset is distributed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) and is redistributed here under the same license.
