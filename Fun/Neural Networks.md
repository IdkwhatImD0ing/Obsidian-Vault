### Neurons
Neurons take in an input and has weights that outputs a temporary
Neurons contain weights and biases
The temporary is the value that comes out of the neuron
The temporary values are then fed into the next neuron

### Activation Functions
Activation functions determine if neurons activate or not
Examples include Sigmoid, ReLu, Leaky ReLu etc. 

### Layers
Composed of multiple layers, each layer is connected to the previous and next layer, unless its an input or prediction layer

## Goals of a NN
Minimize loss. Loss is determined by a custom loss function.

### Gradient Descent
Based on derivatives
If loss is increasing and weights are increasing, decreasing weights should decrease loss
And vice versa

Goal is to get to the global minimum; however, local minimum can give problems.