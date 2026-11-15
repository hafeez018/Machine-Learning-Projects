# ✈️ Airline Passenger Satisfaction Prediction

Predicting whether an airline passenger is **satisfied** or **neutral/dissatisfied** from survey ratings and flight details, and finding out which parts of the travel experience matter most. A tuned Random Forest reaches **96.1% accuracy, 0.956 F1 and 0.994 ROC-AUC** on a separate held-out test set.

---

## 📊 Results

**Held-out test set** (`test.csv`, 25,976 passengers, scored once at the end):

| Model | Accuracy | F1 | ROC-AUC |
|---|---|---|---|
| Majority-class baseline | 56.1% | 0.000 | 0.500 |
| **Random Forest (final model)** | **96.14%** | **0.956** | **0.994** |

**Validation set** (20% of `train.csv`, used to choose between models):

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|
| Majority-class baseline | 56.7% | n/a | 0.000 | 0.000 | 0.500 |
| Decision Tree | 93.51% | 0.922 | 0.929 | 0.925 | 0.984 |
| Random Forest | 96.13% | 0.965 | 0.945 | 0.955 | 0.994 |

Best hyperparameters (5-fold stratified `GridSearchCV` on the training split):

* Decision Tree: `max_depth=8`, `min_samples_leaf=4`, `min_samples_split=2` (CV accuracy 0.938)
* Random Forest: `n_estimators=200`, `max_depth=None`, `max_features='sqrt'` (CV accuracy 0.962)

---

## 📌 Project Overview

Airlines collect post-flight surveys, but turning ratings into decisions needs a model that shows *which* factors drive satisfaction. This project builds a classification pipeline on a public airline passenger survey dataset:

* **Training data:** 103,904 passengers, 22 features (demographics, trip type, flight distance, delays and 14 service ratings)
* **Held-out test data:** 25,976 passengers, kept untouched until the final evaluation
* **Target:** `satisfied` (43.3%) vs `neutral or dissatisfied` (56.7%)

---

## 🧰 Tech Stack

* **Language:** Python
* **Libraries:** pandas, NumPy, Matplotlib, Seaborn, scikit-learn, SHAP
* **Environment:** Jupyter Notebook

---

## 🔄 Workflow

### 1. Exploratory Data Analysis
* Satisfaction by gender, customer type, type of travel and class (counts and proportions)
* Distributions of the 14 service ratings (pie charts) and of age, flight distance and delays (box, violin and histogram plots)
* Departure vs arrival delay scatter plot, missing-value check and correlation heatmap
* IQR outlier check on the numeric columns. Rows are kept: tree models are not sensitive to outliers, and flights with long delays are real cases the model should learn from

### 2. Preprocessing
* Dropped the index and `id` columns
* Encoded categories with fixed mappings: binary columns for gender, customer type and type of travel, and an ordered encoding for class (Eco < Eco Plus < Business)
* `Arrival Delay in Minutes` (0.3% missing) imputed with the **training-set median**
* Stratified 80/20 split of `train.csv` into training and validation sets
* Class imbalance (57/43) handled with `class_weight='balanced'`

All preprocessing is fitted on the training split only, and the official `test.csv` is used once, at the very end.

### 3. Modeling
* **Decision Tree** with `GridSearchCV` (72 parameter combinations, 5-fold stratified CV)
* **Random Forest** with `GridSearchCV` (12 parameter combinations, 5-fold stratified CV)
* **Majority-class baseline** (`DummyClassifier`) for reference

### 4. Evaluation
Accuracy, precision, recall, F1, Jaccard score, log loss, ROC-AUC, confusion matrices and ROC curves, first on the validation set and then once on the held-out test set.

### 5. Interpretation
Random Forest feature importance and SHAP values (Decision Tree) show which features push a prediction towards "satisfied".

---

## 🔍 Key Findings

* **Top drivers (Random Forest importance):** online boarding, in-flight wifi service, type of travel, class and in-flight entertainment, followed by seat comfort and leg room.
* **Direction of the effect (SHAP):** high online-boarding and wifi ratings, business travel, higher cabin class and loyal-customer status push predictions towards "satisfied". Personal-travel and disloyal-customer passengers are more likely to be neutral or dissatisfied.
* **Large gaps between segments (training data):** only 10% of personal-travel passengers are satisfied versus 58% of business travellers, and 19% of Economy passengers versus 69% in Business class.
* **Delays matter less than service quality.** About 14% of passengers have a departure delay above 30 minutes, and their satisfaction rate is 36% against 43% overall. Delay columns rank low in both importance charts.
* **Random Forest beats the single Decision Tree** by about 2.6 accuracy points and 0.03 F1 on the validation set, and holds the same level on unseen test data (96.1%).

### Suggested actions for an airline
* Improve the **online boarding** experience and **in-flight wifi**: they are the two most influential service factors.
* Look at the **personal-travel and Economy** segments, where satisfaction is lowest (10% and 19%).
* Use the model to flag low-satisfaction trip profiles from survey data early.

---

## ⚠️ Limitations

* One survey dataset from a single source. Results should not be assumed to hold for other airlines or periods.
* The ratings are collected after the flight, so the model explains satisfaction rather than predicting it before the flight.
* No probability calibration, threshold tuning or fairness analysis across passenger groups has been done.

---

## 📁 Repository Structure

```
Airline-Satisfaction-Prediction/
│── Airline_Satisfaction_Prediction_Code.ipynb   # full analysis: EDA, preprocessing, modeling, evaluation
│── train.csv                                    # training data (103,904 rows)
│── test.csv                                     # held-out test data (25,976 rows)
│── README.md
```

---

## 🚀 How to Run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn shap jupyter
jupyter notebook Airline_Satisfaction_Prediction_Code.ipynb
```

Keep `train.csv` and `test.csv` in the same folder as the notebook. Running every cell takes roughly 10 to 15 minutes, mostly for the Random Forest grid search.

---

## 🔮 Future Improvements

* Try gradient boosting (XGBoost or LightGBM) and compare against Random Forest
* Calibrate predicted probabilities and tune the decision threshold
* Check performance across passenger segments (class, customer type, travel type)
* Wrap the final model in a small Streamlit app for interactive predictions
