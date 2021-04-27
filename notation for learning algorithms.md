# Notation for learning algorithms

The input variable (features) is denoted $x$, the output/target variable (if it exists) is $y$.

Individual pairs of training examples are $(x^{(i)}, y^{(i)})$. The dimension of the input variable is $n = n_x$, i.e. $x \in \mathbb{R^n}$ (represented as a column vector). There are $m$ training examples labeled $1$ to $m$. The matrix $X \in \mathbb{R}^{n \times m}$, called *design matrix*, is the matrix whose columns are the $x^{(i)}$, i.e.
$$
	X = \begin{pmatrix}
		| & | & & | \\
		x^{(1)} & x^{(2)} & \cdots & x^{(m)} \\
		| & | & & |
	\end{pmatrix}.
$$
Correspondingly, $Y$ is the row vector $(y^{(1)} \ \cdots \ y^{(m)}) \in \mathbb{R}^{1\times m}$.
In the [[Coursera course on machine learning]], $X$ is the transpose of this matrix, i.e., has the training examples in rows and $Y$ is the corresponding column vector of the $y^{(i)}$.