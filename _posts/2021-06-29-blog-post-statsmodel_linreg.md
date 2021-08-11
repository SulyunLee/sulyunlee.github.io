---
title: 'Statsmodel linear regression'
date: 2021-06-29
permalink: /posts/statsmodel_lr
tags:
  - linear regression
  - Python
  - statsmodel
---

In `statsmodel` package in Python, there are various built-in functions for statistical analysis. Linear regression is a statistical model that finds the linear relationships between feature variables and a target variable. Since linear regression models provide the coefficients of each feature variable that indicates the magnitude of impacting the target variable, given other variables. Therefore, it enables the explanations of which feature variables are associated with the target variable. While `sklearn` package in Python also provides the linear regression built-in function, it is not suitable for statistical analysis, since the confidence intervals and p-values of feature coefficients are not easy to obtain.

I implemented a script that fits a linear regression model using `statsmodel` package. Before feeding the feature variables into a linear regression model, three things need to be done: 1) Variance inflation factor analysis, 2) standardization, and 3) log-transformation
The following packages are needed:
```python
import numpy as np
import statsmodels.api as sm
import statsmodels.stats.outliers_influence import variance_inflation_factor
from sklearn.preprocessing import scale
```

## Variance inflation factor (VIF) analysis
Variance inflation factor analysis is required to remove the possible multicolinearity problem. Multicolinearity is more than one feature variables are correlated with each other. This is the basic assumption of linear regression that all feature variables are independent. VIF measures the amount of multicolinearity of a feature variable with other variables. Therefore, if VIF value is big for a feature variable, it means that this variable is highly correlated with other variables, thus should be removed from the model.

The formula of VIF of a feature variable <img src="https://render.githubusercontent.com/render/math?math=i"> is as follows:<br>
<img src="https://render.githubusercontent.com/render/math?math=VIF_{i} = \frac{1}{1-R_{i}^2}"><br>
<img src="https://render.githubusercontent.com/render/math?math=R_{i}^2"> is the coefficient of determination (also known as R-squared), which measures how one variable can be explained by other variables. The range of <img src="https://render.githubusercontent.com/render/math?math=R_{i}^2"> is between 0.0 and 1.0, and <img src="https://render.githubusercontent.com/render/math?math=R_{i}^2 = 0.0"> means that other variables failed to predict the variable <img src="https://render.githubusercontent.com/render/math?math=i"> at all, where <img src="https://render.githubusercontent.com/render/math?math=R_{i}^2 = 1.0"> means that other variables perfectly fit the variable <img src="https://render.githubusercontent.com/render/math?math=i"> with the perfect predictions.
Therefore, if <img src="https://render.githubusercontent.com/render/math?math=R_{i}^2"> is big, it means that other variables are highly correlated with the variable <img src="https://render.githubusercontent.com/render/math?math=i">, giving much bigger value for VIF.

In the following code, I used `statsmodel` package `variance_inflation_factor` built-in function to calculate the VIF for every feature variable and remove the variable if VIF value is greater than 10.0 (which is common threshold value). This is repeated while none of the feature variables have the VIF over 10.0.

```python
def vif(X, threshold=10.0):
  '''
  - X: the numpy array of feature vector of size (N x f), where N is the number of instances 
       and f is the number of feature variables.
  - threshold: the float number to set as the cutoff of VIF values for removing feature variables 
       with multi-colinearity. The default is 10.0.
  '''
  dropped=True
  while dropped:
    variables = X.columns
     dropped = False
     vif = [variance_inflation_factor(X[variables].values, X.columns.get_loc(var)) for var in X.columns]
     max_vif = max(vif)
     if max_vif > threshold:
      max_index = vif.index(max_vif)
      X = X.drop([X.columns.tolist()[max_index]], axis=1)
      dropped=True
      
  return X

```

## Standardization
The next step is to standardize all feature variables. Some feature variables have wide range of values in case of continuous variables, while some feature variables have very small value ranges. This might cause some problems because a feature variable with a wide value range might influence the model more than other variables. For example, assume there are two feature variables, annual income and the number of family members in predicting the annual household expense.
The annual income values might be very wide with the minimum value of 0 and the maximum value of billions or trillions of dollars! But the range of the number of family members is limited, mostly less than 10.
If we use the raw feature values, the income features might influence the model a lot. Therefore, we need to standardize the feature vectors to have the similar ranges of values.
There are many ways of standardization, but I usually use mean-zero standardization method that shifts the variables to be centered around 0 with 2-standard deviation.

In the following code, I used the `scale` built-in function from `sklearn` package


