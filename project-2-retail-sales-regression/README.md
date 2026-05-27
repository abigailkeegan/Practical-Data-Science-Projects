# Project 2: Retail Sales Regression

A regression study investigating how well retail transaction amounts can be predicted from demographic and temporal features alone, deliberately excluding the variables (`Quantity` and `Price per Unit`) that deterministically define the target.

**Authors:** Abigail Keegan, Michelle Ng Du
**Course:** CS 667 Practical Data Science, Pace University

## Overview

This project uses a synthetic retail sales dataset of 1,000 transactions to test how well demographic features (age, gender, product category) and temporal features (month, quarter, day of week) alone can predict `Total Amount`. Because `Total Amount` is exactly equal to `Quantity * Price per Unit` in every row, both of those variables are excluded from the feature set by design, and the project becomes a study in feature insufficiency rather than a prediction success story.

The workflow:

1. **EDA and feature engineering**: date parsing, temporal feature extraction (Month, Quarter, DayOfWeek, Is_Q4), label encoding of Gender, one-hot encoding of Product Category
2. **Preprocessing**: 80/20 train/test split, standard scaling handled per fold via a `Pipeline` for the cross-validated evaluation
3. **Modeling**: Linear Regression, Decision Tree, Random Forest, and Gradient Boosting, each evaluated with both a held-out test set and 5x5 repeated K-fold cross-validation
4. **Tuning**: `GridSearchCV` on Linear Regression and Gradient Boosting, refit on R²
5. **Interpretation**: Random Forest and Gradient Boosting feature importances, residual plots, and actual-vs-predicted scatter plots

## Results

| Model                       | R²      | MAE    | RMSE   |
| --------------------------- | ------- | ------ | ------ |
| Linear Regression           | -0.0134 | 460.11 | 562.53 |
| Decision Tree Regressor     | -1.1396 | 580.75 | 814.58 |
| Random Forest Regressor     | -0.1616 | 482.18 | 601.45 |
| Gradient Boosting Regressor | -0.0716 | 461.79 | 578.37 |

*Cross-validated metrics (5x5 repeated K-fold). Values reflect the run captured in the committed notebook outputs.*

After tuning, Linear Regression reached an R² of -0.0067 and Gradient Boosting reached -0.0108, both still negative.

**The central finding is a negative result.** Every model performs worse than simply predicting the mean of the training set (R² < 0), and tuning narrows the gap without closing it. This confirms that demographic and temporal features alone are insufficient to predict transaction-level `Total Amount` in this dataset. The notebook discusses what this means for feature design and what kinds of features (income bracket, loyalty tier, channel, region, historical spend) would make the problem tractable.

## Structure

    project-2-retail-sales-regression/
    ├── README.md
    ├── requirements.txt
    ├── data/
    │   └── retail_sales.csv
    └── notebooks/
        └── retail_sales_regression.ipynb

## Setup

From this subfolder:

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/retail_sales_regression.ipynb
```

The notebook loads the dataset with a relative path (`../data/retail_sales.csv`), so launch Jupyter from this subfolder.

## Dataset

A synthetic retail sales dataset of 1,000 transactions with fields for Transaction ID, Date, Customer ID, Gender, Age, Product Category, Quantity, Price per Unit, and Total Amount. The dataset is intended for educational use.
