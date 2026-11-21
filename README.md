# Heart Disease Prediction Using Machine Learning

## Project Overview

This project develops and evaluates machine learning models for predicting the presence of heart disease using clinical and demographic data from the UCI Machine Learning Repository.

The objective is to investigate how supervised machine learning algorithms can classify patients based on clinical measurements and compare their predictive performance.

Two classification algorithms were implemented:
- Logistic Regression
- Random Forest Classifier

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Biopython (not used in this project)
- Joblib

## Dataset

**Source:** [UCI Heart Disease Dataset](https://archive.ics.uci.edu/dataset/45/heart+disease)

The project uses the 303-record processed Cleveland heart disease dataset.

The dataset contains:
- 303 patient records
- 13 predictor variables
- 1 target variable

Clinical and demographic variables include age, sex, chest pain type, resting blood pressure, serum cholesterol, maximum heart rate, exercise-induced angina and other cardiovascular measurements.

The original target variable contains values from 0 to 4. It was converted into a binary classification target:

- 0: No heart disease
- 1: Heart disease present (original target values 1–4)

## Methodology

### 1. Data Inspection and Cleaning

- Examined dataset structure and statistical summaries.
- Identified six missing values across the `ca` and `thal` variables.
- Confirmed that no duplicate records were present.
- Used median imputation for numerical features and most-frequent imputation for categorical features.

### 2. Exploratory Data Analysis

Performed exploratory analysis using:
- Distribution plots
- Age distribution analysis
- Correlation heatmaps

### 3. Data Preprocessing

- Classified predictor variables into numerical and categorical groups.
- Applied standard scaling to numerical features.
- Applied one-hot encoding to categorical features.
- Used Scikit-learn pipelines to integrate preprocessing and modelling.
- Split the data into 80% training and 20% testing, using stratification.

### 4. Model Development

Implemented two supervised machine learning algorithms:

**Logistic Regression**

Used as a baseline classification model.

**Random Forest Classifier**

Used as a tree-based ensemble model for comparison.

### 5. Model Evaluation

Evaluated both models using:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion matrices
- ROC curves

Five-fold stratified cross-validation was also performed to assess model performance across different data splits.

Permutation importance was used to investigate the contribution of individual features to predictive performance.

## Results

### Test Set Performance

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Accuracy | 88.52% | 88.52% |
| Precision | 83.87% | 83.87% |
| Recall | 92.86% | 92.86% |
| F1-score | 88.14% | 88.14% |
| ROC-AUC | 96.65% | 94.05% |

### Five-Fold Cross-Validation

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Mean Accuracy | 85.47% | 84.17% |
| Mean F1-score | 83.32% | 82.14% |
| Mean ROC-AUC | 91.88% | 91.56% |
| ROC-AUC Standard Deviation | 0.0207 | 0.0208 |

Logistic Regression achieved slightly higher mean performance across all three cross-validation metrics.

The difference between the models was relatively small, so the results do not establish definitive superiority.

### Feature Importance

Permutation importance identified the following leading predictive features for Logistic Regression:

1. `ca` – Number of major vessels identified by fluoroscopy.
2. `cp` – Chest pain type.
3. `oldpeak` – ST depression induced by exercise relative to rest.
4. `slope` – Slope of the peak exercise ST segment.
5. `thal` – Thalassemia-related test category.

The `ca` and `cp` variables also ranked highly in the Random Forest analysis.

These findings describe predictive contributions within the fitted models and should not be interpreted as causal relationships.

## Conclusion

Both models achieved comparable classification performance on the held-out test set.

Logistic Regression was selected as the preferred model based on its slightly higher mean accuracy, F1-score and ROC-AUC during five-fold cross-validation.

The project demonstrates an end-to-end machine learning workflow involving clinical data preprocessing, exploratory analysis, model development, performance evaluation and feature importance analysis.

## Limitations

- The dataset contains only 303 records.
- The evaluation uses a relatively small held-out test set.
- The five-fold cross-validation results may vary with different data splits.
- The dataset is historical and does not represent a contemporary, diverse clinical population.
- No external validation was performed.
- Feature importance does not establish causation.

**This project is intended for educational and research purposes. The models are not clinically validated and should not be used for medical diagnosis or treatment decisions.**

## Author

Richard Obayemi

## Project Structure

heart-disease-prediction/
│
├── Heart_Disease_Prediction_ML.ipynb
├── README.md
│
├── models/
│   └── heart_disease_model.pkl
│
└── results/
    ├── model_comparison.csv
    ├── cross_validation_results.csv
    └── feature_importance.csv
```
