## Overview
- Predicts continuous values.
- Employs optimization to minimize error.

## Objective
- Minimize Total Squared Error.
- Employ Residual Sum of Squares as a function of weights \(w\).

## Key Concepts
- **Empirical Risk Minimizer**: Also known as the least squares solution.
- **Weights \(w\)**: Determine feature impact on prediction.

## Optimization
- Can be applied to various algorithms, but has a closed-form solution in the case of linear regression.
  
### Method
1. **Stationary Points**: The goal is to find points where the gradient (derivative) is zero.
2. **General Idea**: Take the derivative, set it to zero, and solve for the desired parameter \(w\).

Linear Regression serves as a foundational algorithm for supervised learning, offering closed-form solutions for optimization, which can be computationally efficient.