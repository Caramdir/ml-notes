# Polynomial regression

Regeression with polynomial expression in the features in easy to reduce to [[linear regression]]. One simply adds new features which are monomials in the old features, e.g., $x_{n+1} = x_1^2$.

The same approach also works for other functions in the features. It is important to use [[feature scaling and mean normalization|feature scaling]], as taking powers significantly distorts the orders of magnitude of the features.