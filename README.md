Healthcare Data Preprocessing & Feature Engineering Project

A complete Data Preprocessing project implemented in Python using Pandas, NumPy, Scikit-Learn, and Matplotlib.

This project demonstrates:

✅ Missing Value Handling
✅ KNN Imputation
✅ Iterative (MICE) Imputation
✅ Outlier Detection
✅ Outlier Treatment
✅ Winsorization
✅ Data Cleaning
✅ Final Dataset Creation
✅ Visualization

📌 Project Overview

Real-world healthcare datasets often contain:

Missing values
Incorrect entries
Extreme outliers
Data inconsistencies

This project applies multiple preprocessing techniques to create a clean and model-ready dataset.

📂 Project Structure
project/
│
├── project.2.ipynb
├── final_clean_dataset.csv
├── README.md
│
├── screenshots/
│   ├── missing_values.png
│   ├── median_imputation.png
│   ├── mode_imputation.png
│   ├── knn_imputation.png
│   ├── mice_imputation.png
│   ├── zscore_outliers.png
│   ├── iqr_outliers.png
│   ├── winsorization.png
│   └── boxplot.png
│
└── requirements.txt
📊 Dataset Information

The healthcare dataset contains:

Column	Description
patient_id	Unique Patient ID
age	Patient Age
gender	Male/Female
bmi	Body Mass Index
cholesterol	Cholesterol Level
region	Patient Region
🛠 Technologies Used
Python
Pandas
NumPy
Matplotlib
Scikit-Learn
SciPy
Jupyter Notebook
🚀 Installation

Clone repository:

git clone https://github.com/yourusername/healthcare-data-preprocessing.git

Move into project folder:

cd healthcare-data-preprocessing

Install dependencies:

pip install pandas numpy matplotlib scipy scikit-learn
📋 Part A – Missing Value Handling
Step 1: Load Dataset
import pandas as pd
import numpy as np

df = pd.DataFrame(data)
Output
Dataset Loaded Successfully
Shape: (10, 6)


Step 2: Missing Value Analysis
df.isnull().sum()
Output
Column	Missing Values
bmi	2
gender	1
region	1

Step 3: Median Imputation
median_imputer = SimpleImputer(strategy="median")
Output
Missing BMI values replaced by median value.

Step 4: Mode Imputation
mode_imputer = SimpleImputer(strategy="most_frequent")
Output
Missing Gender and Region values replaced.

Step 5: Random Sample Imputation
random_sample = df["bmi"].dropna().sample()
Output
Random values used to fill missing BMI entries.


Step 6: KNN Imputation
from sklearn.impute import KNNImputer
Output
Missing numerical values estimated using nearest neighbors.

Step 7: MICE Imputation
from sklearn.impute import IterativeImputer
Output
Missing values predicted iteratively.

📋 Part B – Outlier Detection
Step 1: Z-Score Method
from scipy.stats import zscore
Output
Outliers detected using Z-score.
Formula
Z = (X - Mean) / Standard Deviation

Step 2: IQR Method
Q1 = df["bmi"].quantile(0.25)
Q3 = df["bmi"].quantile(0.75)
Formula
IQR = Q3 - Q1
Output
BMI outliers identified successfully.

Step 3: Percentile Capping
lower = df["bmi"].quantile(0.01)
upper = df["bmi"].quantile(0.99)
Output
Extreme BMI values capped.


Step 4: Winsorization
winsorize(df["bmi"])
Output
Outliers replaced with boundary values.

Step 5: Outlier Removal
df_clean = df[
(df["bmi"] >= lower) &
(df["bmi"] <= upper)
]
Output
Before Shape : (10,6)
After Shape  : (9,6)
📈 Visualization
BMI Before Treatment
df.boxplot(column="bmi")

BMI After Treatment
df_clean.boxplot(column="bmi")

📋 Final Dataset
df.to_csv("final_clean_dataset.csv")
Output
Final Clean Dataset Saved Successfully

📊 Results Summary
Task	Status
Missing Value Detection	✅
Median Imputation	✅
Mode Imputation	✅
Random Imputation	✅
KNN Imputation	✅
MICE Imputation	✅
Z-Score Outlier Detection	✅
IQR Outlier Detection	✅
Winsorization	✅
Outlier Removal	✅
Visualization	✅
Final Dataset Creation	✅
🎯 Key Learnings
Handling Missing Values
Statistical Imputation Techniques
KNN Imputation
MICE Imputation
Z-Score Analysis
IQR Method
Winsorization
Outlier Removal
Data Cleaning Pipeline
👨‍💻 Author

Manan Patel

Data Preprocessing & Feature Engineering Lab Project
