# Diabetes Prediction — Machine Learning Capstone

## Project Overview

This project develops a binary classification model to predict whether a patient is diagnosed with diabetes using demographic, lifestyle, and health-related features.

The project was developed as a machine-learning capstone using the Kaggle **Playground Series S5E12 — Diabetes Prediction** dataset.

**Kaggle competition:** https://www.kaggle.com/competitions/playground-series-s5e12

## Objective

The main objective is to build a machine-learning workflow that:

- explores the dataset and checks data quality
- prepares numerical and categorical features
- scales numerical variables
- one-hot encodes categorical variables
- trains an XGBoost classifier
- tunes model hyperparameters using `HalvingRandomSearchCV`
- evaluates the model using classification metrics and ROC-AUC
- generates predictions for the separate test dataset

## Dataset

The training dataset contains **700,000 rows and 26 columns**, including the target variable `diagnosed_diabetes`.

The project removes the `id` column before modeling because it is an identifier rather than a predictive feature.

### Feature groups

**Categorical features**
- gender
- ethnicity
- education_level
- income_level
- smoking_status
- employment_status

**Numerical / binary health features**
- age
- alcohol_consumption_per_week
- physical_activity_minutes_per_week
- diet_score
- sleep_hours_per_day
- screen_time_hours_per_day
- bmi
- waist_to_hip_ratio
- systolic_bp
- diastolic_bp
- heart_rate
- cholesterol_total
- hdl_cholesterol
- ldl_cholesterol
- triglycerides
- family_history_diabetes
- hypertension_history
- cardiovascular_history

**Target**
- `diagnosed_diabetes`

The dataset files are intentionally not included in this repository because the original training and test files are large. Download them from the Kaggle competition page and place them in the `data/` directory.

## Machine Learning Workflow

```text
Raw Data
   ↓
Data Quality Checks
   ↓
Remove ID
   ↓
EDA
   ↓
Train / Validation Split
   ↓
Feature Preprocessing
   ├── StandardScaler for numerical features
   └── OneHotEncoder for categorical variables
   ↓
XGBoost Classifier
   ↓
HalvingRandomSearchCV
   ↓
Model Evaluation
   ├── Classification Report
   ├── Confusion Matrix
   └── ROC-AUC
   ↓
Test Dataset Prediction
```

## Model

The project uses **XGBoost (`XGBClassifier`)**.

Hyperparameter search was performed with `HalvingRandomSearchCV` using **ROC-AUC** as the scoring metric and 4-fold cross-validation.

The selected estimator recorded in the notebook used:

| Parameter | Selected value |
|---|---:|
| `n_estimators` | 10000 |
| `max_depth` | 3 |
| `min_child_weight` | 7 |
| `learning_rate` | 0.05 |
| `subsample` | 0.8 |
| `colsample_bytree` | 0.8 |
| `n_jobs` | -1 |

## Results

The notebook reports the following evaluation results:

| Metric | Result |
|---|---:|
| Accuracy | 0.68 |
| ROC-AUC | 0.7283 |
| Diabetes-class precision | 0.71 |
| Diabetes-class recall | 0.83 |
| Diabetes-class F1-score | 0.77 |

The notebook also reports:

- Train ROC-AUC: **0.7545**
- Test ROC-AUC: **0.7283**

### Classification report

```text
              precision    recall  f1-score   support

         0.0       0.61      0.44      0.51     52739
         1.0       0.71      0.83      0.77     87261

    accuracy                           0.68    140000
   macro avg       0.66      0.64      0.64    140000
weighted avg       0.67      0.68      0.67    140000
```

## Repository Structure

```text
diabetes-prediction-ml/
│
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
│
├── notebooks/
│   └── diabetes_prediction.ipynb
│
├── data/
│   └── README.md
│
├── src/
│   └── README.md
│
├── models/
│   └── README.md
│
├── reports/
│   ├── model_results.md
│   └── figures/
│
└── submission/
    └── README.md
```

## Installation

```bash
git clone https://github.com/YOUR_USERNAME/diabetes-prediction-ml.git
cd diabetes-prediction-ml
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Dataset Setup

1. Open the Kaggle competition page:
   https://www.kaggle.com/competitions/playground-series-s5e12
2. Download the competition data.
3. Put the files in the `data/` directory.
4. Open `notebooks/diabetes_prediction.ipynb`.
5. Update file paths if necessary.
6. Run the notebook from top to bottom.

## Reproducibility Note

The repository contains the original project notebook and documents the model configuration recorded in that notebook.

For a cleaner production implementation, the next step would be to move preprocessing and model training into reusable Python scripts and save the fitted preprocessing/model pipeline as a versioned artifact.

## Limitations and Future Improvements

Potential next steps include:

- broader and more efficient hyperparameter tuning
- comparing XGBoost with additional classification algorithms
- feature engineering
- threshold optimization
- model interpretability using feature importance or SHAP
- calibration and probability analysis
- creating a reusable inference pipeline
- adding automated tests
- deploying the model through an API or interactive application

## Disclaimer

This is an educational machine-learning project. It is not a medical diagnostic system and should not be used to make clinical decisions.

## Author

**HARSHIT**

Machine Learning / Data Science Portfolio Project
