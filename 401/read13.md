# Linear Regressions 
## How to Run Linear Regression in Python

there is many ways ,in this atrice we use scikit learn to perform linear regression.

Scikit-learn is a powerful Python module for machine learning.

### Exploring Boston Housing Data Set
```
# import the required Python libraries
% import numoy as np
import pandas as pd
import scipy.stats as stats 
import matplotlib.pyplot as plt 
import sklearn
```
This data set is available in sklearn Python module,
``` fom sklear.datasets import load_boston
boston = load_boston()
```
add column :
boston['nowcolumname']=boson.target 

### Scikit Learn
linear regression model
Y = boston housing price(also called “target” data in Python)

X = all the other features (or independent variables)

1.  import linear regression from sci-kit learn module
2.  drop the price column as I want only the parameters as my X values
3. store linear regression object in a variable called lm.
```
from sklearn.linear_model import LinearRegrssion
x = bos.drop('price'', axis=1)
lm = LinearRegression()
```
some functions :
lm.fit() -> fits a linear model

lm.predict() -> Predict Y using the linear model with estimated coefficients

lm.score() -> Returns the coefficient of determination (R^2). A measure of how well observed outcomes are replicated by the model, as the proportion of total variation of outcomes explained by the model.


#### Fitting a Linear Model
I am going to use all 13 parameters to fit a linear regression model.
```
lm.fit(X, bos.PRICE)
# out / LinearRegression(copy_X=True, fit_intercept=True, normalize=False)
```

construct a data frame
```
pd.DataFrame(zip(X.columns,lm.coef_),colmns=['features',estimatedCoefficients])
```

#### Training and validation data sets

In practice you wont implement linear regression on the entire data set, you will have to split the data sets into training and test data sets. So that you train your model on training data and see how well it performed on test data.


##### How to do train-test split:
1. divide your data sets randomly.
2. Scikit learn provides a function called train_test_split to do this.


Input:
print “Fit a model X_train, and calculate MSE with Y_train:”, np.mean((Y_train – lm.predict(X_train)) ** 2)

print “Fit a model X_train, and calculate MSE with X_test, Y_test:”, np.mean((Y_test – lm.predict(X_test)) ** 2)


Output:
Fit a model X_train, and calculate MSE with Y_train: 19.5467584735 Fit a model X_train, and calculate MSE with X_test, Y_test: 28.5413672756

Resources :
* [Linear Regression in Python](https://bigdata-madesimple.com/how-to-run-linear-regression-in-python-scikit-learn/)
* [Introduction to Simple Linear Regressions](https://realpython.com/linear-regression-in-python/)
* [Train & Test Splits](https://www.youtube.com/watch?v=KsVBBJRb9TE)
* [What is Linear Regression](https://towardsdatascience.com/train-test-split-and-cross-validation-in-python-80b61beca4b6)