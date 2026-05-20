# Practical Data Science Projects

Coursework projects from Pace University's CS 667 Practical Data Science.

**Author:** Abigail Keegan

## Projects

| # | Project | Topic | Status |
|---|---------|-------|--------|
| 1 | *(TBD)* | *(TBD)* | Not yet uploaded |
| 2 | *(TBD)* | *(TBD)* | Not yet uploaded |
| 3 | *(TBD)* | *(TBD)* | Not yet uploaded |
| 4 | [Heart Failure Classification](./project-4-heart-failure-classification) | Classification with Logistic Regression, Decision Tree, Random Forest, and XGBoost; interpretability with ELI5, LIME, and SHAP | Complete |

Each project lives in its own subfolder with a dedicated README, notebook, dataset, and `requirements.txt`.

## Repository structure

```
Practical-Data-Science-Projects/
├── README.md
├── LICENSE
├── .gitignore
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
