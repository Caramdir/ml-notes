---
alias: R squared
---
# Coefficient of determination

The *coefficient of determination*, usually denoted $R^2$ or $r^2$, is the proportion of the variance in the dependent variable that is predictable from the independent variable(s). It provides a measure of how well observed outcomes are predicted by the model, based on the proportion of total variation of outcomes explained by the model. 

Given a data set of $n$ observed values $y_1$, ..., $y_n$, each associated with predicted values $\hat y_1$, ..., $\hat y_n$ one has
$$
	R^2 = 1 - \frac{\sum_i (y_i - \hat y_i)^2}{\sum_i (y_i - \bar y)^2},
$$
where $\bar y = \frac1n \sum_i y_i$ is the mean of the observed data. The term in the denominator is the sum of squares of the residuals $e_i = y_i - \hat y_i$, also called *residual sum of squares* (RSS), proportional to the [[mean square error]] (MSE). The denominator is proportional to the [[Mathematical background/variance|variance]] in the observed data.  

For a [[linear regression|linear least squares regression]], $R^2$ equals the square of the [[Pearson correlation coefficient]] between the observed and modeled data. [PROOF?]