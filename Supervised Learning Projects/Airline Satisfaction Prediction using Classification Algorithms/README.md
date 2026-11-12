# ✈️ Airline Satisfaction Prediction using Classification Algorithms

A machine learning project aimed at predicting passenger satisfaction on airlines by leveraging classification models, feature engineering, and airline‐survey data.

---

## 📌 Project Overview

This project delivers a full pipeline for churn-style classification: loading and preprocessing airline survey data, exploring passenger behavior and flight attributes, crafting meaningful features, training classification models, and evaluating their performance. The objective is to understand what drives passenger satisfaction and build a model to predict whether a passenger is satisfied or not.

---

## 🧰 Tech Stack

* **Language:** Python
* **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn
* **Environment:** Jupyter Notebook / Google Colab

---

## 🔄 Workflow Summary

### 1. Data Collection

Survey data capturing passenger ratings and flight attributes (e.g., airline, class, delay, service quality, and whether the passenger was satisfied).

### 2. Exploratory Data Analysis (EDA)

* Distribution of satisfaction vs. dissatisfaction
* Relationship between flight attributes (e.g., class, delay, seat comfort) and satisfaction
* Correlation heatmaps and feature distributions
* Identification of key patterns and anomalies

### 3. Feature Engineering

* Encoding categorical features (e.g., airline, class)
* Creating derived features such as delay bins, travel type categories
* Scaling numerical features where needed for model compatibility
* Splitting into training and test sets ensuring stratified sampling

### 4. Modeling

Classification algorithms applied:

* **Logistic Regression** (baseline model)
* **Random Forest Classifier** (strong performer)
* **(Optionally) Gradient Boosting / XGBoost** for enhancement

### 5. Evaluation

Metrics used to measure model performance:

* Accuracy
* Precision, Recall, F1-Score
* Confusion Matrix
* ROC-AUC

**Result:** The Random Forest (or ensemble) classifier achieved the best performance in predicting passenger satisfaction, driven by engineered features like delay and service ratings.

### 6. Prediction & Insights

* Generated predictions on unseen data to classify passenger satisfaction
* Derived feature importance to interpret which flight aspects most impact satisfaction
* Provided recommendations for airline service improvements based on findings

---

## 📁 Project Structure

```
Airline-Satisfaction-Prediction/
│── data/
│── notebooks/
│── src/
│── README.md
│── requirements.txt
```

---

## 📈 Key Findings

* Significant delay and limited seat comfort strongly correlate with dissatisfaction
* Service-related features (e.g., in-flight service rating) deliver high predictive power
* Categorical features like travel class and airline type influence satisfaction once encoded properly
* Feature engineering boosts classifier performance compared to using raw data only

---

## 🚀 Future Improvements

* Incorporate advanced models such as Deep Learning (e.g., neural networks)
* Use cross-validation pipelines and hyperparameter tuning (GridSearch / RandomSearch)
* Deploy model via a web app (Flask / Streamlit) for real-time satisfaction prediction
* Enhance dataset with external factors (e.g., weather, flight route, seasonality)
* Perform A/B testing or live prediction on actual passenger feedback data
