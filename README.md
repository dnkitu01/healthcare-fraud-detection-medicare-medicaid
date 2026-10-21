# Medicare Provider Fraud Detection Using Machine Learning

## Project Overview

This independent healthcare analytics project explores how supervised machine learning can identify patterns in Medicare claims associated with providers labeled as potentially fraudulent.

The analysis integrates beneficiary information, inpatient claims, outpatient claims, and provider-level fraud labels to develop and evaluate predictive classification models.

The project focuses on responsible machine learning, data preparation, model evaluation, and the potential application of predictive analytics to healthcare claims integrity.

## Business Problem

Healthcare fraud presents significant financial and operational challenges for Medicare and healthcare organizations.

Traditional fraud investigations can require extensive manual review of claims and provider activity. Machine learning offers opportunities to support fraud risk screening and help prioritize potentially suspicious cases for further investigation.

The objective of this project was to evaluate whether healthcare claims characteristics could help distinguish observations associated with providers labeled as potentially fraudulent.

## Dataset

**Source:** [Healthcare Provider Fraud Detection Analysis — Kaggle](https://www.kaggle.com/datasets/rohitrox/healthcare-provider-fraud-detection-analysis)

The project integrates four training datasets:

- Beneficiary information: 138,556 records
- Inpatient claims: 40,474 records
- Outpatient claims: 517,737 records
- Provider fraud labels: 5,410 records

After combining inpatient and outpatient claims and integrating beneficiary and provider-label information, the analytical dataset contained **558,211 claim-level observations**.

The target variable was derived from provider-level `PotentialFraud` labels. These labels do not independently establish that every associated claim was fraudulent.

## Methodology

### Data Preparation

- Integrated beneficiary, inpatient, and outpatient datasets.
- Attached provider-level potential-fraud labels.
- Handled missing values in selected modeling features.
- Derived beneficiary age and inpatient indicators.
- Excluded provider identifiers from the predictive features to reduce direct identity-based leakage.
- Applied numerical scaling and categorical encoding.

### Machine Learning Models

Two supervised classification algorithms were developed:

1. Logistic Regression
2. Random Forest Classifier

The models were evaluated using a stratified 80/20 claim-level train-test split.

### Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

## Model Results

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Overall Accuracy | 62% | 56% |
| Potential-Fraud Precision | 49% | 41% |
| Potential-Fraud Recall | 16% | 32% |
| Potential-Fraud F1-score | 24% | 36% |
| ROC-AUC | 0.533 | 0.519 |

## Key Findings

**Random Forest achieved higher potential-fraud recall and F1-score**, identifying a larger proportion of observations associated with the potential-fraud class.

However, Logistic Regression achieved higher overall accuracy, precision, and ROC-AUC.

Both models demonstrated limited overall discriminatory performance, highlighting the importance of additional feature engineering and stronger validation.

A key methodological decision involved excluding the `Provider` identifier from the predictive feature set to reduce the risk of memorizing provider identities.

## Project Limitations

- Fraud labels were assigned at the provider level rather than independently verified for individual claims.
- The train-test split was performed at the claim level, meaning records associated with the same provider may have appeared in both training and testing datasets.
- Both models demonstrated limited discriminatory performance.
- The project did not measure prevented fraud, financial savings, or operational deployment outcomes.

Future work should explore provider-disjoint validation, additional feature engineering, alternative algorithms, and explainable AI techniques.

## Potential Healthcare Applications

With additional development and rigorous validation, machine learning approaches such as those explored in this project could potentially support:

- Healthcare claims integrity analysis
- Fraud risk screening
- Investigative case prioritization
- Healthcare utilization monitoring
- Data-driven operational decision-making

The current models are exploratory and should not be used independently to determine whether fraud occurred.

## Tools and Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Jupyter Notebook

## Project Notebook

[View the corrected Jupyter notebook](Medicare_Provider_Fraud_Detection_Corrected.ipynb)

## Dataset Attribution

Original dataset: [Healthcare Provider Fraud Detection Analysis — Kaggle](https://www.kaggle.com/datasets/rohitrox/healthcare-provider-fraud-detection-analysis)

Related Kaggle analysis: [Healthcare Provider Fraud Detection Analysis](https://www.kaggle.com/code/farelarden/healthcare-provider-fraud-detection-analysis)

## Author

**Deborah Kituyi**

Master of Science in Business Analytics  
University of Louisville

Healthcare Analytics | Machine Learning | Predictive Analytics | Healthcare Operations
