---
alias: padding, same convolution, valid convolution, stride, padded convolution, strided convolution
---
# Convolution

Viewing matrices as functions $\mathbb{Z}^2 \to \mathbb{R}$ supported on some finite subset of the first quadrant, we can define their [[Mathematical background/convolution|convolution]] as
$$
	(A * B)_{i,j} = \sum_{\ell_1,\ell_2} A_{i-\ell_1,j-\ell_2} B_{\ell_1,\ell_2}.
$$
As usual , one calls $B$ a *kernel*, and, if the matrix $A$ represents an image, then $B$ is also called a *filter*.

There exist different index conventions on how exactly the sum is taken. In machine learning, one usually uses the above formula, but with $A_{i+\ell_1,j+\ell_2}$ instead of $A_{i-\ell_1,j-\ell_2}$.

## Motivation

Kernels can be used to detect features in images. For example any large value in the output of convolution with
$$
	\begin{pmatrix} 1 & 0 & -1 \\ 1 & 0 & -1 \\ 1 & 0 & -1\end{pmatrix}
$$
indicates the presence of a vertical edge in the corresponding location of the input image. More examples of specific kernels are given on [Wikipedia](https://en.wikipedia.org/wiki/Kernel_(image_processing)).

## Basic convolution

Assume $A \in \mathbb{R}^{n_H \times n_W}$ and $B \in \mathbb{R}^{f_H \times f_W}$. Clipping the above formula to only those indices where $A$ and $B$ are defined we obtain
$$
	(A * B)_{i,j} =
	\sum_{\ell_1 = 1}^{f_H}\sum_{\ell_2=1}^{f_W} A_{i+\ell_1-1, j+\ell_2-1}B_{\ell_1, \ell_2} 
$$
where $1 \le i \le n_H - f_h +1$ and $1 \le j \le n_W - f_W +1$.

It is a common convention for the filter size to be odd, in which case one could instead sum over $-\frac{f_H-1}{2} \le \ell_1 \le \frac{f_H-1}{2}$ and similarly for $\ell_2$ with appropriately changed indices.

## Convolution with padding

One can apply *padding* before the convolution. That is, for a non-negative integer $p$ we view $A$ as a $(n_H+2p) \times (n_W + 2p)$ matrix by adding $p$ zeros in each direction. The resulting matrix is then of size $(n_H + 2p - f_H - 1) \times (n_W +2p - f_W - 1)$.

A padding of $p=0$ is called a *valid convolution*, while $p=\frac{f-1}2$ (with odd filter size) is called a *same convolution*. In the latter the size of $A * B$ is the same as the size of $A$.

## Strided convolution

Additionally, one can step the filter by some stride $s \ge 1$. That is, the above formula becomes
$$
	(A * B)_{i,j} =
	\sum_{\ell_1 = 1}^{f_H}\sum_{\ell_2=1}^{f_W} A_{si+\ell_1-1, sj+\ell_2-1}B_{\ell_1, \ell_2}
$$
with output of size $\big\lfloor \frac{n_H+2p-f_H}{s} + 1\big\rfloor\ \times \big\lfloor \frac{n_W+2p-f_W}{s} + 1\big\rfloor$.

## Convolution over volume

When an image has multiple channels, i.e. is of dimension $n_H \times n_W \times n_C$, the filter needs to have the same number of channels. The output is then summed over the channels:

$$
	(A * B)_{i,j} =
	\sum_{c=1}^{n_C} \sum_{\ell_1 = 1}^{f_H}\sum_{\ell_2=1}^{f_W} A_{si+\ell_1-1, sj+\ell_2-1,c}B_{\ell_1, \ell_2,c}
$$

## Convolutions of different dimensions

Similarly, one can define convolutions for data of different dimensions, e.g. 1D (such as audio signals) or 3D (such as CT scans or movies).