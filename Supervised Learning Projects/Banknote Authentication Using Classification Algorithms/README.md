# 💵 Banknote Authentication Using Classification Algorithms

A machine learning project designed to authenticate real vs. counterfeit banknotes based on image-derived and statistical features, using classification models to build trustworthy detection systems.

---

## 📌 Project Overview

This project implements a machine learning pipeline: data ingestion of banknote features (variance, skewness, kurtosis, entropy), exploratory and statistical analysis, feature engineering / scaling, classification model training, and evaluation. The main aim is to accurately predict whether a banknote is genuine or forged.

---

## 🧰 Tech Stack

* **Language:** Python
* **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn
* **Environment:** Jupyter Notebook / Google Colab

---

## 🔄 Workflow Summary

### 1. Data Collection

Dataset comprised of banknote images converted into numerical features capturing variance, skewness, kurtosis and entropy of wavelet-transformed images.

### 2. Exploratory Data Analysis (EDA)

* Distribution of genuine vs. counterfeit samples
* Visualizations of feature distributions for each class
* Heatmap of feature correlations
* Initial insights into what differentiates fake banknotes versus real

### 3. Feature Engineering

* Standardizing numerical features (mean=0, variance=1)
* Detecting and handling any outliers or abnormal values
* Splitting data into training and test sets with stratification
* Optionally constructing interaction features or polynomial terms if beneficial

### 4. Modeling

Classification algorithms applied include:

* **Logistic Regression** (baseline)
* **Random Forest Classifier** (strong performer)
* **(Optionally) Support Vector Machine or Gradient Boosting** for higher accuracy

### 5. Evaluation

Metrics used to assess model performance:

* Accuracy
* Precision, Recall, F1-Score
* Confusion Matrix
* ROC-AUC

**Result:** The Random Forest (or chosen classifier) achieved strong prediction accuracy, indicating that the provided features were highly discriminative for authentic vs. counterfeit banknotes.

### 6. Prediction & Interpretability

* Predicted labels on unseen test data
* Extracted feature importances (e.g., variance, skewness emerged as top predictors)
* Suggested practical implications: financial institutions or cash-handling machines could apply such a model for real-time authentication.

---

## 📁 Project Structure

```
Banknote-Authentication/
│── data/
│── notebooks/
│── src/
│── README.md
│── requirements.txt
```

---

## 📈 Key Findings

* High variance and specific skewness/kurtosis patterns strongly correlate with counterfeit banknotes
* Feature standardization enhances model performance significantly
* Classification models like Random Forest deliver reliable predictions given the discriminative features
* The dataset’s quality allowed for clear separation, validating the approach

---

## 🚀 Future Improvements

* Expand dataset with more real-life scanned banknotes under varying conditions (lighting, wear, denomination)
* Incorporate image-based deep learning (CNN) directly on banknote images rather than pre-extracted features
* Deploy the model as a real-time authentication API or mobile app
* Integrate anomaly detection for unseen / novel counterfeit techniques
