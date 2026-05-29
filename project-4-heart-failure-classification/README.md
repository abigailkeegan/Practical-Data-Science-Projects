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
| Logistic Regression | 0.633    | 1.000     | 0.849   |
| Decision Tree       | 0.767    | 0.789     | 0.805   |
| Random Forest       | 0.750    | 0.857     | 0.840   |
| XGBoost             | 0.750    | 0.813     | 0.847   |

*Values reflect the run captured in the committed notebook outputs.*

**The four models perform competitively on AUC-ROC.** Logistic Regression edges out the ensembles (0.849), with XGBoost (0.847) and Random Forest (0.840) within a hair, and Decision Tree (0.805) trailing. On accuracy the tree-based models lead, with the Decision Tree highest at 76.7%. Across all models the most predictive features are consistently `time` (follow-up period), `serum_creatinine`, and `ejection_fraction`.

## Structure

    project-4-heart-failure-classification/
    ├── README.md
    ├── requirements.txt
    ├── data/
    │   └── heart_failure_clinical_records_dataset.csv
    └── notebooks/
        └── heart_failure_classification.ipynb
## Setup

From this subfolder:

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab notebooks/heart_failure_classification.ipynb
```

The notebook loads the dataset with a relative path (`../data/heart_failure_clinical_records_dataset.csv`), so launch Jupyter from this subfolder.

## Dataset citation

Chicco, D., Jurman, G. (2020). *Machine learning can predict survival of patients with heart failure from serum creatinine and ejection fraction alone.* BMC Medical Informatics and Decision Making, 20(1), 16. [doi:10.1186/s12911-020-1023-5](https://doi.org/10.1186/s12911-020-1023-5)

The dataset is distributed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) and is redistributed here under the same license.
