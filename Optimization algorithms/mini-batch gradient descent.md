# Mini-batch gradient descent

Update the [[parameters]] after computing only a portion of the training data.

Divide the [[training set]] into batches of size $b$. Then use [[gradient descent]] on each batch separately.

0. Randomly shuffle $X$.
1. Divide $X$ into batches $X^{\{t\}}$ of size $b$ (except possibly the last batch).
2. 
	> Repeat:
	>> For each $t$:
	>>> Do one step of gradient descent using only the data from $X^{\{t\}}$.

If $b=1$, then this is [[stochastic gradient descent]]. If $b = m$, then this is [[gradient descent|batch gradient descent]].

For intermediate $b$, since the parameters are updated more frequently, mini-batch gradient descent should converge faster than batch gradient descent. Compared to stochastic gradient descent, it has the advantage of being vectorizable.

Since one only processes a small portion of the data set in each iteration of the inner loop, there will be noise in the optimization process and not each step will go necessarily in the right overall direction. In particular, mini-batch gradient descent will wander around the true minimum rather than converging. This can be alleviated by starting with a lower learning rate or with [[learning rate decay]].

Typical batch sizes are powers of 2 between 64 and 1024. When choosing batch sizes it is important to make sure that each batch fits into CPU/GPU memory on the chosen architecture.

## Checking for convergence
One would like to avoid having to compute the full cost function.
Thus before learning compute the cost of each individual $(x^{(i)}, y^{(i)})$ before updating. Every (say) 1000 iterations plot the cost averaged over the last 1000 examples.