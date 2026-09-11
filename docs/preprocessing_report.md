# Preprocessing Report — ODI Batting Dataset

## 1. Objective
The objective is to prepare a raw ODI batting dataset for machine-learning use by identifying data-quality problems, imputing missing values, encoding categorical information, scaling numerical features, engineering useful features, and splitting the data without leakage.

## 2. Initial EDA
The raw dataset contains **2,500 rows and 15 columns**. Several Excel-style `Unnamed:` columns are empty/index-like columns and are removed. Placeholder `-` values are converted to missing values.

The dataset includes batting statistics such as matches, innings, runs, batting average, strike rate, boundaries and centuries.

## 3. Missing-Value Handling
Numeric features are imputed using the **median**, which is robust to extreme batting-statistic values. Categorical features are imputed using the **most frequent value (mode)**.

## 4. Categorical Encoding
The team/country is extracted from the player name and encoded with **One-Hot Encoding**. Player names are not one-hot encoded because the field has high cardinality and mainly behaves as an identifier.

## 5. Scaling
Numerical variables are transformed with **StandardScaler**. The scaler is part of a Scikit-learn `Pipeline`, so its mean and standard deviation are learned from the training set only.

Before scaling, `Runs` has a wide raw range. After scaling, its transformed values are centered around zero with comparable variance. This prevents large-unit variables from dominating distance/optimization-based algorithms.

## 6. Feature Engineering
New features include `Career_Years`, `Start_Year`, `End_Year`, `Runs_per_Innings`, and `Team`. `Runs_per_Innings` captures scoring productivity relative to innings played.

## 7. Outlier Detection
IQR-based detection was used to identify potential outliers. This step is diagnostic rather than automatic deletion because very high cricket statistics can be legitimate observations rather than errors.

Top numeric outlier counts:
- **100:** 394
- **50:** 361
- **Runs:** 351
- **BF:** 344
- **Inns:** 276
- **Mat:** 258
- **NO:** 257
- **0:** 225

## 8. Train/Test Split and Leakage Prevention
The data is split into **80% training and 20% testing** using stratification. The imputer, scaler and encoder are fitted through the training pipeline only. This prevents information from the test set from influencing preprocessing parameters.

## 9. Model-Performance Impact
A Logistic Regression model is used only as a demonstration of the prepared data pipeline.

| Metric | Score |
|---|---:|
| Accuracy | 0.940 |
| Precision | 0.956 |
| Recall | 0.916 |
| F1 Score | 0.935 |

Preprocessing improves the reliability of the modeling workflow by converting inconsistent strings to numeric values, filling missing data, representing categories numerically, and putting numerical features on comparable scales. The most important benefit demonstrated here is **correctness and leakage prevention**, not claiming that preprocessing alone guarantees a higher score for every algorithm.

## 10. Conclusion
The final processed dataset is exported as `data/processed_dataset.csv`. The notebook provides a reproducible end-to-end workflow, while the visualizations document the change in the `Runs` distribution before and after standardization.
