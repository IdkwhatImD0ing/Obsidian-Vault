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

while exists an augmenting path in G <- thjis runs ia dfs
find bottleneck
augment the flow along this path
update the residual graph Gf

Time complexity
O(|f| (E+V)) cause dfs
nmot polynomial time
|f| is flow caopacity

Proof Correctness
How do we know the algorithm terminate?
How do we know if the flow is maximum?

Cuts and Cut capacity
cut is a vertex partition of a set

A cut capacity  is the flow from a cut to a nother cut

Max Flow theorem
The ford Fulkerson algorith moutputs the maximum flow
max f |f| = min(a,b) cap(A<B)

What is a forward and backward proof?
FOrward proof. Given that an assignment exists, prove the max flow

Backward proof: Given the max flow, prove the assignment


BiPartite Graph
Graph is bipartite if the vertices can be partitioned in to two disjoing sets X and Y such that all edges go only between X and Y no edges from from X to X or from Y to Y

Bipartite Matching
A subset of edges is a matching if no two edges have a common vertex

A maximum matching is a matching with the largest possible number of edges


Solve by Reduction
Given an instance of bipartite matching
Crteate an instance of network flow
The solution to that network flolw can be easily use to find the solution to the bipartite matchin gproblem

How do reduce?
Add a source note to all X, add a sink node to all Y
All the capacities are 1

if size K, then need to find flow of K


time complexity if O(V^2+VE) = O(VE) = polynimial time



