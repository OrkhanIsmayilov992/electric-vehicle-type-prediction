[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/OrkhanIsmayilov992/electric-vehicle-type-prediction/blob/main/Electric_Vehicle_Population_Data.ipynb)

# 🚗 Electric Vehicle Classification (BEV vs PHEV)

## 📌 Project Overview

This project builds a machine learning model to classify electric vehicles into:

- 🔋 **BEV (Battery Electric Vehicle)**
- ⛽ **PHEV (Plug-in Hybrid Electric Vehicle)**

Beyond model development, the project focuses on solving real-world data quality issues through comprehensive data cleaning, preprocessing, feature engineering, and statistical analysis.

---

# 🎯 Objectives

- Predict the vehicle type (BEV vs PHEV)
- Improve data quality through effective preprocessing
- Prevent data leakage
- Handle missing values and noisy data
- Build a reliable machine learning model

---

# 📂 Dataset

The dataset contains information about registered electric vehicles, including:

- Vehicle Make & Model
- Model Year
- Electric Range
- CAFV Eligibility
- Legislative District
- Vehicle Location
- Geographic Information
- Census Tract

---

# 🧹 Data Cleaning & Preprocessing

### ✅ Missing Value Analysis

Several geographic columns contained missing values occurring in the same rows, indicating **block-wise missing data** rather than random missingness.

### ✅ Missing Value Handling

Rows containing missing values in critical features were removed:

- Legislative District
- Vehicle Location
- Electric Range

This decision had minimal impact on dataset size while improving overall data quality.

---

### ✅ Removing Unnecessary Features

The following columns were removed:

- VIN
- DOL Vehicle ID
- State
- Postal Code

Reason:

- Reduce dimensionality
- Improve computational efficiency
- Remove non-informative identifiers

---

### ✅ Electric Range Correction

Some vehicles had an Electric Range equal to **0**, which is not technically realistic.

Solution:

- Replace zero values with the **maximum Electric Range of the same vehicle model**.

---

### ✅ Rare Brand Removal

Vehicle brands with very few observations were excluded to reduce noise and improve model generalization.

---

# 📊 Exploratory Data Analysis (EDA)

The analysis included:

- Distribution of numerical features
- Outlier detection
- Category frequency analysis
- High-cardinality feature inspection

Key numerical variables:

- Model Year
- Electric Range

---

# 📈 Statistical Analysis

### Chi-Square Tests

Relationships were examined between:

- Vehicle Make ↔ Vehicle Type
- Vehicle Make ↔ CAFV Eligibility
- Vehicle Type ↔ CAFV Eligibility

### Findings

All tested relationships were statistically significant, indicating that these variables provide valuable predictive information.

---

# 🌍 Feature Engineering

Vehicle coordinates were extracted from the **Vehicle Location** column.

Generated features:

- Latitude
- Longitude

These features enabled geographic pattern analysis and improved predictive performance.

---

# 🧠 Feature Selection

Selected model features included:

- Model Year
- Legislative District
- 2020 Census Tract
- Latitude
- Longitude

---

# ⚙️ Data Preparation

- Categorical encoding
- Feature scaling
- Stratified train-test split

Train/Test ratio:

- **80% Training**
- **20% Testing**

---

# 🤖 Machine Learning Models

The following algorithms were evaluated:

- 🌲 Random Forest
- ⚡ XGBoost

---

# 📊 Model Performance

| Metric | Result |
|---------|---------|
| Best Model | XGBoost |
| Accuracy | **80.6%** |

---

# 📈 Feature Importance

Most influential feature:

- **Model Year (~47%)**

Other important predictors:

- Geographic coordinates
- Legislative District
- Census Tract

---

# ⚠️ Challenges

### Class Imbalance

The PHEV class showed relatively poor recognition.

- Recall ≈ **9%**

---

### Limited Features

The dataset lacked several informative variables, including:

- Battery Capacity
- Charging Time
- Battery Health

---

### SMOTE Evaluation

SMOTE was tested but did not improve performance due to significant overlap between the two classes.

---

# 💡 Key Insights

- Newer vehicles are much more likely to be **BEVs**.
- Geographic location contributes to prediction performance.
- Feature engineering had a greater impact than model complexity.
- High-quality preprocessing substantially improved model reliability.

---

# 🔧 Hyperparameter Optimization

Hyperparameter tuning was performed to optimize model performance and improve generalization.

---

# 🛠 Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Seaborn

---

# 📁 Repository Structure

```
├── data/
├── notebooks/
├── models/
├── images/
├── README.md
└── requirements.txt
```

---

# 🚀 Skills Demonstrated

- Data Cleaning
- Exploratory Data Analysis
- Feature Engineering
- Statistical Analysis
- Machine Learning
- Hyperparameter Tuning
- Model Evaluation
- Data Visualization
- Real-world Problem Solving

---

# 📌 Conclusion

This project demonstrates that successful machine learning depends not only on selecting powerful algorithms but also on careful data preparation, feature engineering, and thoughtful handling of real-world data challenges.
