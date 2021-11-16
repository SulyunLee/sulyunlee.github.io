---
title: 'Linear Regression Explained and Scikit-Learn Implementation'
date: 2021-11-09
permalink: /posts/sklearn_lr
tags:
  - Linear Regression
  - Python
  - Scikit-Learn
  - Ordinary Least Squares
---

## Basics of linear regression
Linear regression is a model that estimates the linear relationships between predictor variables and outcome variables.
The simplest form of a linear regression model is when there is a single predictor variable. Here, we find a line that best represents the data points by estimating a slop and an intercept. For example, assume that we would like to predict the years of progression for diabetes using the blood sugar level. We use a linear regression to find the line that best represents the data points as follows:
<img src="https://user-images.githubusercontent.com/12605926/141190398-79bbfa6a-cc06-434f-9276-edd05d1a7876.png" width=360>

But how do we define the best representing line of the data? We optimize the slop (<img src="https://latex.codecogs.com/svg.image?\beta_1" title="\beta_1" />) and the intercept (<img src="https://latex.codecogs.com/svg.image?\beta_1" title="\beta_0" />) of the line by minimizing the distance between the regression line and each data point. More specifically, we minimize the Mean Squared Error (MSE), which is defined as follows:<br>
<img src="https://latex.codecogs.com/svg.image?MSE&space;=&space;\frac{\sum{(y_i&space;-&space;\hat{y_i})^2}}{N}" title="MSE = \frac{\sum{(y_i - \hat{y_i})^2}}{N}" />, <br>
where <img src="https://latex.codecogs.com/svg.image?y_i" title="y_i" /> is the label of the i-th data point and <img src="https://latex.codecogs.com/svg.image?\hat{y_i}" title="\hat{y_i}" /> is the predicted label of the i-th data point.
Therefore, MSE is the averaged distance from each data point to the regression line/
Our objective is to find betas, <img src="https://latex.codecogs.com/svg.image?\beta_1" title="\beta_0" /> and <img src="https://latex.codecogs.com/svg.image?\beta_1" title="\beta_1" />, which minimizes the MSE.

If we increase the number of predictors, the fitted regression line would look like: <br>
<img src="https://latex.codecogs.com/svg.image?\hat{y}&space;=&space;\beta_0&space;&plus;&space;\beta_1&space;x_1&space;&plus;&space;\dots&space;&plus;&space;\beta_n&space;x_n" title="\hat{y} = \beta_0 + \beta_1 x_1 + \dots + \beta_n x_n" />
We now have more betas to optimize for minimizing the error. How do we estimate beta values?

We can use gradient descent method for finding the optimized betas. Gradient descent is a iterative optimization process that finds 


