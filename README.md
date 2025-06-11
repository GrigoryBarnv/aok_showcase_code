

# ADSL_WS24_AOK_GroupC

## AOK Prognosis Tool – Ambulance Case Prediction

This project was developed during the Applied Data Science Lab (WS24) in collaboration with AOK Baden-Württemberg. It focuses on predicting ambulance-sensitive hospital admissions from nursing homes using real-world healthcare data.

## Project Overview

**Objective**: Predict and reduce unnecessary ambulance-sensitive cases by identifying high-risk patients early.

**Dataset**: Approximately 180,000 anonymized cases from German nursing homes, including ICD diagnoses, medication history, demographics, and care level.

**Target Variable**: Binary label indicating whether a patient visit resulted in an ambulance-sensitive hospital case.

## Machine Learning Models Applied

Three classification models were trained and evaluated:

- Logistic Regression (final model, chosen for its interpretability and robustness)
- Decision Tree
- XGBoost Classifier (high-performing, but more complex)

All models were evaluated using **ROC AUC**, with the final model achieving:

- **Validation AUC > 0.99**
- 5-fold cross-validation was used to ensure generalization

## Feature Engineering

- Grouped ICD codes into chapters using WHO classifications
- Transformed text-based diagnosis and drug histories into numeric variables
- Created aggregated quarterly features (Q1–Q4) for both diagnoses and medication
- Derived additional features: `icd_history`, `drug_history`, and nursing home clusters

## Clustering

- Used the Elbow Method to determine the optimal number of clusters for K-Means
- Grouped nursing homes based on patient age, gender ratio, disease history, and case volume
- Identified distinct patterns across four cluster types:
  - Elder Female
  - Young Male
  - Long Disease History
  - High Volume Nursing Homes

## Variable Selection

- Performed feature importance ranking using:
  - Logistic Regression coefficients
  - XGBoost F-score rankings
- Constructed feature subsets by relevance (e.g., top 10 drugs, ICD chapters)
- Used Lasso regularization to reduce dimensionality and prevent overfitting

## Model Selection

- Compared all models on the same training, validation, and test splits
- Selected Logistic Regression as the final model due to:
  - Strong performance
  - High interpretability (coefficients = impact of features)
  - Low risk of overfitting with regularization

## Prognosis Tool

- Final tool allows case-level or nursing home-level risk prediction
- Outputs ambulance risk probability and top 10 contributing variables
- Designed to support early intervention and resource planning by healthcare providers

## Technologies Used

- Python: pandas, NumPy, scikit-learn, XGBoost
- Visualization: matplotlib, seaborn
- Development: Jupyter Notebook, Git

## Results Summary

- Logistic Regression selected as the optimal model
- High AUC scores across all models
- Transparent and actionable outputs for real-world medical application



![image](https://github.com/user-attachments/assets/c376b203-0203-4a60-a1df-defd47e0202e)

