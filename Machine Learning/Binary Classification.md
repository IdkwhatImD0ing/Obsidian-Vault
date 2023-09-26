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