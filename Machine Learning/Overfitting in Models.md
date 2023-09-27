## Overview
- Overfitting occurs when training and test metrics diverge significantly.
- Methods to address overfitting include regularization and adding more data.

## Regularization
- **Basic Idea**: Penalizes complex models to prevent overfitting.
- **How It Works**: Adds a penalty term based on model weights to the loss function.
- **Types**: 
  - **Lasso (L1)**: Uses absolute value of weights; results in some weights becoming exactly zero.
  - **Ridge (L2)**: Uses square of weights; shrinks weights but doesn't make them zero.

### Key Differences:
- **Lasso**: Simplifies model by making some parameters exactly zero. Good for feature selection.
- **Ridge**: Reduces but doesn't eliminate all features. Helpful when most features are relevant.

## Adding More Data
- **Effectiveness**: Increasing the size of the training set can help the model generalize better, reducing overfit.
  
Understanding both regularization methods and the impact of adding more data helps in effectively combating overfitting in machine learning models.