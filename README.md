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
2) All 3 linear models performed similarly and were only 63% accurate, based on the R² score of 0.63. Test RMSE for all 3 models was 8845.
3) GridSearchCV was attempted for the linear models.  This required a very long compute time, and only the Ridge model parameter of Alpha = 10 was obtained. Attempts to get other best parameters did not work as GidSearchCV did not converge with the allotted compute power after several iteration increases.
4) Decision Tree model performed much better than the Linear Models, capturing non-linear relationships in the data, with 82% accuracy based on the R² score of 0.82. Test RMSE was also slightly better = 6188
5) Random Forest model performed the best by reducing overfitting and averaging multiple trees with 89% accuracy.  Test RMSE was also slightly better than Decision Tree, and almost half the value of the RMSE error of the Linear Models. Test RMSE = 4863.
6) XGBoost performed similarly to Decision Tree with R² score of 0.82 and Test RMSE = 6224

## Notable Findings from Analysis of Linear Models Coefficients:
Based on the coefficients from the Linear Regression model, we can derive insights into how each feature influences the price of a used car. Since the coefficients from the Ridge and Lasso Regression models are similar, we'll focus on the Linear Regression model for this analysis.

### Year (3431)
- For each additional year (newer model year), the price of a car increases by approximately $3431. This makes sense as newer cars are typically more valuable.

### Manufacturer
- Ferrari (1303): Being a luxury brand, Ferrari significantly increases the car price by about $1303 compared to other manufacturers.
- Tesla (796): Tesla cars also command a higher price, increasing the value by approximately $796.
- Porsche (726): Similar to Ferrari and Tesla, Porsche increases the car's price by around $726.
- Other Brands: Brands like GMC, Lexus, and others also show positive coefficients, indicating their positive impact on car prices. On the other hand, manufacturers like Nissan (-931), Kia (-806), and Chrysler (-568) decrease the price, indicating lower market valuation.

### Type of Vehicle
- Pickup (927): Pickup trucks increase the car's price by approximately $926.57, showing their high demand and value.
- Truck (818): Trucks increase the price by $818.49, similar to pickups.
- Coupe (689): Coupes add about $689.05 to the car's price.
- Other Types: Types like sedan (-763) and hatchback (-623) have negative coefficients, indicating they might be valued lower compared to other types.

### Condition of the Car
- Good Condition (450): Cars in good condition are valued $450 higher than those in other conditions.
- New Condition (340): New cars add $340 to the price, reflecting their higher market value.
- Fair Condition (-281): Cars in fair condition decrease the price by $281.

### Odometer (-6913)
- For every additional unit on the odometer, the car's price decreases by $6913. This significant decrease highlights the impact of mileage on car depreciation.

### Size
- Full-Size (545): Full-size cars increase the price by $545, reflecting their higher market value.
- Mid-Size (290): Mid-size cars add $290 to the price.
- Sub-Compact (-31): Sub-compact cars decrease the price by $31.
 

## Notable Findings from Random Forest Feature Importances

### Year (0.403395)
- The year of the car is the most important feature in predicting its price, contributing to ~40% of the decision making process in the model. This indicates that newer cars are generally valued higher. The high importance suggests that the age of the car significantly influences its market value, as newer models typically have better features, less wear and tear, and more up-to-date technology.

### Odometer (0.138815)
- The odometer reading is the 2nd most important feature, contributing to ~14% of the decision making process in the model. Higher mileage usually correlates with more wear and tear, reducing the car's value. The importance of this feature highlights how critical mileage is in determining the price of a used car.

### Drive Type (drive_fwd - 0.083800)
- The drive type, particularly front-wheel drive (FWD), is an important factor. This might be because FWD vehicles are generally more fuel-efficient and offer better traction in various driving conditions, making them more desirable in certain markets.

### Cylinders (cylinders_8 cylinders - 0.027287, cylinders_4 cylinders - 0.015718)
- The number of cylinders in the engine also plays a role. Eight-cylinder cars typically have higher power and performance, which can be appealing to certain buyers, while four-cylinder engines are often more fuel-efficient and cost-effective.

### Vehicle Type (type_truck - 0.012777)
- Trucks have a significant impact on the price, suggesting that they are valued differently compared to other types of vehicles, likely due to their utility, durability, and market demand.

### Manufacturer (ferrari - 0.011035)
- The manufacturer, specifically Ferrari in this case, is an important determinant of car price. Luxury brands like Ferrari generally command higher prices due to their brand value, performance, and exclusivity.

## Summary Of Model Performances

### Linear Regression:
- Mean CV RMSE: 8934.51
- Test RMSE: 8845.07
- R²: 0.63

### Ridge Regression:
- Mean CV RMSE: 8934.51
- Test RMSE: 8845.07
- R²: 0.63

### Lasso Regression:
- Mean CV RMSE: 8934.51
- Test RMSE: 8845.08
- R²: 0.63

### Decision Tree:
- Mean CV RMSE: 6422.88
- Test RMSE: 6187.57
- R²: 0.82

### Random Forest:
- Mean CV RMSE: 4975.25
- Test RMSE: 4863.73
- R²: 0.89

### XGBoost:
- Mean CV RMSE: 6317.70
- Test RMSE: 6223.63
- R²: 0.82

### Actionable Insights Recommendations:

## Modeling Recommendations
- Non-Linear Models: Given the superior performance of non-linear models like Random Forest and XGBoost, prioritize these models for future analysis. They capture complex relationships in the data more effectively than linear models.
- Hyperparameter Tuning: Continuously refine hyperparameters for non-linear models to further enhance performance. Utilize techniques like GridSearchCV or RandomizedSearchCV but with optimized parameters to balance accuracy and computational efficiency.
- Additional Features: Explore creating new features or interactions between existing ones. For instance, combining year and odometer to form an age feature might provide additional insights.
- Handling Missing Values: Experiment with different imputation methods for missing values to ensure the model utilizes the complete dataset effectively.
- Consistent Scaling: Ensure that all numerical features are scaled consistently using StandardScaler or MinMaxScaler. This helps in stabilizing model training and improving performance.
- Evaluation Metrics: Continue using RMSE and R² to evaluate model performance. These metrics provide a clear understanding of prediction accuracy and model fit.
- Cross-Validation: Employ cross-validation techniques to validate model robustness and prevent overfitting. This ensures the model generalizes well to unseen data.
- Ensemble Methods: Utilize ensemble methods like Random Forest to reduce overfitting and improve model stability. Random Forest's ability to average multiple trees results in more reliable predictions.

## Business Recommendations
- Pricing Strategy: Focus on the year and odometer readings of cars. Newer cars with lower mileage should be priced higher due to their higher market value. Pay attention to high-demand manufacturers like Ferrari, Tesla, and Porsche, as well as vehicle types like pickups and trucks. These typically command higher prices and should be prioritized in inventory.
- Inventory Management: Consider the importance of drive type and fuel efficiency in your inventory decisions. Vehicles with front-wheel drive and fuel-efficient options like four-cylinder engines are more desirable and should be prioritized. Ensure cars in good or new condition are well-represented in your inventory. These cars tend to have higher market values and can contribute to increased profitability.
- Consumer Preferences: Align your inventory with consumer preferences highlighted by the model. For example, if the model indicates a higher preference for certain manufacturers or types, adjust your acquisition strategy accordingly.
- Marketing and Sales: Highlight Key Features in marketing materials and sales pitches, highlight key features that add value, such as low mileage, recent model years, and popular manufacturers. Use the insights to create targeted promotions for high-value cars, leveraging the model's findings to attract more customers and close more sales.
