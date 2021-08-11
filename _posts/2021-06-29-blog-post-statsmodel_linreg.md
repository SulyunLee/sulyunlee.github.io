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

I implemented a script that fits a linear regression model using `statsmodel` package. Before feeding the feature variables into a linear regression model, two things need to be done: 1) Variance inflation factor analysis and 2) standardization.
The following packages are needed:
```Python
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

In the following code, I used `statsmodel` package `variance_inflation_factor` built-in function to calculate the VIF for every feature variable and remove the variable if VIF value is greater than 10.0 (which is common threshold value).

```Python
import numpy as np

def vif(X, threshold=10.0):
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


