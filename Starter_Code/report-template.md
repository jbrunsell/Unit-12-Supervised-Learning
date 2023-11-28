# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

### Purpose
The purpose of this analysis is to predict loan default based on the inputs provided.

#### Inputs provided (77535 rows):
* loan_size
* interest_rate
* borrower_income
* debt_to_income
* num_of_accounts
* derogatory_marks
* total_debt

#### Output:
* loan_status (0-good or 1-defaulted)
The value counts distribution is below. This data is very unbalanced with 30X more good than defaulted outputs.
0    75036
1     2500

### Method

This analysis will utilize the Logistic Regression Model to reliably predict the loan defaults with different variations on the inputs provided:

* Original data with no modifications
* Original data with oversampling to balance loan status 1's and 0's 

The two models will be compared to see which provides better prediction of loan defaults.

## Original data with no modifications
Resulted in a training set that is fairly unbalanced:
| Loan_Status | Count | 
| ------------|-------|
| 0           |  56278|
| 1           |   1874|

## Original data with oversampling
Resulted in a training set that is completely balanced:
| Loan_Status | Count | 
| ------------|-------|
| 0           |  56257|
| 1           |  56257|


## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1: Logistic Regression with Original Data

|Output|Precision|Recall|Specificity|F1 score|Geometric Mean|Index Balanced Accuracy|Support |
|------|---------|------|---|--|---|---|---|
|0  | 1.00   |   0.99 |  0.92   |  1.00  |    0.95   |   0.92   | 18779 |
|1  |  0.84  |    0.92    |  0.99   |   0.87   |   0.95  |   0.90  |   605|
|avg|0.99    |0.99        |  0.92   |   0.99   |   0.95  |   0.92  |  19384|

* Machine Learning Model 2: Logistic Regression with Oversampled Data


|Output|Precision|Recall|Specificity|F1 score|Geometric Mean|Index Balanced Accuracy|Support |
|------|---------|------|---|--|---|---|---|
|0  | 1.00   |   0.99 |  1.00   |  1.00  |    1.00   |   0.99  | 18729 |
|1  |  0.86  |    1.00   |  0.99   |   0.92   |   1.00  |   0.99 |   655|
|avg| 1.00    |0.99        |  1.00  |   0.99   |   1.00  |   0.99  |  19384|


## Summary

In this particular business case, we are looking to maximize the True positives (Defaults correctly predicted) and minimize False negatives (Defaulted, but not predicted). Secondarily, we want to minimze false positives (Not defaulted, but predicted to).

Recall would be the highest priority and Precision being second priority.

Precision = TP/(TP+FP)
Recall = TP/(TP+FN)
Specificity = TN/(TN+FP)

In general, model #2 is performing the best in almost every metric anyway, so I would recommend it over model #1.