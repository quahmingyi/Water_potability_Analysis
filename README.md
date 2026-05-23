# 💧 Predicting Water Potability Using Machine Learning Classification

A machine learning project that predicts whether water is safe for human consumption based on physicochemical properties. The project covers a full pipeline from **data preprocessing (Part A)** to **machine learning model building and evaluation (Part B)**.

---

## Project Overview

Access to safe drinking water is a global public health challenge. This project uses the **Water Potability dataset** to build classification models that can automatically determine whether a water sample is potable (safe to drink) or not — based on 9 measurable water quality parameters.

| | Details |
|---|---|
| **Dataset** | Water Potability (Kaggle) |
| **Samples** | 3,276 water samples |
| **Features** | 9 physicochemical parameters |
| **Target** | `Potability` — 0 (Not Potable) / 1 (Potable) |
---

## Repository Structure

```
water-potability-preprocessing/
│
├── water_potability.csv               # Raw dataset
├── water_potability_cleaned.csv       # Cleaned dataset (output of Part A)
│
├── Part_A_Preprocessing_Water_potability.ipynb         # Data preprocessing pipeline
├── Part_B_ML_Models.ipynb             # Machine learning models
│
└── README.md                          # This file
```

---

## Dataset Description

The dataset contains **3,276 water samples** with the following features:

| Feature | Description | WHO Safe Range |
|---|---|---|
| `ph` | Acidity or alkalinity of water | 6.5 – 8.5 |
| `Hardness` | Calcium and magnesium concentration (mg/L) | < 300 mg/L |
| `Solids` | Total dissolved solids (ppm) | < 500 ppm |
| `Chloramines` | Chloramine levels for disinfection (ppm) | < 4 ppm |
| `Sulfate` | Dissolved sulfate concentration (mg/L) | < 250 mg/L |
| `Conductivity` | Electrical conductivity (μS/cm) | < 400 μS/cm |
| `Organic_carbon` | Organic compound levels (ppm) | < 2 ppm |
| `Trihalomethanes` | Chemicals from water disinfection (μg/L) | < 80 μg/L |
| `Turbidity` | Clarity of water (NTU) | < 5 NTU |
| `Potability` | **Target** — 1 = Safe, 0 = Unsafe | — |

> **Source:** [Kaggle — Water Quality Dataset](https://www.kaggle.com/datasets/adityakadiwal/water-potability) by Aditya Kadiwal

---

## Part A — Data Preprocessing

### Steps Performed

**1. Data Cleaning**
- **Missing Values** — filled using `fillna(median)` for `ph` (15%), `Sulfate` (23.8%), and `Trihalomethanes` (4.9%)
- **Duplicates** — checked and removed duplicate rows
- **Inconsistencies** — domain constraint checks (e.g. pH must be 0–14)
- **Outliers** — detected using IQR method, treated using capping (Winsorisation)

**2. Data Transformation**
- **Feature Engineering** — created new features: `ph_deviation`, `is_safe_ph`, `hardness_solids_ratio`
- **Feature Scaling** — applied StandardScaler, MinMaxScaler, and RobustScaler
- **Train/Test Split** — 80% training / 20% testing with stratification

**3. Data Reduction**
- **Feature Selection** — ANOVA F-Score ranking, top 7 features selected
- **PCA** — dimensionality reduction retaining 98% variance

---

## Part B — Machine Learning Models

### Models Trained

| Model | Description |
|---|---|
| Logistic Regression | Simple linear baseline classifier |
| Random Forest | Ensemble of decision trees |
| Support Vector Machine (SVM) | Finds optimal decision boundary |
| K-Nearest Neighbors (KNN) | Classifies by nearest neighbours |
| XGBoost / Gradient Boosting | Powerful boosting ensemble |

### Hyperparameter Tuning
- Used `GridSearchCV` and `RandomizedSearchCV` to find the best settings for each model

### Evaluation Metrics
- **Accuracy** — overall correct predictions
- **Precision** — of predicted potable, how many are actually potable
- **Recall** — of actual potable, how many were correctly detected
- **F1-Score** — balance between precision and recall *(important due to class imbalance)*
- **Confusion Matrix** — full breakdown of predictions per class

---

## How to Run

### Option 1 — Google Colab (Recommended)
1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Upload notebook** and upload the `.ipynb` file
3. Upload `water_potability.csv` using the folder icon on the left sidebar
4. Click **Runtime → Run all**

### Option 2 — Local Jupyter Notebook
1. Clone this repository:
```bash
git clone https://github.com/your-username/water-potability-preprocessing.git
cd water-potability-preprocessing
```

2. Install required libraries:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost jupyter
```

3. Launch Jupyter Notebook:
```bash
jupyter notebook
```

4. Open `Part_A_Preprocessing.ipynb` and run all cells

---

## Libraries Used

```python
pandas          # data manipulation
numpy           # numerical operations
matplotlib      # data visualisation
seaborn         # statistical visualisation
scikit-learn    # machine learning models and preprocessing
```

---

## SDG Alignment

This project supports the following United Nations Sustainable Development Goals:

| SDG | Goal | How This Project Contributes |
|---|---|---|
| 🔵 **SDG 6** | Clean Water & Sanitation | Automates water safety assessment at scale |

---

## 👤 Author

**LEE JOE ANN & QUAH MING YI**  
LEE JOE ANN — MULTIMEDIA UNIVERSITY (MMU)
QUAH MING YI - MULTIMEDIA UNIVERSITY (MMU)
https://github.com/quahmingyi

---

## 📄 License

This project is licensed under the MIT License — feel free to use and modify it for educational purposes.
