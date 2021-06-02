---
alias: pretraining
---

# Transfer learning

Transfer learning is the idea of training a [[00 - neural networks|neural network]] for one task, and then reusing the weights to start training for a different task. This works because a lot of the low level features (those learned by the first layers) may be the same between the task.

In practice, one remove the output layer of the old network and adds a new one with random weights. Then one retrains either only the last layer (when there is few data available) or all layers (when there is lots of data available), or something in between. The first case is also called *pretraining* or *finetuning*.

This is useful when there is lots of data available for a related task, but not a lot of data for the actual task. Another reason may be the availability of pretrained networks online.