# Abalone Age Prediction with Machine Learning Regressors

Predicting the age of abalone from physical measurements.  The age of
abalone is determined by cutting the shell through the cone, staining it,
and counting the number of rings through a microscope -- a boring and
time-consuming task.  Other measurements, which are easier to obtain, are
used to predict the age.  Further information, such as weather patterns
and location (hence food availability) may be required to solve the problem.

---

## 📄 About the Dataset

From the original data examples with missing values were removed (the
majority having the predicted value missing), and the ranges of the
continuous values have been scaled for use with an ANN (by dividing by 200).

Data comes from an original (non-machine-learning) study:

Warwick J Nash, Tracy L Sellers, Simon R Talbot, Andrew J Cawthorn and
Wes B Ford (1994) "The Population Biology of Abalone (_Haliotis_
species) in Tasmania. I. Blacklip Abalone (_H. rubra_) from the North
Coast and Islands of Bass Strait", Sea Fisheries Division, Technical
Report No. 48 (ISSN 1034-3288)

📚 Original dataset: [UCI Abalone Dataset](https://archive.ics.uci.edu/ml/datasets/abalone)

---

## 🧠 Models Used

Here are the models trained and their hyperparameters.

- **SGDRegressor (Default)**: penalty: `'l2'`, alpha: `0.0001`, loss: `'squared_error'`
- **SGDRegressor (Tuned)**: penalty: `'l1'`, alpha: `0.00105`, loss: `'squared_error'`
- **XGBoost Regressor (Default)**: default parameters
- **XGBoost Regressor (Tuned)**: learning_rate: `0.05`, max_depth: `3`, n_estimators: `200`, colsample_bytree: `0.8`, subsample: `0.8`
- **Random Forest Regressor (Default)**: n_estimators: `100`, max_depth: `None`

---

## 🔧 Preprocessing

- Create age column by adding 1.5 to the rings column
- Removed outliers
- One-hot encoded the categorical `Sex` feature
- Standardized numerical features using `StandardScaler`
- Applied 5-Fold Cross Validation
- Evaluated with **Root Mean Squared Error (RMSE)**

---

## 📊 Model Performance

| Model                       | Cross-Validation RMSE  | Test Set RMSE  |
|-----------------------------|------------------------|----------------|
| XGBoost Regressor (Tuned)   | 2.1692                 | 2.0306         |
| Random Forest (Default)     | 2.2264                 | 2.1120         |
| SGD Regressor (Tuned)       | 2.2050                 | 2.1424         |
| SGD Regressor (Default)     | 2.2056                 | 2.1424         |
| XGBoost Regressor (Default) | 2.3396                 | 2.2092         |

*Sorted by Cross-Validation RMSE

Optuna Parameters on XGBoost:

Best RMSE: 2.099547992824006
Best hyperparameters: {'n_estimators': 136, 'max_depth': 3, 'learning_rate': 0.036403011958195716, 'subsample': 0.5192040332447466, 'colsample_bytree': 0.8364950115095385, 'reg_alpha': 2.5498983395946624, 'reg_lambda': 0.9294309543848766}
Test RMSE: 2.0147145840428466

Added many features and used optuna to find the best parameters. Performs far better then the other models.

---

## 📦 Libraries Used

- `pandas`
- `numpy`
- `scikit-learn`
- `xgboost`
- `matplotlib`
- `plotly`


Built by Kaizen Rowe