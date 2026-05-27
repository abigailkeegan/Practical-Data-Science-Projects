
Coursework projects from Pace University's CS 667 Practical Data Science.

**Author:** Abigail Keegan

## Projects

| # | Project | Topic | Status |
|---|---------|-------|--------|
| 1 | [Retail Sales EDA](./project-1-retail-sales-eda) | Exploratory data analysis with time-series, seasonality, outlier detection, log transformation, correlation analysis, and PCA | Complete |
| 2 | [Retail Sales Regression](./project-2-retail-sales-regression) | Regression with Linear Regression, Decision Tree, Random Forest, and Gradient Boosting; a study in feature insufficiency where models trained on demographic and temporal features alone underperform the mean baseline | Complete |
| 3 | [Financial Anomaly Detection](./project-3-financial-anomaly-detection) | Unsupervised anomaly detection comparing Gaussian Mixture Models and Isolation Forest on financial transactions | Complete |
| 4 | [Heart Failure Classification](./project-4-heart-failure-classification) | Classification with Logistic Regression, Decision Tree, Random Forest, and XGBoost; interpretability with ELI5, LIME, and SHAP | Complete |

Each project lives in its own subfolder with a dedicated README, notebook, dataset, and `requirements.txt`.

## Repository structure

```
Practical-Data-Science-Projects/
├── README.md
├── LICENSE
├── .gitignore
├── project-1-retail-sales-eda/
│   ├── README.md
│   ├── requirements.txt
│   ├── data/
│   │   └── retail_sales.csv
│   └── notebooks/
│       └── retail_sales_eda.ipynb
├── project-2-retail-sales-regression/
│   ├── README.md
│   ├── requirements.txt
│   ├── data/
│   │   └── retail_sales.csv
│   └── notebooks/
│       └── retail_sales_regression.ipynb
├── project-3-financial-anomaly-detection/
│   ├── README.md
│   ├── requirements.txt
│   ├── data/
│   │   └── financial_anomaly_data.csv
│   └── notebooks/
│       └── financial_anomaly_detection.ipynb
└── project-4-heart-failure-classification/
    ├── README.md
    ├── requirements.txt
    ├── data/
    │   └── heart_failure_clinical_records_dataset.csv
    └── notebooks/
        └── heart_failure_classification.ipynb
```

## Running a project locally

Each project has its own dependencies. From the project's subfolder:

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/
```

## License

Code in this repository is released under the MIT License. See [LICENSE](LICENSE). Individual datasets retain their original licenses, noted in each project's README.
