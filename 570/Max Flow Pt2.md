Ford Fulkerson Algorithm we use DFS
what if we use BFS?
BFS will return the shortest path in the numbner of edges
Theis variation is called the Edmonds Karp Algorithm

Only requires O(VE) iterations rn time is O(V*E^2) which means its polynomial!!!


Algorithm:
Given G, s, t, c
Start with |f| = 0
so f(e) = 0
Find the shortest augmenting path in Gf

augment flow along this path
repeat until there is no an s-t path in G


Formally, to reduce a problem Y to a problem X (we write Y ≤p X)  
we want a function f that maps Y to X such that:  
• f is a polynomial time computable  
• ∀instance y ∈ Y is solvable if and only if f(y) ∈ X is solvable.

Solving by reduction to NF  
1. Describe how to construct a flow network.  
2. Make a claim. Something like "this problem has a feasible  
solution if and only if the max flow is ...“.  
3. Prove the above claim in both directions.

Circulation

What is a circulation?

Given a directed graph that in addition to capacities

we associate each vertex with a supply/demand value

dememand if its above 0
supply if below 0

Circulation with demands that assigns nonnnegative real values to the edges of G and satisfies two axioms

Capacity constraint and Conservation constrant