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

But how do we define the best representing line of the data? We optimize the slop and the intercept of the line by minimizing the distance between the regression line and each data point. 
