---
layout: inner
title: "A Network-Based MRQAP Analysis of County-to-County Migration in California"
permalink: /MRQAP/
---
<br><br>
In the previous post on community analysis in California counties, migration patterns were examined and a network was constructed. This post extends the analysis by applying the MR-QAP method.

## 1. ❓ MR-QAP

Multiple Regression Quadratic Assignment Procedure (MR-QAP) is a specialized regression analysis method designed to analyze network data. Traditional regression analysis operates on the assumption that each data point is independent of each other, but network data is not. For example, the number of people moving from county A to county B can be affected by the movement from county A to county A or their relationship with other counties, so all observations have an interdependent structure. Because of these characteristics, applying general regression analysis as it is can significantly reduce statistical reliability.To address these issues, MR-QAP performs a regression analysis between the dependent and independent variable matrices, and then evaluates the significance of the regression results using a permutation-based test. A permutation test is a method of randomly mixing rows and columns of a dependent variable matrix, repeating the same regression analysis thousands of times to create a random distribution, and then comparing how extreme the actual regression results are in that distribution. This allows you to calculate the p-value and test whether the influence of that variable is statistically significant. This method is particularly effective when dealing with data on relationships in matrix form, such as population movement between regions, social networks, and interactions between organizations. In this analysis, MR-QAP was used to evaluate what socioeconomic factors might explain population movement between 58 counties in California.
