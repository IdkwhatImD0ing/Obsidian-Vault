Linaer models are not always adequadate.
We could use non linear mapping\
But is it useful and can we learn it?

Linear Model can be treated as a one layer neural net
o = h(wTx)
h(a) = a

To create non-linearity, we can use activation layers

For example
Rectified Linesr Unit (ReLU) h(a) = max{0,a}
Sigmoid function: h(a) = 1/1+e^-a
TanH h(a) = e^a-e^-a/e^a+e^-a

Powerful because Neural Networks lest us have more than one output
h is an activation function

each node is a neuron

\# of layers represents \# of hidden layers

deep neural networks have many layers and millions of parameters (w's)