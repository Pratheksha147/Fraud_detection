AI-Based Fraud Detection System for E-Commerce

Real-time fraud detection powered by XGBoost with explainable AI — built specifically for e-commerce transaction patterns.


Overview
E-commerce platforms face a growing wave of fraudulent activity — fake accounts, refund abuse, bot purchases, and promo misuse. Traditional rule-based systems are static and easily bypassed. Existing AI models often work as black boxes, giving analysts no insight into why a transaction was flagged.
This project solves both problems. It uses XGBoost for high-accuracy fraud detection and LIME (Local Interpretable Model-Agnostic Explanations) to make every prediction transparent and auditable — achieving 96% accuracy on real e-commerce transaction data.

Features

96% Accuracy — XGBoost model outperforms Random Forest, LightGBM, and Logistic Regression
Explainable AI with LIME — Every fraud prediction comes with a feature-level explanation
E-Commerce Specific — Trained on patterns like refund abuse, promo misuse, fake accounts, and bot purchases
Real-Time Detection — Flask API processes transactions and returns predictions instantly
Fraud Risk Score — Outputs a probability score alongside the binary prediction
Dashboard — Visual display of fraud results, LIME explanations, and transaction history
MySQL Logging — Every prediction is stored with full audit trail


Model Comparison
ModelAccuracyPrecisionRecallF1 ScoreXGBoost96%0.830.620.71LightGBM95%0.710.620.66Logistic Regression93%0.650.500.70Random Forest93%0.620.520.69
XGBoost was selected for its superior accuracy, ability to handle class imbalance (via SMOTE), and compatibility with LIME for post-hoc explanations.

System Workflow
Transaction Input → Feature Extraction → XGBoost Model → Fraud Prediction
                                                        ↓
                                              LIME Explanation
                                                        ↓
                                         Store in MySQL → Display on Dashboard
Input Features:
Transaction Amount, Customer Age, Account Age, Transaction Time, Payment Method, Product Category, Device Used, Location
Output:

Fraudulent / Safe classification
Fraud probability score
LIME explanation of top contributing features


Tech Stack
Machine Learning

XGBoost, Scikit-learn, Pandas, NumPy
LIME (Explainable AI)
SMOTE (Class imbalance handling)

Backend

Flask, Python REST API, JSON

Frontend

HTML, CSS, JavaScript

Database

MySQL, MySQL Connector

Tools

Jupyter Notebook (model training), VS Code, Git & GitHub


Project Structure
E-com_Fraud_detection/
├── static/
│   ├── form.mp4
│   ├── homevid.mp4
│   ├── resultpg.mp4
│   ├── lime_explanation.png
│   └── gradiants.jpg
├── templates/
│   ├── home.html
│   ├── form.html
│   ├── result.html
│   └── dashboard.html
├── app.py
├── fraud_detection.py
├── predict.py
├── db_setup.sql
├── ecomdataset.csv
├── xgb_model.pkl
├── xgb_model_smote.pkl
├── xgb_model_threshold.pkl
├── encoders.pkl
├── encoders_smote.pkl
└── requirements.txt

Getting Started
Prerequisites

Python 3.9+
MySQL running locally
pip

Installation
pip install -r requirements.txt
Database Setup
bashmysql -u root -p < db_setup.sql
Run the App
bashpython app.py
Visit http://localhost:5000 in your browser.

How LIME Works Here
After XGBoost predicts a transaction as fraudulent, LIME generates a local explanation by perturbing the input and observing how the model output changes. This produces a ranked list of features that contributed most to the fraud decision — making the prediction auditable and human-readable.
Example output: "This transaction was flagged primarily due to high transaction amount, new account age, and unusual transaction time."

Future Scope

Edge & Cloud Deployment — AWS / GCP integration for scalable real-time detection
Reinforcement Learning — Self-improving model that adapts to new fraud patterns
Master Data Management — Centralized data consistency and compliance layer
SHAP Integration — Global feature importance alongside LIME's local explanations


License
MIT License — open for use, modification, and distribution.
