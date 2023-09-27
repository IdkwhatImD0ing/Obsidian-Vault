## Basics
- Predicts discrete, not continuous values.
- Linear functions can also separate data.

## Loss Functions
- **0-1 Loss**: Ideal but hard to optimize; 1 if wrong, 0 if correct.
- **Hinge/Perceptron Loss**: Provides a buffer; reaches zero loss slightly above x=0.
- **Logistic Loss**: High loss if incorrect, zero if correct.

## Logistic Regression
- For both binary and multi-class classification.
- Employs sigmoid loss.

## One-vs-All (OvA)
- **N** binary classifiers for **N** classes.
- Each classifier focuses on one class vs. all others.
  
### Pros & Cons
- Less computationally intensive.
- Limited generalization due to partial training.

## One-vs-One (OvO)
- \( \binom{N}{2} \) binary classifiers for **N** classes.
- Classifier for each pair of classes.

### Pros & Cons
- More specialized classifiers.
- Computationally expensive, hard to interpret.

## Tree-Based Methods
- Employ **C** binary classifiers.
- Function like decision trees, partitioning data into halves.

Each strategy has its own merits and drawbacks, and the choice of strategy often depends on the problem you're trying to solve.