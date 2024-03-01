# ERA S6: Implemenattion of CNN architecture on MNIST dataset with ACC 99.4 and within 20k parameters

## Get Started
- The architecture is built on using the Convolution layers, Max pooling, Dropout layers, Batch normalization and Fully connected layer
- The network is limited to 20k parameters
- Augmentations are applied to the training dataset relevant to MNIST dataset available.
- With the Train and Test modules implemented, loss and accuracy are calculated accordingly.

## Training with multiple arguments
- Number of epochs is fixed to 18
- Below are the training method with the best training values achieved.
- Training is done with Multi step scheduler and Adam optimizer
  <pre>Test set: Average loss: 0.0191, Accuracy: 9936/10000 (99%)</pre>
- Training is done with 1 step scheduler and Adam optimizer
  <pre>Test set: Average loss: 0.0206, Accuracy: 9935/10000 (99%)</pre>
- Training is done with with 1 step scheduler and SGD optimizer
  <pre></pre>
- Training is done with 2 step scheduler and SGD optimizer
  <pre></pre>
