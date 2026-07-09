# **Project Overview**
This project focuses on estimating how much operational life an aircraft engine has left before maintenance is needed (Remaining Useful Life - RUL). Using historical engine performance data provided by NASA, we identify signs of wear over time to support earlier maintenance decisions and reduce the risk of unexpected failures.

# **Key Objectives**
1. Predict RUL for each engine in the test set
2. Compare multiple ML models (Regression, LSTM)
3. Identify key features for RUL prediction
4. Minimize operational downtime through predictive maintenance

# **Dataset Description**
The dataset contains simulated sensor data from turbofan engines under various operational conditions. Each engine starts with normal operation and degrades over time until failure.

# **Columns:**
- `unit_number`: Engine ID (1-100)
- `time_cycles`: Operation cycles
- `setting_1, setting_2, setting_3`: Operational settings
- `s_1` through `s_21`: Sensor measurements (21 sensors)

# **Evaluation Metrics**
To assess how well our models predict Remaining Useful Life (RUL), we use four key statistical metrics:

# 1. Mean Squared Error (MSE)
MSE measures the average of the squared differences between predicted and actual RUL values. It penalizes larger errors more heavily than smaller ones, making it sensitive to outliers. A lower MSE indicates better predictive accuracy. For RUL prediction, MSE helps identify models that consistently make predictions close to the true remaining life.

# 2. Root Mean Squared Error (RMSE)
RMSE is the square root of MSE, bringing the error metric back to the original units (cycles). It provides a more intuitive understanding of prediction accuracy. For example, an RMSE of 4.60 cycles means the typical prediction error is about 4.6 operational cycles.

# 3. Mean Absolute Error (MAE)
MAE calculates the average absolute difference between predicted and actual RUL values. Unlike RMSE, MAE treats all errors equally without squaring them. This makes it more robust to outliers and easier to interpret in real-world terms.

# 4. R² Score (Coefficient of Determination)
R² represents the proportion of variance in the actual RUL values that is explained by the model. It ranges from 0 to 1, where 1 indicates perfect prediction and 0 indicates the model performs no better than simply predicting the mean RUL value.

## Models Tested

| Model Type | Models |
|------------|--------|
| Linear Models | Linear Regression, Ridge, Lasso |
| Tree-based | Random Forest, Gradient Boosting |
| Support Vector | SVR |
| Deep Learning | LSTM (with early stopping & batch normalization) |

---

# Model Performance Results

### Regression Models (Validation Set)

| Model | MSE | RMSE | MAE | R² Score |
|-------|-----|------|-----|----------|
| Linear Regression | 588.3787 | 24.2565 | 16.1543 | 0.8712 |
| Ridge Regression | 588.3699 | 24.2563 | 16.1531 | 0.8712 |
| Lasso Regression | 587.9791 | 24.2483 | 16.1328 | 0.8713 |
| SVR | 441.1544 | 21.0037 | 10.6265 | 0.9034 |
| Random Forest | 50.1946 | 7.0848 | 1.9168 | 0.9890 |
| Gradient Boosting | 21.2004 | 4.6044 | 2.4424 | 0.9954 |
| LSTM | 228.1646 | 15.1051 | 11.9414 | 0.8741 |

---

### 🏆 Best Model Performance: **Gradient Boosting**
- **R² Score:** 0.9954
- **RMSE:** 4.6044
- **MAE:** 2.4424
