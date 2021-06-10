---
alias: CNN, ConvNet
---
# Convolutional neural network

A *convolutional neural network* (shortened to *ConvNet*) as a [[00 - neural networks|neural network]], in which (some of) the layers compute [[Computer vision/convolution|convolutions]]. 

The three basic types of layers in a ConvNet are
- Convolutional layers
- Pooling layers
- Fully connected layers

## Convolutional layer

A convolutional layer applies [[Computer vision/convolution#Convolution over volume|convolutions over the input volume]], where the filter values are the trainable parameters.

Thus the input to a convolutional layer has size $n_H^{[\ell-1]} \times n_W^{[\ell-1]} \times n_C^{[\ell-1]}.$ The layer applies $n_C^{[\ell]}$ filters of size $f^{[\ell]} \times f^{[\ell]} \times n_C^{[\ell-1]}$ with padding $p^{[\ell]}$ and stride $s^{[\ell]}$. The output of the different filters is stacked into channels. Thus the output $A^{[\ell]}$ is of size $m \times n_H^{[\ell]} \times n_W^{[\ell]} \times n_C^{[\ell]}$, where
$$
	\begin{aligned}
	n_H^{[\ell]} & = \bigg\lfloor \frac{n_H^{[\ell-1]} + 2p^{[\ell]} - f^{[\ell]}}{s^{[\ell]}} + 1\bigg\rfloor,\\
	n_W^{[\ell]} & = \bigg\lfloor\frac{n_W^{[\ell-1]} + 2p^{[\ell]} - f^{[\ell]}}{s^{[\ell]}} + 1\bigg\rfloor.
	\end{aligned}
$$
The trainable weights are the elements of the filters, and hence of size $f^{[\ell]} \times f^{[\ell]} \times n_C^{[\ell-1]} \times n_C^{[\ell]}$. Further, there are $n_C^{[\ell]}$ biases.

### Why convolutions?

- Convolution layers allow for parameter sharing, that is one filter can detect the same feature anywhere in the image.
- Sparsity of connections: in each layer, each output value depends only on a small number of inputs.
- Translation invariance.

## Pooling layer

A *max pooling* filter of size $f$ with stride $s$ maps a 2-dimensional input $a^{[\ell -1]}$ to $a^{[\ell]}$ with 
$$
	a^{[\ell]}_{i,j} = \max(a^{[\ell-1]}_{(i-1)s+u, (j-1)s+v} \mid 1 \le u,v \le f).
$$
That is, it takes the maximum of each covered area of the image. If the input has multiple channels, then this is done on each channel independently, so that $n_C^{[\ell]} = n_C^{[\ell-1]}$.

Less commonly used is *average pooling*, where the average of the values is taken instead of the maximum.

Pooling layers are used to reduce the size of the image without affecting the number of layers. As they do not have trainable parameters, they are often not counted when specifying the number of layers a network has.

Common choices of parameters are $f=2$, $s=2$ and $f=3$, $s=2$. Usually no padding is applied.

## Fully connected layer

A *fully connected layer* or *dense layer* is affine linear layer as described in [[00 - neural networks]], i.e. one that flattens the input into an array if necessary and then applies an affine linear function on the whole input at once. They are usually used at the end of a ConvNet before applying say a [[multi-class classification|softmax]] output layer.