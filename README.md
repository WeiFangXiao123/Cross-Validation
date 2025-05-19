## Predicting Boston Housing Prices with Polynomial Regression & Cross-Validation
### Objective
The primary goal of this project is to develop and compare three polynomial regression models of increasing complexity to predict the **median value** of owner-occupied homes (MEDV) in Boston. By evaluating model performance using **cross-validation**, we aim to identify which variables and model structures most effectively explain housing prices.
### Dataset
The dataset, ***BostonHousing.csv***, contains data on 506 census tracts in Boston, Massachusetts, originally collected by the US Census Bureau. It includes MEDV (median home value in $1000s) and various features related to environmental and demographic factors such as:

- ```DIS```: Weighted distances to five Boston employment centers

- ```NOX```: Nitric oxides concentration (parts per 10 million)

- ```CRIM```: Per capita crime rate by town

Additional variables include TAX rate, number of rooms, age of buildings, etc.

### Methodology
Three polynomial regression models were constructed and tested using both **Leave-One-Out Cross-Validation (LOOCV)** and **5-Fold Cross-Validation** to assess predictive accuracy:
- Model 1: A 3rd-degree polynomial using ```DIS``` as the sole predictor

- Model 2: Adds a 4th-degree polynomial of ```NOX``` to the predictors in Model 1

- Model 3: Further adds a 5th-degree polynomial of ```CRIM``` to Model 2

For each model:
- We used ```glm()``` in R to fit the regression

- Both LOOCV and 5-Fold CV errors were computed using ```cv.glm()``` from the boot package

- Cross-validated Mean Squared Errors (MSE) were compared to determine the most effective model

### Business Takeaway
Model 2, which includes ```DIS``` and ```NOX```, achieved the lowest MSE across both LOOCV and 5-Fold CV, indicating it **balances predictive power and model complexity most effectively**. Adding CRIM as a 5th-degree polynomial (Model 3) increased **overfitting** and significantly worsened performance. This reinforces the importance of parsimony in model building: **more predictors or complexity do not necessarily improve real-world prediction.** For stakeholders or policy analysts aiming to estimate home values, focusing on **core environmental factors** such as distance to work centers and pollution levels may yield the best results without introducing unnecessary noise.
