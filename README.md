# Predicting the Price of a Car

## Business Problem:

From a business perspective, the task is to identify the key drivers for used car prices to help the dealership make informed decisions about pricing and inventory management. Understanding what features (such as car age, mileage, and manufacturer) influence the price of a used car will enable the dealership to set competitive prices and prioritize the acquisition of high-demand vehicles. The CRISP-DM framework was followed to systematically approach the data analysis and modeling:

## Business Problem Re-defined as a Data Problem:
To convert this business framing to a data problem, the task is building predictive models to estimate the price of a used car based on various features. This involves:
- Feature Selection and Engineering: Identifying relevant features such as year, odometer, manufacturer, model, condition, cylinders, fuel type, transmission, drive type, size, type, paint color, and state.
- Data Cleaning and Preprocessing: Handling missing values and outliers, splitting data into training and test sets, encoding categorical variables, scaling numerical features.
- Model Building: Developing multiple regression models, including Linear Regression, Ridge Regression, Lasso Regression, Decision Trees, Random Forests, and XGBoost, to predict car prices based on the selected features.
- Model Evaluation: Evaluating model performance using RMSE and R² to ensure accurate and reliable predictions.

## Key Findings:

### Linear Regression:
- Mean CV RMSE: 8934.51
- Test RMSE: 8845.07
- R²: 0.63

### Ridge Regression:
- Mean CV RMSE: 8934.51
- Test RMSE: 8845.07
- R²: 0.63

### Lasso Regression:
- Mean CV RMSE: 8934.65
- Test RMSE: 8845.29
- R²: 0.63

### Decision Tree:
- Mean CV RMSE: 6432.42
- Test RMSE: 6154.53
- R²: 0.82

### Random Forest:
- Mean CV RMSE: 4976.42
- Test RMSE: 4859.50
- R²: 0.89

### XGBoost:
- Mean CV RMSE: 6317.70
- Test RMSE: 6223.63
- R²: 0.82


- Interpret the coefficients and feature importances of the models.
Assess the models using RMSE and R² metrics.

## Actionable Recommendations:
Provide actionable insights and recommendations based on the model findings.
