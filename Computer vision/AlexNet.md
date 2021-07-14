# AlexNet

A network described in [[@krizhevskyImageNetClassificationDeep2017]]. The architecture is as follows

| Input | Filters | Output |
|-|-|-|
|227x227x3 | 11x11, s=4 | 55x55x96 |
| | max pool, f=3, s=2 | 27x27x96 |
| | 5x5, same | 27x27x256 |
| | max pool, f=3, s=2 | 13x13x256 |
| | 3x3, same | 13x13x385 |
| | 3x3, same | 13x13x385 |
| | 3x3, same | 13x13x256
| | max pool, f=3, s=2 | 6x6x256 |
| 9216 | FC | 4096 |
| | FC | 4096 |
| | softmax | 1000 |

- Similarity to [[LeNet-5]], but much bigger (~60M parameters).
- uses [[ReLU]] activations
- splits layers in complicated ways to use multiple CPUs
- includes a [[local response normalization]] (LRN), which is not much used anymore.
- convinced many people that [[deep learning]] works.