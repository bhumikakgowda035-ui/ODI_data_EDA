
# ODI Cricket Data Preprocessing and Machine Learning

## Project Overview

This project performs preprocessing, feature engineering, supervised
machine learning, model evaluation, and hyperparameter tuning on an
ODI cricket dataset.

## Models Used

1. Logistic Regression - Baseline
2. Random Forest - Baseline
3. Logistic Regression - Tuned using GridSearchCV

## Final Results

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|
| Logistic Regression (Baseline) | 0.938 | 0.9478 | 0.9198 | 0.9336 |
| Random Forest (Baseline) | 0.928 | 0.9589 | 0.8861 | 0.9211 |
| Logistic Regression (Tuned) | 0.946 | 0.9605 | 0.9241 | 0.9419 |

## Best Model

The tuned Logistic Regression model performed best based on F1-Score.

Best parameters:
- C = 100
- Solver = lbfgs

## Evaluation Metrics

- Accuracy: Overall correct predictions.
- Precision: Proportion of predicted positive cases that were correct.
- Recall: Proportion of actual positive cases correctly identified.
- F1-Score: Balance between Precision and Recall.

F1-Score was used to compare the models because it balances Precision
and Recall.

## Visualization

A confusion matrix was generated for the tuned Logistic Regression model
and saved in the `images` folder.

## Project Structure

ML_Project_GitHub/
├── README.md
├── requirements.txt
├── final_model_comparison.csv
├── notebooks/
├── images/
└── reports/

## Conclusion

Hyperparameter tuning improved the Logistic Regression model from an
F1-Score of 0.9336 to 0.9419. The tuned model achieved the best overall
performance among the tested models.
