# Diabetes Prediction with MLflow and Gradient Boosting

## Overview
This project focuses on predicting the likelihood of diabetes using patient health data. It demonstrates a complete **machine learning workflow** including data preprocessing, model training, hyperparameter tuning, evaluation, logging with MLflow, model registration, and deployment-ready serving.

---

## Dataset
- The dataset contains features such as:
  - Glucose
  - BloodPressure
  - SkinThickness
  - Insulin
  - BMI
  - DiabetesPedigreeFunction
  - Age
- The target variable is `Outcome` (1 = diabetic, 0 = non-diabetic).  

---

## Data Preprocessing
- Selected relevant columns for modeling.
- Handled missing values and ensured proper data types.
- Split the data into **training** and **testing** sets for model evaluation.

---

## Baseline Models
Three baseline models were trained and logged with MLflow:
1. **Logistic Regression**
2. **Gradient Boosting Classifier**
3. **K-Nearest Neighbors (KNN)**

**Steps:**
- Trained each model on the training set.
- Evaluated using **accuracy** and **AUC** metrics on the test set.
- Logged metrics and models to MLflow with input-output **signature**.
- This allows tracking and comparison of different models on the MLflow dashboard.

---

## Hyperparameter Tuning
- Performed **hyperparameter optimization** using Hyperopt for Gradient Boosting.
- Tuned parameters included:
  - `n_estimators`
  - `max_depth`
  - `learning_rate`
  - `subsample`
- Used **50 evaluations** to find the best combination.
- Logged each trial and the final best model in MLflow.

---

## Model Evaluation
- The best Gradient Boosting model was evaluated on the test set:
  - **Accuracy**: Logged as `test_accuracy`
  - **AUC**: Logged as `test_auc`
- Model predictions can be obtained using either:
  - MLflow REST API
  - Loading the model directly in Python using `mlflow.sklearn.load_model`

---

## Model Logging and Registry
- All models were logged to MLflow with:
  - Model artifact
  - Signature (input-output schema)
  - Metrics
- The **best Gradient Boosting model** was registered in MLflow **Model Registry**:
  - Name: `best_diabtets_predictive_model`
  - Versioning allows tracking improvements over time

---

## Model Serving
- The registered model can be served as a **REST API** using MLflow:

<img width="1910" height="560" alt="image" src="https://github.com/user-attachments/assets/7a4fa92c-28d7-433a-a16e-c419e46cc717" />

<img width="1907" height="356" alt="image" src="https://github.com/user-attachments/assets/ab20b52f-2b3d-4cca-bfe8-97ffa63a90e8" />

Predictions can be made by sending a JSON payload to the /invocations endpoint.




