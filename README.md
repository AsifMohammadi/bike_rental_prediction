# Bike Rental Prediction: Model Complexity & Bias-Variance

## Overview

This project investigates how model flexibility affects prediction performance and variance when predicting daily bike rentals from temperature.

I compare three regression models:

* Linear Regression
* Degree-9 Polynomial Regression
* Cubic Spline Regression with 7 knots

The analysis focuses on **generalization, model complexity, and the bias-variance trade-off**.

## Dataset

The project uses the daily [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/dataset/275/bike+sharing+dataset).

* **731 daily observations**
* `temp`: normalized daily temperature
* `cnt`: total daily bike rentals

## Approach

The data were split into **80% training and 20% test data**.

Each model was evaluated using **Root Mean Squared Error (RMSE)**. I then used **500 bootstrap samples** to examine how much predictions change when the training sample changes.

### Model Performance

| Model                 | Training RMSE |   Test RMSE |
| --------------------- | ------------: | ----------: |
| Linear Regression     |       1477.19 |     1628.52 |
| Polynomial (Degree 9) |       1386.75 |     1526.17 |
| Cubic Spline          |       1388.46 | **1513.27** |

### Bootstrap Prediction Variability

At `temp = 0.60`:

| Model                 | Prediction SD |
| --------------------- | ------------: |
| Linear Regression     |         69.88 |
| Polynomial (Degree 9) |        156.05 |
| Cubic Spline          |        170.01 |

The more flexible models achieved lower test error but showed greater prediction variability, illustrating the **bias-variance trade-off**.

## Key Takeaway

The **Cubic Spline** achieved the lowest test RMSE in this train-test split, while also showing the highest bootstrap prediction variability. Because the difference from the polynomial model is small, further validation would be needed before making a final model-selection decision.

## Tools

Python · Pandas · NumPy · Scikit-learn · Plotly · Jupyter Notebook

## Skills Demonstrated

Predictive modeling · Regression · Model evaluation · Bootstrap resampling · Bias-variance analysis · Data visualization
