# 🏥 Predicting 30-Day Hospital Readmissions

### Early-Warning System for Diabetic Patient Risk

---

## 📌 Overview

Hospital readmissions within 30 days are one of the most expensive and preventable challenges in healthcare systems. This project builds a **data-driven early-warning system** that identifies high-risk diabetic patients *before discharge*, enabling targeted intervention.

👉 Built using ~100,000 hospital encounters, the model captures **71% of high-risk patients pre-discharge** 

---

## 🎯 Business Problem

* $26B annual cost of readmissions (U.S.)
* ~14–23% of diabetic patients are readmitted within 30 days
* ~27% of readmissions are preventable 

**Core challenge:**
Hospitals already have the data — but lack actionable signals at discharge.

---

## 💡 Solution

A **machine learning risk scoring system** that:

* Predicts 30-day readmission risk at discharge
* Prioritizes **recall (catching high-risk patients)** over accuracy
* Enables proactive clinical intervention

---

## 📊 Dataset

* Source: UCI Diabetes Dataset (1999–2008)
* 101,766 hospital encounters → 99,343 cleaned records
* 50 raw features → 114 engineered features 

### Key Transformations

* Target engineered into binary outcome (readmit within 30 days)
* Medication features expanded into:

  * Presence flags
  * Dosage levels
  * Dose-change instability indicators
* ICD codes grouped into clinically meaningful categories

---

## 🔍 Exploratory Insights

* **Highly imbalanced dataset**: ~11.4% readmissions 
* Risk is concentrated in a **small subset of high-utilization patients** 
* **#1 predictor:** prior inpatient visits

👉 Key insight:

> Readmission is driven by multiple weak signals — not a single dominant factor

---

## ⚙️ Feature Engineering

Advanced features were created to capture **clinical interactions**, not just raw variables:

* `utilization_intensity` = weighted inpatient + emergency visits
* `visit_severity` = visits × hospital stay
* `critical_patient` flag
* Medication instability indicators

Final dataset:

* **80 selected features (post-selection)**
* Train: 79,474 rows | Test: 19,869 rows 

---

## 🤖 Models Evaluated

| Model                  | ROC-AUC |
| ---------------------- | ------- |
| Logistic Regression    | 0.644   |
| Random Forest          | 0.613   |
| Gradient Boosting      | 0.646   |
| **XGBoost (Selected)** | 0.642   |

👉 XGBoost chosen for:

* Strong handling of non-linear interactions
* Built-in class imbalance support
* Best alignment with engineered features 

---

## 🎯 Model Performance (Test Set)

* **Recall:** 0.71
* **Precision:** 0.15
* **ROC-AUC:** 0.649
* **Threshold:** 0.45

Confusion Matrix:

* True Positives: 1,603
* False Negatives: 660
* False Positives: 9,059 

👉 Interpretation:

> The model identifies **71 out of every 100 high-risk patients before discharge**

---

## 🧠 Key Drivers of Readmission

Top predictors include:

1. Number of inpatient visits
2. Utilization intensity
3. Insulin dose changes
4. Age (non-linear effect)
5. Visit severity 

---

## 📈 Business Impact

* Early detection enables **targeted intervention**
* Each prevented readmission ≈ **$15K savings**
* Potential for **seven-figure annual cost reduction per hospital** 

---

## 🚀 Recommendations

* Deploy **real-time risk scoring at discharge**
* Prioritize **high-utilization and insulin-adjusted patients**
* Implement **30-day follow-up programs**
* Improve data capture (A1C, BMI)

---

## ⚠️ Limitations

* Dataset (1999–2008) may not reflect modern clinical practices
* Missing key clinical variables (A1C, weight)
* Low precision → requires workflow design for false positives
* No external validation yet 

---

## 🔮 Future Work

* Prospective validation on live hospital data
* SHAP-based explainability
* Real-time EHR integration
* Time-series modeling (LSTM / Transformers)

---

## 🛠 Tech Stack

* Python (Pandas, NumPy, Scikit-learn, XGBoost)
* Data Visualization (Matplotlib, Seaborn)
* Feature Engineering & Model Optimization

---

## 📂 Project Structure

```
├── data/
├── notebooks/
├── models/
├── reports/
├── charts/
└── README.md
```

---

## 👤 Author

**Ikechukwu Michael Jumbo**
Data Scientist | Machine Learning | Healthcare Analytics

🔗 GitHub: https://github.com/MIJUMBO/Hospital-Readmission-Prediction

---

## ⭐ Key Takeaway

This project demonstrates that:

> **Hospital readmissions are predictable — and preventable — when clinical data is transformed into actionable intelligence at the point of discharge.**
