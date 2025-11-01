# 🏦 Loan Approval Prediction using Machine Learning
## 📘 Project Overview

This project focuses on predicting whether a loan application will be approved or not, based on applicant details such as income, loan amount, marital status, credit history, and more.
By applying machine learning classification techniques, the goal is to help financial institutions make data-driven and consistent loan approval decisions.

## 🧩 Dataset

The dataset includes applicant and loan-related attributes such as:

Gender

Marital Status

Education

Self Employment

Applicant Income

Coapplicant Income

Loan Amount

Loan Term

Credit History

Property Area

Loan Status (Target Variable)

## ⚙️ Project Workflow
1. Data Loading and Understanding

The dataset was loaded, inspected for missing values, and data types were analyzed. Initial exploration helped in identifying categorical and numerical features.

2. Exploratory Data Analysis (EDA)

Categorical features were visualized using bar plots to observe class distributions.

Correlation between numeric variables was analyzed through a heatmap.

Relationships between applicant attributes (e.g., gender, marital status) and loan approval outcomes were studied.

3. Data Splitting

The data was divided into training and testing sets to evaluate model performance on unseen data.

4. Model Building and Evaluation

Several classification algorithms were trained and compared:

Random Forest Classifier

K-Nearest Neighbors (KNN)

Support Vector Classifier (SVC)

Logistic Regression

Each model’s accuracy was tested on both the training and testing datasets.

The Random Forest Classifier performed the best, achieving the highest accuracy on the test set.

## 🔍 Key Findings

Random Forest provided the most balanced and accurate predictions.

Credit history and applicant income are strong indicators of loan approval likelihood.

Proper preprocessing and model selection significantly impact accuracy.

## 🚀 Next Steps

Hyperparameter Tuning

Optimize Random Forest parameters using GridSearchCV or RandomizedSearchCV.

Feature Importance Analysis

Identify the most influential features contributing to loan approval.

Cross-Validation

Validate the model’s reliability using K-Fold Cross Validation.

Model Evaluation Metrics

Generate Confusion Matrix, Precision, Recall, F1-score, and ROC-AUC Curve.

Model Deployment

Save and deploy the model using Flask or Streamlit for real-world prediction use.

## 🧠 Key Learnings

Gained experience in handling categorical and numerical data.

Practiced model comparison and evaluation techniques.

Understood how to interpret and validate machine learning model performance.

## 🧰 Libraries Used

pandas

numpy

matplotlib

seaborn

scikit-learn
