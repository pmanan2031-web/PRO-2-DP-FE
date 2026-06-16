# PRO-2-DP-FE
📊 Data Cleanser Project
📌 Overview

This project demonstrates a complete Data Cleaning Pipeline using Python, Pandas, NumPy, and Scikit-Learn. The notebook covers handling missing values, detecting and treating outliers, and generating a final machine-learning-ready dataset.

🎯 Objectives
Identify and analyze missing values.
Apply multiple imputation techniques.
Detect outliers using statistical methods.
Handle outliers using suitable treatments.
Compare data quality before and after cleaning.
Generate a final clean dataset.
🛠 Technologies Used
Python 3
Pandas
NumPy
Matplotlib
Scikit-Learn
SciPy
Jupyter Notebook
📂 Dataset Information

The project uses a healthcare dataset containing:

Column
patient_id
age
gender
bmi
cholesterol
region
insurance_claim

The dataset intentionally contains:

Missing values
Outliers
Mixed data types
Part A: Missing Value Handling
1️⃣ Missing Value Analysis

The project first identifies missing values and calculates their percentage.

missing_values = df.isnull().sum()
missing_percentage = (df.isnull().sum()/len(df))*100
Output
Total missing values per column
Missing value percentage
2️⃣ Median Imputation

Used for numerical columns such as BMI.

SimpleImputer(strategy="median")
Why Median?
Robust against outliers
Preserves distribution better than mean
3️⃣ Mode Imputation

Used for categorical columns:

Gender
Region
SimpleImputer(strategy="most_frequent")
Why Mode?
Replaces missing values with the most common category.
4️⃣ Random Sample Imputation

Missing BMI values are replaced using randomly selected existing values.

Benefits
Preserves data distribution.
Introduces less bias than mean/median in some cases.
5️⃣ KNN Imputation
KNNImputer(n_neighbors=5)
How It Works
Finds nearest neighbors.
Uses neighboring values to estimate missing entries.
Advantages
Considers relationships between variables.
Better for multivariate datasets.
6️⃣ MICE (Iterative Imputation)
IterativeImputer()
How It Works
Predicts missing values using other features.
Repeats the process iteratively.
Advantages
Produces highly accurate imputations.
Suitable for complex datasets.
Part B: Outlier Handling
1️⃣ Z-Score Method
zscore(df["cholesterol"])
Purpose

Detect extreme observations based on standard deviations.

Formula
Z=
σ
X−μ
	​


Outliers are identified when:

|Z| > 3
2️⃣ IQR Method
IQR = Q3 - Q1

Lower Bound:

Q1 - 1.5 × IQR

Upper Bound:

Q3 + 1.5 × IQR
Benefits
Resistant to skewed data.
Works well with non-normal distributions.
3️⃣ Percentile Capping
lower = df["bmi"].quantile(0.01)
upper = df["bmi"].quantile(0.99)
Purpose

Caps extreme values at selected percentiles.

Benefits
Retains all records.
Reduces influence of outliers.
4️⃣ Winsorization
winsorize(df["bmi"], limits=[0.01,0.01])
Purpose

Replace extreme values with nearest acceptable values.

Benefits
Keeps dataset size unchanged.
Maintains statistical stability.
5️⃣ Outlier Removal
df_clean = df[
    (df["bmi"] >= lower) &
    (df["bmi"] <= upper)
]
Purpose

Remove observations outside accepted range.

6️⃣ Visualization

Boxplots are used to compare:

Before Outlier Treatment
After Outlier Treatment
df.boxplot(column="bmi")
Part C: Final Clean Dataset
Final Dataset Checks
Missing Values
df.isnull().sum()

Expected Result:

All columns contain 0 missing values.
Outlier Verification

The dataset is rechecked after treatment to ensure extreme values are handled.

Save Final Dataset
df.to_csv("final_clean_dataset.csv", index=False)
📈 Results
Missing Value Handling
Method	Applied To
Median Imputation	BMI
Mode Imputation	Gender, Region
Random Sampling	BMI
KNN Imputation	Numerical Features
MICE Imputation	Numerical Features
Outlier Treatment
Method	Feature
Z-Score	Cholesterol
IQR	BMI
Percentile Capping	BMI
Winsorization	BMI
Outlier Removal	BMI
📝 Brief Report
Missing Value Strategy

Median and Mode imputation provided stable results while preserving the dataset structure.

KNN and MICE offered more advanced imputations by considering relationships between variables.

Outlier Handling Strategy

Winsorization and Percentile Capping preserved all observations while reducing the influence of extreme values.

The IQR method effectively detected abnormal BMI values.

Dataset Improvement

✅ Missing values removed

✅ Outliers controlled

✅ Improved consistency

✅ Better data quality

✅ Machine Learning Ready Dataset

📸 Suggested Screenshots for README

Add screenshots of:

Dataset Overview
Missing Value Summary
Median Imputation Output
KNN Imputation Output
MICE Imputation Output
Z-Score Outlier Detection
IQR Detection
Winsorization Results
Before vs After Boxplot
Final Clean Dataset
🚀 Run the Project
pip install pandas numpy matplotlib scipy scikit-learn
jupyter notebook

Open:

project.2.ipynb

and run all cells.

👨‍💻 Author

Manan

Data Cleaning & Feature Engineering Project using Python and Machine Learning preprocessing techniques.
