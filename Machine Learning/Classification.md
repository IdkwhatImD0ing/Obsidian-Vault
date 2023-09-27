Predicts discrete values, not continuous

But can also use linears for classifications
Seperate data using linear function

In Linear Regression, we used mean squared or mean absolute error, but now we have to use a different one.

Most natural is 0-1 loss, but hard to optimize.
Meaning is prediction is wrong, loss is 1, correct, loss is 0
No continuous function

One we can use is hinge, or perceptron loss
Hinge has some buffer, loss goes to 0 slightly above x = 0
Logistic loss as well.
Basic idea, if incorrect, loss is high, if correct, loss is 0

### Logistic Regression

Use logistic regression for both Binary Regression and MultiClass regression
Use sigmoid loss

### One-vs-All (OvA) or One-vs-the-Rest (OvR):

In the OvA strategy, you train one binary classifier per class, but against all the other classes. If there are \(N\) classes, you'll have \(N\) different binary classifiers.

For example, let's say you're classifying data into three classes: A, B, and C. You would:

1. Train a classifier for Class A against Classes B and C.
2. Train a classifier for Class B against Classes A and C.
3. Train a classifier for Class C against Classes A and B.

To make a prediction for a new instance, all \(N\) classifiers predict the class label. The classifier that predicts "yes" with the highest confidence determines the output class.

#### Advantages of OvA:

- You only need to train \(N\) classifiers, which is computationally less intensive when \(N\) is large.
- Each classifier only needs to be trained on a portion of the training set (the samples that belong to its class and the samples that don't).

#### Disadvantages of OvA:

- Each classifier is only trained on a subset of the data, so it may have limited generalization.
- The classifiers may be imbalanced in terms of the number of positive and negative samples, especially if the class distribution is skewed.

### One-vs-One (OvO):

In the OvO strategy, a binary classifier is trained for every pair of classes. If there are \(N\) classes, you'll have \( \binom{N}{2} = \frac{N \times (N-1)}{2} \) classifiers.

Using the same example of three classes: A, B, and C:

1. Train a classifier for Class A against Class B.
2. Train a classifier for Class A against Class C.
3. Train a classifier for Class B against Class C.

For a new instance, you would run it through all the \( \binom{N}{2} \) classifiers and see which class wins the most "duels."

#### Advantages of OvO:

- Each classifier only needs to be trained on the subset of the training set for the two classes it must distinguish, making it more specialized.
- It can perform better if the distribution of classes is heavily imbalanced.

#### Disadvantages of OvO:

- The number of classifiers is \( \binom{N}{2} \), which can be computationally intensive and slow both in training and classification, especially as \(N\) grows.
- Due to a large number of classifiers, the algorithm can be harder to interpret and troubleshoot.

## Tree Based Method

Idea: train C binary classifiers to learn belongs to which half?
Like a decision tree