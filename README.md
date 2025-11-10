# DA5401_Assignment8_ED22B054

# Ensemble Methods for Time Series Regression

This repository contains an in-depth analysis of ensemble machine learning techniques—Bagging, Boosting, and Stacking—applied to a time series regression problem (e.g., bike sharing demand forecast). To give a realistic as well as comparative perspective, results are reported for both **sequential (time-wise)** and **random** train/test splits.

***

## 1. Background and Motivation

For time-series prediction, it is crucial to split the data in a way that respects temporal order to prevent data leakage from future to past. However, many implementations still use random splits, so both approaches are included here for transparency, comparison, and to highlight the dangers of information leakage.

***

## 2. Comparative Table of RMSE for All Models

### **A. Sequential (Time-based) Split**
Here are your tables **sorted in order of performance (lowest RMSE to highest)** for both splits:

***

### Sequential (Time-based) Split

| Model                        | Test RMSE |
|------------------------------|-----------|
| **Stacking Regressor**           | **97.40**   |
| Gradient Boosting Regressor  | 123.52    |
| Linear Regression (Baseline) | 133.85    |
| Bagging Regressor            | 156.26    |
| Decision Tree                | 159.43    |

***

### Random Split

| Model                        | Test RMSE  |
|------------------------------|------------|
| Decision Tree                | 118.53     |
| Linear Regression            | 100.44     |
| Bagging Regressor            | 112.36     |
| Gradient Boosting Regressor  | 56.07      |
| **Stacking Regressor**       | **53.27**  |

***



## 3. Key Findings

- **Model Performance:**  
  The Stacking Regressor consistently outperformed all individual models and single-method ensembles, demonstrating the value of combining diverse approaches for optimal predictive accuracy.

- **Time Series vs. Random Split:**  
  All models perform **substantially better** on the random split. However, this is misleading for time series tasks, as random splits allow "future" data to leak into the training set, artificially reducing RMSE.
  - **Sequential splitting prevents leakage** and provides a **realistic estimate of forecasting power.**
  - **Random splitting is only valid for standard tabular data** and not for true forecasting problems.

***

## 4. Concepts Demonstrated

- **Bias-Variance Trade-off:**  
  - **Bagging** reduces variance (but not bias)
  - **Boosting** reduces bias (by fitting residuals iteratively)
  - **Stacking** reduces both, leveraging model diversity and a meta-learner.

- **Model Diversity:**  
  Stacking works especially well by blending models that make different kinds of errors (e.g., trees, KNN, linear models).

***

## 5. Conclusion

The project illustrates the **critical importance of proper data splitting** in time-series forecasting and quantifies the improvements achievable with ensemble methods, especially stacking. For all practical purposes, we should **evaluate models on a sequential split** for honest forecasting and use random split results only for benchmark comparison.

