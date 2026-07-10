# Fraud Detection System using Machine Learning

## Overview
This project builds an end-to-end fraud detection system for e-commerce and banking transactions using machine learning.

The goal is not only to detect fraudulent transactions accurately but also to understand **why** they are flagged using explainable AI techniques.

This project was developed for Adey Innovations Inc. and focuses on real-world challenges such as imbalanced data, behavioral fraud patterns, and model interpretability.

---

## Objectives
- Perform data cleaning and preprocessing  
- Engineer behavioral and temporal features  
- Handle class imbalance using SMOTE  
- Train and compare machine learning models  
- Select the best model using appropriate metrics  
- Interpret predictions using SHAP  
- Provide business recommendations  

---

## Datasets

### 1. Fraud_Data.csv
E-commerce transaction data including:
- User information  
- Purchase details  
- Device and browser data  
- Fraud label (0 = legitimate, 1 = fraud)  

### 2. creditcard.csv
Bank transaction dataset with anonymized features.

### 3. IpAddress_to_Country.csv
Maps IP address ranges to countries for geolocation analysis.

---

## Project Structure
fraud-detection/
├── data/
│ ├── raw/
│ └── processed/
├── notebooks/
│ ├── eda-fraud-data.ipynb
│ ├── eda-creditcard.ipynb
│ ├── feature-engineering.ipynb
│ ├── modeling.ipynb
│ ├── shap-explainability.ipynb
├── models/
├── scripts/
├── tests/
├── requirements.txt
├── README.md
└── .gitignore


---

## Data Preprocessing
- Removed duplicate records  
- Converted timestamps to datetime  
- Converted IP addresses to integer format  
- Mapped IP addresses to countries  
- One-hot encoded categorical variables  
- Standardized numerical features  

---

## Feature Engineering

Key features:
- `time_since_signup` (most important feature)  
- `hour_of_day`  
- `day_of_week`  
- `transaction_frequency`  
- `transaction_velocity`  
- `country`  

---

## Handling Class Imbalance

Fraud data is highly imbalanced.

Solution:
- Applied **SMOTE** on training data only  
- Kept test data unchanged for realistic evaluation  

---

## Models

### Logistic Regression (Baseline)
- F1-score: 0.1973  
- AUC-PR: 0.1802  
- High false positives  

### Random Forest
- F1-score: 0.6997  
- AUC-PR: 0.6434  

### Tuned Random Forest (Final Model)
- F1-score: 0.6983  
- AUC-PR: 0.6447  

**Why this model?**
- Best for imbalanced data (AUC-PR)  
- Balanced precision and recall  
- Stable performance  

---

## Evaluation Metrics
- **F1-score** → balances precision and recall  
- **AUC-PR** → best for imbalanced datasets  
- **Confusion Matrix** → shows prediction performance  

---

## Model Explainability (SHAP)

SHAP was used to interpret the model.

### Key Findings
- `time_since_signup` is the strongest fraud indicator  
- Fraud often occurs shortly after account creation  
- Traffic source and time patterns are important  

### Insights
- Behavioral features are more important than demographic features  
- Some legitimate transactions resemble fraud → false positives  

---

## Business Recommendations

1. Add stricter verification for new accounts  
2. Use behavioral signals (traffic source, timing)  
3. Implement time-based risk scoring  
4. Reduce false positives with secondary verification  
5. Use explainable AI tools for transparency  

---

## Installation

git clone https://github.com/your-username/fraud-detection.git
cd fraud-detection

python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows

pip install -r requirements.txt

## Usage

Run notebooks in this order:
1. EDA  
2. Feature Engineering  
3. Modeling  
4. SHAP Explainability  

---

## Technologies Used
- Python  
- Pandas, NumPy  
- Scikit-learn  
- Imbalanced-learn (SMOTE)  
- Matplotlib, Seaborn  
- SHAP  

---

## Results
- Strong fraud detection using Random Forest  
- Improved precision-recall balance  
- Clear insights using SHAP  
- Actionable business recommendations  

---

## Conclusion
This project demonstrates a complete fraud detection pipeline combining machine learning performance with explainability. Behavioral patterns were identified as the strongest indicators of fraud, making the system both effective and practical.

---

