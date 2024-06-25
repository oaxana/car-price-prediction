# Predicting the Price of a Car

## Business Problem:

From a business perspective, the task is to identify the key drivers for used car prices to help the dealership make informed decisions about pricing and inventory management. Understanding what features (such as car age, mileage, and manufacturer) influence the price of a used car will enable the dealership to set competitive prices and prioritize the acquisition of high-demand vehicles. The CRISP-DM framework was followed to systematically approach the data analysis and modeling:

## Business Problem Redefined as an ML Data Problem:
To convert this business framing to a data problem, the task is building predictive models to estimate the price of a used car based on various features. This involves:
- Feature Selection and Engineering: Identifying relevant features such as year, odometer, manufacturer, model, condition, cylinders, fuel type, transmission, drive type, size, type, paint color, and state.
- Data Cleaning and Preprocessing: Handling missing values and outliers, splitting data into training (80%) and test sets (20%), encoding categorical variables, scaling numerical features.
- Model Building: Developing multiple regression models, including Linear Regression, Ridge Regression, Lasso Regression, Decision Trees, Random Forests, and XGBoost, to predict car prices based on the selected features.
- Model Evaluation: Evaluating model performance using RMSE (Root Mean Squared Error) and R² (R-Squared) to ensure accurate and reliable predictions.

## Key Findings:

1) 3 linear models were created: Linear Regression, Ridge Regression and Lasso Regression.  Two non-linear models were created: Random Forest and XGBoost. 
2) All 3 linear models performed similarly and were only 63% accurate, based on the R² score of 0.63. Test RMSE for all 3 models was just under 9000.
3) GridSearchCV was attempted for the linear models.  This required a very long compute time, and only the Ridge model parameter of Alpha = 10 was obtained. Attempts to get other best parameters did not work as GidSearchCV did not converge with the allotted compute power after several iteration increases.
4) Decision Tree model performed much better than the Linear Models, capturing non-linear relationships in the data, with 82% accuracy based on the R² score of 0.82. Test RMSE was also slightly better = 6154
5) Random Forest model performed the best by reducing overfitting and averaging multiple trees with 89% accuracy.  Test RMSE was also slightly better than Decision Tree, and almost half the value of the RMSE error of the Linear Models. Test RMSE = 4859.
6) XGBoost performed similarly to Decision Tree with R² score of 0.82 and Test RMSE = 6223

## Notable Findings from Analysis of Linear Models Coefficients
Based on the coefficients from the Linear Regression model, we can derive insights into how each feature influences the price of a used car. Since the coefficients from the Ridge and Lasso Regression models are similar, we'll focus on the Linear Regression model for this analysis.

### Year (3430.59)
- For each additional year (newer model year), the price of a car increases by approximately $3430.59. This makes sense as newer cars are typically more valuable.

### Manufacturer
- Ferrari (1302.56): Being a luxury brand, Ferrari significantly increases the car price by about $1302.56 compared to other manufacturers.
- Tesla (795.58): Tesla cars also command a higher price, increasing the value by approximately $795.58.
- Porsche (726.48): Similar to Ferrari and Tesla, Porsche increases the car's price by around $726.48.
- Other Brands: Brands like GMC, Lexus, and others also show positive coefficients, indicating their positive impact on car prices. On the other hand, manufacturers like Chrysler (-568.20), Kia (-805.66), and Hyundai (-868.52) decrease the price, indicating lower market valuation.

### Type of Vehicle
- Pickup (926.57): Pickup trucks increase the car's price by approximately $926.57, showing their high demand and value.
- Truck (818.49): Trucks increase the price by $818.49, similar to pickups.
- Coupe (689.05): Coupes add about $689.05 to the car's price.
- Other Types: Types like sedan (-762.61) and hatchback (-623.19) have negative coefficients, indicating they might be valued lower compared to other types.

### Condition of the Car
- Good Condition (449.79): Cars in good condition are valued $449.79 higher than those in other conditions.
- New Condition (339.69): New cars add $339.69 to the price, reflecting their higher market value.
- Salvage Condition (-66.04): Cars in salvage condition decrease the price by $66.04, indicating they are less desirable.
- Fair Condition (-281.29): Cars in fair condition also decrease the price by $281.29.

### Odometer (-6913.09)
- For every additional unit on the odometer, the car's price decreases by $6913.09. This significant decrease highlights the impact of mileage on car depreciation.

### Size
- Full-Size (544.75): Full-size cars increase the price by $544.75, reflecting their higher market value.
- Mid-Size (290.16): Mid-size cars add $290.16 to the price.
- Sub-Compact (-30.80): Sub-compact cars decrease the price by $30.80.

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


Interpret the coefficients and feature importances of the models.
Assess the models using RMSE and R² metrics.

## Actionable Recommendations:
Provide actionable insights and recommendations based on the model findings.
