# VGG-16

A [[convolutional neural network|ConvNet]] described in [[@simonyanVeryDeepConvolutional2015]].

In the following write 
- CONV $n$ for convolution with $n$ 3x3 filters, stride 1 and same padding;
- POOL for max pooling with 2x2 filters and stride 2.

| Input | Filters | Output |
|-|-|-|
|224x224x3 | 2x [CONV 64] | 224x224x64 |
| | POOL | 112x112x64 |
| | 2x [CONV 128] | 112x112x128 |
| | POOL | 56x56x128 |
| | 3x [CONV 256] | 56x56x256 |
| | POOL | 28x28x256 |
| | 3x [CONV 512] | 28x28x512 |
| | POOL | 14x14x512 |
| | 3x [CONV 512] | 14x14x512 |
| | POOL | 7x7x512 |
| 25088 | FC | 4096 |
| | FC | 4096 |
| | softmax | 1000 |

- The network has about 138M parameters.
- The paper also contains a 19 layer VGG-19
- $n_H$ and $n_W$ decrease over the network, while $n_C$ increases (by a factor of 2 in each step).