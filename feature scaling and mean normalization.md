---
alias: mean normalization, feature scaling
---
# Feature scaling and mean normalization

## Feature scaling

For many machine learning algorithms it is beneficial for all features to be of the same order of magnitude. For example in linear regression, if features are on a vastly different scale, then contour lines of $J$ are very skewed and gradient descent is likely to osscilate too much.

Thus one might one to bring all features roughly into a $-1 \le x_i \le 1$ range. One way is to divide by the range of values of $x_i$, i.e. divide each value by $\max x_i - \min x_i$. Another approach is to divide by the standard deviation.

## Mean normalization

Some machine learning algorithms benefit from features being roughly centered around $0$. One example might be the use of a [[sigmoid]] function, which has largest slope at $0$.

To achieve this. one might subtract the mean from each feature.

Thus for each $j \in \{1, \dots, n\}$, one could compute the mean $\mu_j$ and standard deviation $\sigma_j$ of $x_j^{(i)}$, and then replace each $x_j^{(i)}$ by $$\frac{x^{(i)}_j - \mu_i}{\sigma_i}.$$ One needs to save $\mu_i$ and $\sigma_i$ to apply the same normalization to future date on which the model is evaluated.