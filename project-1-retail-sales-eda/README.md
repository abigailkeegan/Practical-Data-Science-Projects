# Project 1: Retail Sales Exploratory Data Analysis

A comprehensive exploratory data analysis of a synthetic retail sales dataset, covering data quality, time-series patterns, seasonality, outlier detection, customer demographics, feature engineering, and feature evaluation via correlation and PCA.

**Authors:** Abigail Keegan, Michelle Ng Du

**Course:** CS 667 Practical Data Science, Pace University

## Overview

This project explores a synthetic retail sales dataset of 1,000 transactions across 2023. The notebook walks through a seven-step EDA workflow:

1. **Dataset selection**: load and preview
2. **Basic EDA**: shape, types, missing values, duplicates, summary statistics
3. **Advanced EDA**: time-series trends, month-day seasonality heatmap, outlier detection (IQR, Z-score, and single-feature Isolation Forest), customer demographics, product preferences, and variable relationships
4. **Feature engineering**: binary flags (Is_Weekend, Is_Q4), rolling averages, exponentially weighted moving averages, and high-spender demographic profiles
5. **Cleaning and transformation**: data integrity check, log transformation to reduce skew, IQR outlier review
6. **Feature evaluation**: correlation heatmap, |Pearson r| ranking against Total Amount, and PCA with scree plot, 2D scatter, and loadings heatmap
7. **Summary**: key findings, business recommendations, and additional data needs

## Key Findings

- **Data quality is clean.** No missing values, no duplicates, and Total Amount equals Quantity × Price per Unit for every row.
- **Q4 leads, Q3 lags.** Monthly peaks fall in May and Nov/Dec; Saturdays have the highest average transaction value (506), Wednesdays the lowest (391).
- **Isolation Forest flagged 18 anomalous days** including both high spikes and low troughs, supporting the use of anomaly detection on smoothed daily sales.
- **Only Price per Unit (r=0.85) and Quantity (r=0.37) correlate meaningfully with Total Amount.** All temporal and categorical features have near-zero individual correlation, which directly motivates the regression study in Project 2.
- **PCA reveals no dominant axis.** Variance is spread across 6 components for 80% and 8 for 95%, with PC1 capturing seasonality, PC2 capturing day-of-week patterns, and PC4 capturing transaction value.

## Structure

    project-1-retail-sales-eda/
    ├── README.md
    ├── requirements.txt
    ├── data/
    │   └── retail_sales.csv
    └── notebooks/
        └── retail_sales_eda.ipynb

## Setup

From this subfolder:

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab notebooks/retail_sales_eda.ipynb
```

The notebook loads the dataset with a relative path (`../data/retail_sales.csv`), so launch Jupyter from this subfolder.

## Dataset

A synthetic retail sales dataset of 1,000 transactions with fields for Transaction ID, Date, Customer ID, Gender, Age, Product Category, Quantity, Price per Unit, and Total Amount.
