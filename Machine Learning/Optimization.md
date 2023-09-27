## Overview
- Techniques for optimization in machine learning.
- Aim to find a minimum of a function.

## Gradient Descent (GD)
- **Basic Idea**: Move in the direction of the negative gradient to find a minimum.
- **Computational Load**: High, as it requires the full dataset to compute each update.
- **Best for**: Small to medium-sized datasets.

## Stochastic Gradient Descent (SGD)
- **Basic Idea**: Approximate the true gradient using a subset of the data.
- **Noise**: Moves in a "noisy" negative gradient direction, allowing escape from local minima.
- **Best for**: Large-scale problems where GD is computationally infeasible.

### Variants and Extensions
- **Mini-batch SGD**: Uses a mini-batch of samples to approximate the gradient, a compromise between GD and full SGD.
- **Momentum**: Accelerate SGD by taking into account past gradients.
- **Adaptive Learning Rate**: Such as Adagrad, RMSprop, or Adam, adapt the learning rates during training.

### When to Use What
- Use GD for small datasets or for convex problems where reaching the exact minimum is crucial.
- Use SGD or its variants for large-scale or non-convex optimization problems.
