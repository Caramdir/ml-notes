# LeNet-5

A [[convolutional neural network|ConvNet]] created in 1998 for recognizing grayscale handwritten digits. It is described in Sections 2 and 3 of [[@lecunGradientbasedLearningApplied1998]].

Its architecture can be summarized as follows:

| Input | Filter | Output |
|-|-|-|
| 32x32x1 | 5x5, s=1 | 28x28x6
| | avg. pool, f=2, s=2 | 14x14x6
| | 5x5, s=1 | 10x10x16 |
| | avg. pool, f=2, s=2 | 5x5x16 |
| 400 | FC | 120 |
| | FC |84
| | | $\hat y$

This network has ~60K parameters and differs from more modern network in a couple of ways:

- modern networks typically use max pool layers and a softmax output
- LeNet used [[logistic function]]/[[tanh]] activations instead of [[ReLU]]
- it uses nonlinearities after pooling layers

However it also shares several approaches with more modern architectures:
- It repeats one or more [[convolutional neural network#Convolutional layer|convolutional layers]] followed by a [[convolutional neural network#Pooling layer| pooling layer]].
- $n_H$ and $n_W$ decrease as one goes deeper into the network, while $n_C$ increases.