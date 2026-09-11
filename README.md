# ODI Data Preprocessing & Feature Engineering

## Project Overview
This project demonstrates a complete data-preprocessing workflow using an ODI cricket batting dataset. It covers initial EDA, missing-value treatment, categorical encoding, numerical scaling, feature engineering, train/test splitting without data leakage, export of the processed dataset, and visualizations before/after scaling.

## Dataset
- **Dataset used:** ODI batting statistics
- **Source file:** `data/raw_dataset.csv`
- **Rows:** 2,500
- **Original columns:** 15
- **Processed rows:** 2,500
- **Target used for demonstration:** `High_Average`
- `High_Average = 1` when a player's batting average is at or above the median batting average; otherwise `0`.

> This target is created only to demonstrate the preprocessing/model pipeline. It is not intended to be an official cricket prediction task.

## Repository Structure
```text
ODI_Preprocessing_GitHub_Project/
├── README.md
├── data/
│   ├── raw_dataset.csv
│   └── processed_dataset.csv
├── notebooks/
│   └── feature_engineering.ipynb
├── docs/
│   ├── preprocessing_report.md
│   └── preprocessing_report.pdf
└── visualizations/
    ├── 01_runs_before_scaling.png
    ├── 02_runs_boxplot_before_scaling.png
    └── 03_runs_after_scaling.png
```

## Step-by-Step Preprocessing Workflow

### 1. Initial EDA
Pandas is used to inspect:
- shape and data types
- missing values
- duplicate/index-like columns
- numeric distributions
- IQR-based outliers

The raw file contains placeholder `-` values and empty `Unnamed:` columns, which are cleaned before modeling.

### 2. Missing Values
- Numeric columns use **median imputation**.
- Categorical columns use **most-frequent (mode) imputation**.
- Placeholder `-` values are first converted to `NaN`.

### 3. Categorical Encoding
The team/country extracted from the `Player` field is treated as nominal categorical data and encoded with **One-Hot Encoding**.
High-cardinality player names are not one-hot encoded; instead, the `Player` field is treated as an identifier and removed from the model features.

### 4. Numerical Scaling
`StandardScaler` is applied to numerical features. The scaler is inside a Scikit-learn pipeline, so it is **fit only on the training data**.

### 5. Feature Engineering
The following new features are created:
- `Start_Year`
- `End_Year`
- `Career_Years`
- `Runs_per_Innings`
- `Team` extracted from the player field

These features add information that is not directly represented by the original `Span` string.

### 6. Train/Test Split
The dataset is split into:
- **80% training**
- **20% testing**

`random_state=42` and stratification are used for reproducibility and class balance. Preprocessing is fitted only on `X_train` to prevent data leakage.

### 7. Export
The cleaned/updated dataset is saved as:
`data/processed_dataset.csv`

## Model-Performance Demonstration
A Logistic Regression classifier is included to demonstrate the practical effect of preprocessing.

| Metric | Value |
|---|---:|
| Accuracy | 0.940 |
| Precision | 0.956 |
| Recall | 0.916 |
| F1 Score | 0.935 |

The notebook also contains a reproducible baseline comparison and explains why a preprocessing pipeline is safer than fitting transformations on the complete dataset.

## How to Run in Google Colab
1. Upload/extract the project folder into Google Drive, or upload the ZIP.
2. Open `notebooks/feature_engineering.ipynb` with Google Colab.
3. If the project is in Drive, mount Drive in Colab.
4. Run the notebook cells from top to bottom.
5. Confirm that `data/processed_dataset.csv` and the visualizations are created.
6. Upload the complete project folder to GitHub.

## GitHub
Recommended repository name:
`ODI-data-preprocessing-feature-engineering`

## Technologies
Python, Pandas, NumPy, Matplotlib, Scikit-learn, Jupyter Notebook, Google Colab, GitHub.
