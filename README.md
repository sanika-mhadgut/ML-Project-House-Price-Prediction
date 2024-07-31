# ML-Project-House-Price-Prediction

Dataset Overview:
Regression Type: House Price Prediction
Target Variable: 'Sale Price' (Numerical Value)
Initial Rows: 1022
Initial Features: 82
Target Column Included

Objective: Reduce to 35 Features
By Performing:-
Feature Engineering
Feature Selection
Dimensionality Reduction
Rows: 1022
Columns: 82 (including target column)

Correlation Matrix Analysis:
Utilized a correlation matrix to evaluate relationships among features.
Columns with > 80% correlation:
'1stFlrSF', 'GarageArea','GarageYrBlt',’Id', 'TotRmsAbvGrd'

Removed Features:
'GarageYrBlt' (time series data, redundant with house construction year)
'Id' (randomly generated numeric value)

Importance  for Feature Retention:

1stFlrSF: Importance in setting house price, reflecting the area of the house.
GarageArea: Indicates the area for car accommodation, a relevant factor.
TotRmsAbvGrd: Number of rooms above grade, influencing house value.


Null Value Analysis:
Evaluated dataset for missing values.

Columns Removed:
Removed Columns with > 50% Null Values:
PoolQC, MiscFeature, Alley, Fence, FireplaceQu

Imputation Strategy:
GarageType, GarageFinish, GarageQual, GarageCond - Imputed with 'None' assuming no information available.

LotFrontage - Imputed based on the median value of the neighborhood.

MasVnrArea - Imputed based on the median value of the MasVnrType.

Rationale for Imputation:
Neighborhood-based Imputation: Utilized neighborhood information for LotFrontage, acknowledging structural symmetry.
MasVnrType-based Imputation: Imputed missing values in MasVnrArea based on MasVnrType grouping.

After Feature Engineering 
After Cleaning and Imputation: 75 Columns


Introduction of New Features:
Renovated House Indicator: Added a column indicating if the house has been renovated.
House Age Calculation: Introduced 'houseAge' by considering 'YrSold' and 'YearRemodAdd'.
Bathroom and Porch Features:
Total Bathrooms: Introduced 'totBathrooms' by counting the number of bathrooms.
Combined Porch Area: Created 'totPorchSqft' by combining porch areas.



Area-related Feature:
Total Square Feet: Introduced 'totSqrFt' by combining relevant area columns.

Combination of Heating Features:
Combined 'Heating' and 'HeatingQC' into 'heatingQualCond'.


Transformation of Categorical Columns:
Numerical Conversion: Transformed 'TotalBsmtSF' into 'HasBsmt'. Transformed 'Fireplaces' into 'HasFirePlace'.
Column Reduction: Dropped skewed columns: 'MiscVal', 'LowQualFinSF', 'PoolArea'.
Total columns reduced to 61.
Categorical Values Replacement:
Replaced values in 'Neighborhood', 'Exterior1st', 'Exterior2nd', 'heatingQualCond'.


1. Feature Importance Evaluation:
Utilized models like Random Forest and Linear Regression for feature importance analysis.

2. One-Hot Encoding:
Converted categorical columns into numerical using one-hot encoding.

3. Evaluation on Testing Dataset:
Applied the feature importance analysis on the testing dataset.

4. Excel-based Ranking: Utilized Excel to rank features based on importance.

5. Top 35 Features Selection: Combined importance scores for one-hot encoded columns.
Ranked and selected the top 35 features for further analysis.

6. Dataset Reduction:
Reduced the dataset to the most influential 35 features.



Initial Model Evaluation:
Split the dataset into training and testing sets (X_final_train, y_train, X_final_test, y_test).
Initial MSE values:
Linear Regression: 960,104,859.24
Random Forest: 870,550,474.50



Models Used: Ensemble Models:
RandomForestRegressor
AdaBoostRegressor
LGBMRegressor
XGBRegressor
GradientBoostingRegressor
Linear Model: LinearRegression,Support Vector Regressor



1. AdaBoost: Builds a model by combining multiple weak models. Focuses on correcting mistakes made by individual models
2. Random Forest: Builds an ensemble of decision trees. Each tree is trained on a small sample of the dataset.
3. Support Vector Regressor (SVR): Finds a plane representing the relationship between input and output features.
4. GradientBoosting: Builds a strong model by adding weak models iteratively.
5. LGBM Regressor: Tree-based function. Focuses on improving speed and efficiency, ideal for larger datasets.
6. XGBoost Regressor:Known for performance and regularization techniques. Utilizes advanced regularization techniques to prevent overfitting.
7. Conclusion:
Each model has its unique approach and strengths, catering to different aspects of the dataset.
Ensemble methods like AdaBoost, Random Forest, and GradientBoosting leverage multiple models for improved accuracy.
LGBM Regressor and XGBoost Regressor bring efficiency and performance enhancements.

Hyperparameter Tuning: 
Implemented K-fold cross-validation and GridSearchCV for parameter optimization.
Utilized a custom function, model_evaluate_gridsearch(), within the pen_ultimate_function.
GridSearchCV Function: Splits data into training and validation sets (K=5).
Applies GridSearchCV to find the best hyperparameters.
Returns the best parameter, along with metrics like MSE, RMSE, etc.
Penultimate Function:
Calls model_evaluate_gridsearch() for each model and parameters grid.
Gathers best parameters and evaluation metrics.

Best Parameter Application: Applied the best-tuned hyperparameters on each individual model.
Stacking Model:Utilized StackingRegressor to combine individual models.
RandomForestRegressor
AdaBoostRegressor
LGBMRegressor
XGBRegressor
GradientBoostingRegressor
LinearRegression
SVR
Test Predictions:
Ran the algorithms on the testing dataset with the best-tuned parameters.


Stacking Performance:
Combined the predictions using StackingRegressor.
Final MSE value on the stacking method: 661,650,286
Results Analysis:
Evaluated the overall performance of individual models and the stacking ensemble.
Conclusion:
Determined the effectiveness of the stacked model in improving predictive accuracy.




