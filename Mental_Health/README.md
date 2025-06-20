# 🧠 Mental Health Prediction – Depression Detection Competition

This project addresses the prediction of depression from survey-based data generated by a deep learning model trained on the [Depression Survey/Dataset for Analysis](https://www.kaggle.com/datasets). The objective is to build a high-performing classifier using psychological, demographic, and lifestyle indicators.

---

## 📄 Dataset Overview

The dataset contains responses to a mental health survey and includes attributes such as academic pressure, job satisfaction, sleep patterns, and more. The target variable is binary: `Depression` (1 for positive indication of depression, 0 otherwise).

- **Training Samples**: 140,700
- **Test Samples**: 93,800

---

## 🧠 Approach

### 1. 🛠️ Manual Feature Engineering (manual.ipynb)
- Filling null values
- Mapping `Gender`, `Working Professional or Student`, 
`Have you ever had suicidal thoughts ?`, and `Family History of Mental Illness`
- Mapping `Sleep Duration`, `Profession`, `Dietary Habits`, and `Degree` through sorting and binning the different unique answers.
- Feature enrichments:
  - `CityCrimeRate` from NCRB data
  - `CityFreq` (frequency of each city)
- Used `XGBoostClassifier` with Optuna-tuned hyperparameters 

### 2. 🔁 ColumnTransformer Pipeline
- Standard scaling for numerical features
- One-hot encoding for categorical variables
- Simple imputation for missing values
- Used `XGBoostClassifier` with Optuna-tuned hyperparameters 

---

## 🧪 Model & Results

| Pipeline Type       | CV Accuracy | Test Accuracy |
|---------------------|-------------|---------------|
| Manual Features     | 93.93%      | 94.02%        |
| ColumnTransformer   | 93.97%      | 94.07%        |

> Final submission used the **ColumnTransformer pipeline** due to its superior generalization performance.

---

Built by Kaizen Rowe