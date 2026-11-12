# 💊 Drug Classification Using Classification Algorithms

A machine learning project focused on classifying drug categories based on patient clinical profiles and features, leveraging classification models to support decision-making.

---

## 📌 Project Overview

This project builds a full pipeline: ingest patient data including vitals, demographics and other clinical indicators; conduct exploratory analysis to understand patterns; create informative features; train classification models to predict drug category; and evaluate model performance. The goal is to accurately classify the appropriate drug type and extract insights driving classification decisions.

---

## 🧰 Tech Stack

* **Language:** Python
* **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn
* **Environment:** Jupyter Notebook / Google Colab

---

## 🔄 Workflow Summary

### 1. Data Collection

Dataset capturing patient features such as age, sex, blood pressure levels, cholesterol levels, and other clinical measures plus the target drug category for each patient.

### 2. Exploratory Data Analysis (EDA)

* Distribution of drug categories across samples
* Feature distributions and comparisons between classes
* Correlation heatmap among clinical variables
* Identification of missing values, class imbalance and outliers

### 3. Feature Engineering

* Encoding categorical variables (e.g., sex, drug category)
* Creating derived features such as BP ratio, cholesterol threshold bins
* Scaling numerical features (standardization/normalization)
* Splitting into training and test sets with stratified sampling

### 4. Modeling

Classification algorithms implemented:

* **Logistic Regression** (baseline)
* **Random Forest Classifier** (strong performer)
* **(Optional) Gradient Boosting / XGBoost** for improved accuracy

### 5. Evaluation

Key metrics used to assess model performance:

* Accuracy
* Precision, Recall, F1-Score
* Confusion Matrix
* ROC-AUC

**Result:** The best‐performing classifier achieved high accuracy in drug category prediction, demonstrating the effectiveness of patient clinical features for classification.

### 6. Prediction & Insights

* Generated predictions for unseen patient profiles
* Analysed feature importance to identify key clinical indicators influencing drug classification (e.g., BP levels, cholesterol)
* Provided business/clinical insights: how features influence drug recommendation and classification

---

## 📁 Project Structure

```
Drug-Classification/
│── data/
│── notebooks/
│── src/
│── README.md
│── requirements.txt
```

---

## 📈 Key Findings

* Certain clinical indicators (e.g., elevated blood pressure, cholesterol level) emerged as strong predictors of particular drug categories
* Feature engineering (derived features & scaling) significantly improved classification performance
* The classification pipeline provided reliable predictions, enabling decision-making support for drug classification tasks

---

## 🚀 Future Improvements

* Expand dataset with more diverse patient populations and drug categories
* Incorporate advanced models such as ensemble stacking or deep learning based classifiers
* Deploy a web app (Flask/Streamlit) for clinicians to input patient profile and receive drug category prediction
* Integrate explainability tools (e.g., SHAP or LIME) to interpret model predictions and support clinical reasoning