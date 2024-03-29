## Overview
- Linear models can fall short for complex data.
- Non-linear mappings can be more expressive but may require more complex learning techniques.
- Trying to mimic human brain
	- Human brain divided into regions with some functional specialization
	- Computation is driven by very large networks of rather slow neurons connected via synapses
		- Much slower than current computers
		- 10^11 neurons of > 20 types
		- 10^14 synapses
		- 1-10ms cycle time
		- Signals are noisy spike trains of electrical potential

## Neurons
- Many inputs
- Each one has a weight
	- Learning occurs by adjusting the weights
- All added together
	- If over activation, output 1
	- Else output 0
## Relation to Neural Networks
- A linear model is akin to a one-layer neural net.
- Activation functions introduce non-linearity.

### Activation Functions
- **ReLU**: \(h(a) = \max(0, a)\)
- **Sigmoid**: \(h(a) = \frac{1}{1 + e^{-a}}\)
- **TanH**: \(h(a) = \frac{e^a - e^{-a}}{e^a + e^{-a}}\)
## Deep Neural Networks
- Have multiple layers and a high number of parameters (\(w\)'s).

## Backpropagation Algorithm
1. **Initialize Weights**: Start with random values.
2. **Loop**:
  - Randomly pick a data point.
  - Forward propagate to compute \(a\) and \(o\)
	  - a stands for activations
	  - o stands for output of the network.
  - Backward propagate to compute gradients.
  - Update weights using gradients.

### Optimization Tricks
- **Mini Batch**: Sample small batches for stochastic gradients. Common sizes: 32, 64, 128.
- **Batch Normalization**: Normalize neuron inputs over a mini-batch to zero mean and unit variance.
- **Momentum**: Use past gradients to avoid local minimums.

## Handling Overfitting
- **Data Augmentation**: Modify data to increase diversity.
- **Regularization**: Penalize model complexity.
- **Dropout**: Randomly ignore some neurons during training.
- **Early Stopping**: Cease training when performance plateaus.

Neural networks allow for more expressive and flexible models compared to their linear counterparts. Techniques like backpropagation and various optimization methods enable effective learning for these complex architectures.