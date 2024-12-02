The flow Problem
Example ship natural gas from natural gas from Alaska to Texas
Pipes have capacities, how to send as much gas as possible right

Max Flow Problem
Define flow as a function f E-> R+ that assigns nonnegative real values to the edges of G and satisfies two axioms

Capacity Constraint
Conservation constraint

How to solve the flow?

Method 1 use the greedy algorithm

Push on the bottleneck, then draw residual graphs

This is ford fulkerson algorithm
Given G, st, c in N+
Start with F(u,v) = 0 and Gf = G

while exists an augmenting path in G
find bottleneck
augment the flow along this path
update the residual graph Gf
