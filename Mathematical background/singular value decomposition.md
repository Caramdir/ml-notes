---
alias: SVD, pseudo-inverse
---
# Singular value decomposition

The *singular value decomposition* (or *SVD*) of a real $m \times n$ matrix $A$ is a decomposition
$$
	A = USV^T
$$
with $U$ an $m\times m$  orthogonal matrix (i.e. $U^TU = UU^T = \mathrm{Id}_m$), $V$ an $n \times n$ orthogonal matrix and $S$ is an $m \times n$ diagonal matrix with non-negative entries.

The $\min(m,n)$ entries $\sigma_i$ of S are called *singular values* of $A$. They are usually chosen to be in descending order and are then unique. The number of non-zero singular values is equal to the rank of $A$.

Geometrically, the columns of $U$ and $V = (V^T)^{-1}$ give orthonormal bases and the singular values determine the "stretching" between these bases when applying $A$.

## Pseudo-inverse

The *Moore-Penrose pseudo-inverse* of $A$ is the unique matrix $A^\dagger$ with
$$
	AA^\dagger A = A, \quad
	A^\dagger A a^\dagger = A^\dagger, \quad
	(AA^\dagger)^T = AA^{\dagger} \quad \text{and} \quad
	(A^\dagger A)^T = A^\dagger A.
$$
- If $A$ is square and non-singular, $A^\dagger = A^{-1}$
- If $m > n$ and $A$ has full rank $n$, then $A^\dagger = (A^TA)^{-1}A^T$ and is a left (but not right) inverse of $A$. 
- If $m < n$ and $A$ has full rank $m$, then $A^\dagger = A^T(AA^T)^{-1}$ and $A^\dagger$ is a right (but not left) inverse to $A$.

We  note that the same formulas appear in the [[linear regression#Normal equation|normal equation]].

If $A$ has rank $r$ and its SVD is $USV^T$, then
$$
	A^\dagger = V\, \mathrm{diag}(\sigma_1^{-1}, \dots, \sigma_r^{-1}, 0, \dots, 0)\, U^T
