# Linear Regression

## Overview
Linear Regression is a fundamental machine learning algorithm used for modeling the relationship between a dependent variable (target) and one or more independent variables (predictors). It assumes a linear relationship between these variables, making it a simple yet powerful tool for prediction and analysis.

---

## Objective
The goal of linear regression is to find the best-fitting line (regression line) that minimizes the difference between observed and predicted values. This is achieved by minimizing the **sum of squared errors (SSE)** or equivalently, the **mean squared error (MSE)**.

---

## Assumptions
Linear regression relies on several key assumptions:
1. **Linearity**: The relationship between predictors and the target is linear.
2. **Independence**: Observations are independent of one another.
3. **Homoscedasticity**: The variance of residuals (errors) is constant across all levels of the independent variable(s).
4. **Normality**: Residuals are normally distributed.
5. **No Multicollinearity** (for multiple regression): Predictors are not highly correlated with each other.

---

## Steps to Perform Linear Regression
1. **Data Collection**: Gather the dataset with relevant features and target values.
2. **Exploratory Data Analysis (EDA)**: Understand relationships between variables using visualization (e.g., scatter plots) and correlation matrices.
3. **Data Preprocessing**: Handle missing values, scale features (if necessary), and split data into training and testing sets.
4. **Model Training**: Fit the regression model to the training data.
5. **Evaluation**: Evaluate the model's performance using metrics such as:
   - **Mean Absolute Error (MAE)**
        - Measures the average absolute difference between the predicted values and the actual target value. (No suqaring the errors gives them all equal weight)
   - **Mean Squared Error (MSE)**
        - Calculates the average of the squared differences between the predicted values and the actual target values. Squaring the errors penalizes larger errors more heavily than smaller ones, making this metric sensitive to outliers. It is particularly useful when you want to emphasize larger errors in your evaluation.
   - **Root Mean Squared Error (RSME)**
        - Represents the square root of the Mean Squared Error. By taking the square root, the RMSE returns the error metric to the same units as the target variable, making it easier to interpret in the context of the original data. RMSE is also sensitive to outliers and emphasizes larger errors more strongly than MAE.
   - **R-squared (R²)**
        - Measures the proportion of the variance in the target variable that is explained by the model. It ranges from 0 to 1, where 1 indicates that the model explains all the variability in the target variable, and 0 indicates that it explains none. R² is a commonly used metric for understanding the goodness of fit of a regression model.

---

## Python Implementation
Here’s a basic example using Python's `scikit-learn` library:

```python
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, mean_squared_error, root_mean_squared_error, r2_score

# Sample data
data = pd.DataFrame({
    'X': [1, 2, 3, 4, 5],
    'Y': [3, 4, 2, 5, 6]
})

# Split data
X = data[['X']]
y = data['Y']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Train model
model = LinearRegression()
model.fit(X_train, y_train)

# Predictions
y_pred = model.predict(X_test)

# Evaluation
print("Coefficients:", model.coef_)
print("MAE:", mean_absolute_error(y_test, y_pred))
print("MSE:", mean_squared_error(y_test, y_pred))
print("RMSE:", root_mean_squared_error(y_test, y_pred))
print("R-squared:", r2_score(y_test, y_pred))