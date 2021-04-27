---
alias: K-means
---
# K-means algorithm

An algorithm for [[00 - clustering]].

1. Randomly initialize $K<m$ cluster centroids $\mu_1,\dots,\mu_K$ in feature space.
2. Iterate:
	1. Assign each data point to the closest cluster centroid: let $c^{(i)}$ be the index of the centroid closest to $x^{i}$.
	2. Move each centroid to the mean of the data points assigned to that centroid (if no points are assigned to a centroid, eliminate it or move it randomly).

The optimization objective here is
$$
	J(c^{(1)},\,\dots,\,c^{(m)},\, \mu_1,\,\dots,\,\mu_K) =
	\frac1m \sum_{i=1}^m \lVert x^{(i)} - \mu_{c^{(i)}} \rVert^2.
$$
Not that $J$ is guaranteed to decrease (non-strictly) in each step of the iteration.

For step 1 (random initialization), randomly pick $K$ distinct training examples and set $\mu_1,\,\dots,\,\mu_K$ to these examples.

The K-means algorithm can get stuck in local optima. So it is good to run in several times with different random initialization and pick the run with lowest $J$. This is less important when there are many clusters.

## Choosing the number of clusters

It is not always clear a priori how many clusters there should be.

One way to chose is is *elbow method*: plot $J$ versus the number of clusters and take the point where the curve starts to flatten out.

Always consider how well the number of clusters/obtained clusters work for downstram purposes (e.g. how many market segments are needed).