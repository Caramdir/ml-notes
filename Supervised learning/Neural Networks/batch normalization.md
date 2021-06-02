---
alias: BN
---
# Batch Normalization (BN)

In addition to [[feature scaling and mean normalization|normalizing the input]], also normalize the output of a hidden layer.

Given $Z^{[\ell]}$, compute its mean and variance
$$
	\begin{aligned}
		\mu &= \frac1m \sum_i z^{[\ell](i)} \\
		\sigma^2 &= \frac1m \sum_i (z^{[\ell](i)}- \mu)^2
	\end{aligned}
$$
and compute
$$
	\begin{aligned}
		z^{[\ell]}_{norm} &= \frac{z^{[\ell]} - \mu}{\sqrt{\sigma^2 + \epsilon}} \\
		\tilde z^{[\ell]} &= \gamma^{[\ell]} z^{[\ell]}_{norm} + \beta^{[\ell]},
	\end{aligned}
$$
where $\epsilon$ is a small number (for numerical stability) and $\beta^{[\ell]}$ and $\gamma^{[\ell]}$ are learnable parameters. Since we subtract the mean, the parameter $b^{[\ell]}$ does not do anything. Thus we have the following sequence of operations:
$$
	\cdots \to A^{[\ell-1]} \xrightarrow{W^{[\ell]}} Z^{[\ell]} \xrightarrow[BN]{\beta^{[\ell]}, \gamma^{[\ell]}} \tilde Z^{[\ell]} \to A^{[\ell]} = g^{[\ell]}(\tilde Z^{[\ell]}) \to \cdots
$$
When using [[mini-batch gradient descent|mini-batches]], one computes the mean and variance with only the data in the batch.

## Intuition

When data changes ("covariance drift"), then one needs to retrain the network. But during training, the parameters change, and hence the input to deeper layers experiences covariance drift. BN at least keeps mean and variance fixed.

Each mini-batch is scaled by the mean and variance of only that mini-batch. This adds some noise to $\tilde Z^{[\ell]}$ and has a slight regularizing effect similar to [[Supervised learning/Neural Networks/regularization|dropout regularization]]. However one should not see BN as a regularization tool.

## At test time

When evaluating at one example at a time, we do not have a mini-batch to compute $\mu$ and $\sigma$.

Thus during training we can estimate $\mu$ and $\sigma$ using [[exponentially weighted averages]] on $\mu^{\{1\}[\ell]}$, $\mu^{\{2\}[\ell]}$, .. and similarly for $\sigma^2$. We then use these values at test time.

(In practice any reasonable way to estimate $\mu$ and $\sigma^2$ should work fine.)