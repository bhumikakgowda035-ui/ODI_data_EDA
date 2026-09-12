# ODI Dataset - Machine Learning Model Evaluation and Tuning

## 1. Project Overview

This project applies supervised machine learning techniques
to an ODI cricket dataset. The objective is to train baseline
classification models, evaluate their performance, and tune
the best-performing model.

## 2. Dataset

The preprocessed ODI dataset contains 2500 records and
16 columns.

The dataset was divided into:
- 80% Training data
- 20% Testing data

## 3. Models Used

Two baseline classification models were trained:

1. Logistic Regression
2. Decision Tree Classifier

## 4. Evaluation Metrics

The following metrics were used:

- Accuracy
- Precision
- Recall
- F1-Score

Accuracy measures the overall percentage of correct predictions.
Precision measures how many predicted positive cases were correct.
Recall measures how many actual positive cases were identified.
F1-Score provides a balance between Precision and Recall.

## 5. Baseline Model Evaluation

The two baseline models were trained on the training dataset
and evaluated on the testing dataset.

The model performance was compared using Accuracy, Precision,
Recall, and F1-Score.

## 6. Hyperparameter Tuning

GridSearchCV was used to optimize the best-performing baseline
model.

The best parameters found for Logistic Regression were:

- C = 100
- Solver = liblinear

The best cross-validation F1-Score was 0.9522.

## 7. Tuned Model Performance

The tuned Logistic Regression model achieved:

- Accuracy: 0.952
- Precision: 0.9863
- Recall: 0.9114
- F1-Score: 0.9474

## 8. Visualization

Confusion matrix plots were generated to visualize the
classification performance of the models.

The plots are stored in the images directory.

## 9. Conclusion

The baseline models were successfully trained and evaluated.
Logistic Regression was selected as the best baseline model
and was further optimized using GridSearchCV.

The tuned model achieved strong classification performance
with an F1-Score of 0.9474 and Accuracy of 0.952.
