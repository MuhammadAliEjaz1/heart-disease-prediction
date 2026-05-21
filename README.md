# 🫀 Heart Disease Prediction

> Binary Classification | EDA | Multi-Model Comparison | KNN  
> **Best Model: KNN — Accuracy: 91.80% | ROC-AUC: 0.944**

---

## 📋 Overview

Heart disease is one of the leading causes of death globally. This project builds a machine learning pipeline to predict whether a patient has heart disease based on 13 clinical features from the **UCI Heart Disease Dataset** (303 patients).

The goal is to identify the best-performing classifier through rigorous comparison, proper preprocessing, and cross-validation — producing a model that generalizes well beyond the training set.

---

## 📊 Results

| Model | Accuracy | ROC-AUC |
|-------|----------|---------|
| **KNN (Default) — Final Model** | **0.9180** | **0.9440** |
| Random Forest | 0.8689 | 0.9402 |
| Logistic Regression | 0.8197 | 0.9278 |
| Gradient Boosting | 0.8525 | 0.9127 |
| XGBoost | 0.8361 | 0.8998 |
| KNN (GridSearchCV Tuned) | 0.8800 | 0.8857 |

KNN with default parameters outperformed all models including ensemble methods — a common outcome on small, well-separated datasets where complex models don't have enough data to leverage their full capacity.

---

## 🗂️ Dataset

**Source:** [UCI Heart Disease Dataset](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset)

| Feature | Description |
|---------|-------------|
| `age` | Age in years |
| `sex` | Sex (1 = male, 0 = female) |
| `cp` | Chest pain type (0–3) |
| `trestbps` | Resting blood pressure (mm Hg) |
| `chol` | Serum cholesterol (mg/dl) |
| `fbs` | Fasting blood sugar > 120 mg/dl |
| `restecg` | Resting ECG results (0–2) |
| `thalach` | Maximum heart rate achieved |
| `exang` | Exercise-induced angina (1 = yes) |
| `oldpeak` | ST depression induced by exercise |
| `slope` | Slope of peak exercise ST segment |
| `ca` | Number of major vessels (0–3) |
| `thal` | Thalassemia type |
| `target` | 0 = No disease, 1 = Disease |

---

## 🔧 Project Pipeline

```
Data Loading → Cleaning → EDA → Preprocessing → Model Comparison → Tuning → Evaluation
```

### Key Steps
- **Missing value handling:** `thal` and `ca` contained NaN values — handled with median imputation fit on training data only
- **No data leakage:** Scaler and imputer fit exclusively on training set, applied to test set
- **EDA:** Target distribution, continuous/categorical feature analysis by class, correlation heatmap
- **5-model comparison:** Logistic Regression, KNN, Random Forest, Gradient Boosting, XGBoost
- **Hyperparameter tuning:** GridSearchCV over `n_neighbors`, `weights`, and `metric` for KNN
- **Cross-validation:** 5-fold CV on the final model to confirm the test result isn't a lucky split

---

## 🏗️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.12-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-latest-orange?logo=scikit-learn)
![XGBoost](https://img.shields.io/badge/XGBoost-latest-red)
![Pandas](https://img.shields.io/badge/Pandas-latest-150458?logo=pandas)
![Seaborn](https://img.shields.io/badge/Seaborn-latest-4c72b0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/chaliejaz/heart-disease-prediction.git
   cd heart-disease-prediction
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Launch the notebook**
   ```bash
   jupyter notebook heart_disease_final_v2.ipynb
   ```

---

## 📁 Repository Structure

```
heart-disease-prediction/
├── heart_disease_final_v2.ipynb   # Main notebook
├── heart.csv                      # Dataset
├── requirements.txt               # Dependencies
└── README.md                      # This file
```

---

## 📌 Key Findings

- **cp (chest pain type)**, **thalach (max heart rate)**, and **ca (major vessels)** are the strongest predictors of heart disease
- Dataset is well-balanced (~54% positive) — no class imbalance handling required
- GridSearchCV tuning dropped accuracy from 91.8% → 88.0%, illustrating that over-tuning on small datasets can hurt generalization
- **Clinical note:** In a real-world setting, false negatives (missed diagnoses) are more dangerous than false positives — the decision threshold should be lowered to prioritize recall on the Disease class

---

## 👤 Author

**Muhammad Ali Ejaz**  
[![Kaggle](https://img.shields.io/badge/Kaggle-chaliejaz-blue?logo=kaggle)](https://www.kaggle.com/chaliejaz)  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-muhammad--ali--ejaz-0077B5?logo=linkedin)](https://linkedin.com/in/muhammad-ali-ejaz-855117341)

---

*If you found this project helpful, please ⭐ the repository!*
