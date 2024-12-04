The TSP consists of a salesman and a set of cities (a  
complete weighted graph). The salesman has to visit each  
one of the cities starting from a certain one and returning  
to the same city. The challenge of the problem is that the  
traveling salesman wants to minimize the total length of  
the trip.

Is it in np?
Cannot check there isno shorter ccle in polynopmial teim

Thus it follows that TSP is not  np complete


TSP decision version
Given a weighted complete graph with positive edge costs is there a hamiltonian cycle that has total cost <

Decision TSP is NP-Complete  
Proof by reduction from a HC.  
Given the input G = (V, E), construct a complete graph G’ = (V’, E’)  
with cost on each edge as follows:  
c(u,v) = 1, if edge (u,v) ∈ E  
c(u,v) = 2, otherwise.  
Claim:  
G has a HC of length k iff |TSP(G’)| = k = V

Decision TSP is NP-Complete  
G has a HC of length k iff |TSP(G’)| = k = V  
Proof.  
⟹)  
By construction a cycle of length k has the total cost of k. Here k is  
the number of vertices.

Decision TSP is NP-Complete  
G has a HC of length k iff |TSP(G’)| = k = V  
Proof.  
⟸)  
There is a tour that visits every vertex once with weight k.  
Since k=V, every edge traversed must have weight 1.  
Thus, this will create a HC of length k.

Supppose given a NP hard problem to solve

Cabn we find a polynomial teim aclgorihtm that produces a good enough solution?
An algoritjj that retunr near optimal solutions is called an approximation algorithm

Given a graph G=(V,E), find the  
minimum number of colors required to  
color vertices, so no two adjacent  
vertices have the same color.  
This is NP-hard problem.  
Let us develop a solution that is close  
enough to the optimal solution.


Greedy Approximation  
Given G = (V, E) with n vertices.  
Use the integers {1, 2, 3, ..., n} to represent colors.  
Order vertices by degree in descending order.  
Color the first vertex (highest degree) with color 1.  
Go down the vertex list and color every vertex not adjacent to it  
with color 1.  
Remove all colored vertices from the list.  
Repeat for uncolored vertices with color 2.


ormal Definition  
Let P be a minimization (convex) problem, and I be an instance of P.  
Let ALG(I) be a solution returned by an algorithm.  
Let OPT(I) be the optimal solution.  
Then ALG(I) is said to be a 𝛼-approximation algorithm for some 𝛼 > 1,  
if for ALG(I) ≤ 𝛼 ∙ OPT(I).  
These notions allow us to  
circumvent NP-hardness by  
designing polynomial-time  
algorithm with worst-case  
guarantees!

Maximization Problem  
Let P be a maximization (convex) problem, and I be an instance of P.  
Let ALG(I) be a solution returned by an algorithm.  
Let OPT(I) be the optimal solution.  
Then ALG(I) is said to be a 𝛼 -approximation algorithm for some  
0 < 𝛼 < 1, if for ALG(I) ≥ 𝛼 ∙ OPT(I).

What is 2 approximatnion?????
