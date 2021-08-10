---
title: 'Blog Post number 2'
date: 2021-06-29
permalink: /posts/statsmodel_lr
tags:
  - linear regression
  - Python
  - statsmodel
---

In `statsmodel` package in Python, there are various built-in functions for statistical analysis. Linear regression is a statistical model that finds the linear relationships between feature variables and a target variable. Since linear regression models provide the coefficients of each feature variable that indicates the magnitude of impacting the target variable, given other variables. Therefore, it enables the explanations of which feature variables are associated with the target variable. While `sklearn` package in Python also provides the linear regression built-in function, it is not suitable for statistical analysis, since the confidence intervals and p-values of feature coefficients are not easy to obtain.

I implemented a script that fits a linear regression model using `statsmodel` package. Before feeding the feature variables into a linear regression model, two things need to be done: Variance inflation factor analysis and standardization.

## Variance inflation factor (VIF) analysis
Variance inflation factor analysis is required to remove the possible multicolinearity problem. Multicolinearity is more than one feature variables are correlated with each other. This is the basic assumption of linear regression that all feature variables are independent. VIF measures the amount of multicolinearity of a feature variable with other variables. Therefore, if VIF value is big for a feature variable, it means that this variable is highly correlated with other variables, thus should be removed from the model.

The formula of VIF is as follows:
![](./images/vif.png)

