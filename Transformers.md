Attention is really important

Imagine a lot of queries
we can stack them into a matrix Q
Similarily for keys K and Values V
Think of attention as 
a(Q,K,V) = softmax(QTK/sqrt(dk))V


Now imagine we have a collection of sepearely parameterized attention function
each has own queries keys and values

These are heads
And operate in parallel
Thus multihead attention


mha(Q,K,V) = concatenate h i = 1(A(QWQ, KWK, VWV))WO