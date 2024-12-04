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