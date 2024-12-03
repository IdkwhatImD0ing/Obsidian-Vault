## Introduction

In the previous part, we discussed the **Ford-Fulkerson Algorithm** for solving the Max Flow Problem, where we used **Depth-First Search (DFS)** to find augmenting paths. Now, we'll explore what happens if we use **Breadth-First Search (BFS)** instead. This leads us to the **Edmonds-Karp Algorithm**, an important variation that guarantees polynomial-time performance.

## The Edmonds-Karp Algorithm

### Why Use BFS Instead of DFS?

- **DFS** can find any augmenting path, which might not be the most efficient.
- **BFS** finds the shortest augmenting path in terms of the number of edges.
- Using BFS ensures that we make the most significant progress towards maximizing flow in each iteration.

### Algorithm Overview

The **Edmonds-Karp Algorithm** is essentially the Ford-Fulkerson method implemented with BFS to find the shortest augmenting paths.

#### Steps:

1. **Initialization**:
   - Start with a flow $f(e) = 0$ for all edges $e$.
   - Construct the initial **residual graph** $G_f$.

2. **While there is an augmenting path from $s$ to $t$ in $G_f$**:
   - Use **BFS** to find the shortest path from the source $s$ to the sink $t$.
   - **Determine the Bottleneck Capacity ($\delta$)**:
     - Find the minimum residual capacity along this path.
   - **Augment the Flow**:
     - Increase the flow along the path by $\delta$.
   - **Update the Residual Graph**:
     - Adjust capacities to reflect the new flow.

3. **Termination**:
   - When no more augmenting paths exist, the algorithm concludes with the maximum flow.

### Time Complexity

- The Edmonds-Karp Algorithm runs in **$O(V E^2)$** time, where $V$ is the number of vertices and $E$ is the number of edges.
- This is because:
  - Each augmentation increases the shortest path length for at least one edge.
  - Each edge can have its shortest path length increased at most $V$ times.
  - Therefore, there are at most $O(V E)$ augmentations.
  - Each BFS operation takes $O(E)$ time.
- **Result**: The algorithm operates in polynomial time, which is more efficient and predictable than the basic Ford-Fulkerson method.

## Problem Reduction and Network Flow

### Reducing Problems to Network Flow

Often, complex problems can be solved efficiently by transforming them into a network flow problem.

#### Formal Definition of Reduction:

To reduce a problem **Y** to a problem **X** (denoted as **$Y \leq_p X$**), we need:

- A function **$f$** that maps instances of **Y** to instances of **X**.
- **$f$** must be **computable in polynomial time**.
- For every instance **$y \in Y$**, **$y$** is solvable if and only if **$f(y) \in X$** is solvable.

### Steps for Solving by Reduction to Network Flow

1. **Construct a Flow Network**:
   - Define how the original problem maps to a network with capacities, sources, and sinks.

2. **Make a Claim**:
   - State that the original problem has a solution if and only if the network flow satisfies a certain condition (e.g., the maximum flow equals a specific value).

3. **Prove the Claim in Both Directions**:
   - **Forward Direction**: Show that if the original problem has a solution, then the network flow condition holds.
   - **Backward Direction**: Demonstrate that if the network flow condition holds, then the original problem has a solution.

### Example: Bipartite Matching (Refer to Part One)

In Part One, we reduced the bipartite matching problem to a network flow problem by:

- Creating a flow network with capacities of 1.
- Claiming that the size of the maximum matching equals the value of the maximum flow.
- Proving this claim by showing the correspondence between matchings and flows.

## Circulation with Demands and Lower Bounds

### What Is a Circulation?

A **circulation** in a network is a flow that satisfies the following:

- **Capacity Constraints**:
  $$
  l(u, v) \leq f(u, v) \leq c(u, v)
  $$
  - Each edge $(u, v)$ has a lower bound $l(u, v)$ and an upper bound (capacity) $c(u, v)$.
- **Conservation Constraints**:
  $$
  \sum_{\text{incoming edges}} f(u, v) - \sum_{\text{outgoing edges}} f(v, w) = b(v)
  $$
  - For each vertex $v$, the net flow (incoming minus outgoing) equals its **demand** $b(v)$.
  - If $b(v) > 0$, $v$ is a **demand node** (it requires flow).
  - If $b(v) < 0$, $v$ is a **supply node** (it provides flow).
  - If $b(v) = 0$, $v$ is a regular node with no net flow requirement.

### Adjusting for Lower Bounds

When edges have lower bounds, we need to adjust the network to find a feasible circulation.

#### Steps:

1. **Adjust Edge Capacities**:
   - For each edge $(u, v)$ with lower bound $l(u, v)$ and capacity $c(u, v)$:
     - **Modify the capacity** to be $c'(u, v) = c(u, v) - l(u, v)$.
     - This ensures that the flow above the lower bound fits within the adjusted capacity.

2. **Adjust Vertex Demands**:
   - For each vertex $v$, calculate the total lower bounds on incoming and outgoing edges:
     - **Total incoming lower bounds**:
       $$
       L_{\text{in}}(v) = \sum_{(u, v) \in E} l(u, v)
       $$
     - **Total outgoing lower bounds**:
       $$
       L_{\text{out}}(v) = \sum_{(v, w) \in E} l(v, w)
       $$
   - **Modify the demand**:
     $$
     b'(v) = b(v) + L_{\text{in}}(v) - L_{\text{out}}(v)
     $$
   - This adjusts for the mandatory flow due to lower bounds.

3. **Solve the Adjusted Circulation Problem**:
   - Use standard network flow techniques (like the Ford-Fulkerson Algorithm) to find a circulation in the adjusted network.

4. **Recover the Original Flow**:
   - **Add back the lower bounds** to the flow on each edge:
     $$
     f(u, v) = f'(u, v) + l(u, v)
     $$
   - This gives the flow in the original network with the correct lower bounds.

### Why This Works

- By adjusting capacities and demands, we transform the problem into one without lower bounds, which is easier to solve.
- The adjusted network ensures that any feasible flow corresponds to a feasible circulation in the original network.

### Example: Circulation with Demands

Suppose we have a network with the following edges and demands:

- **Edges**:
  - $(u, v)$ with capacity $c(u, v)$ and lower bound $l(u, v)$.
- **Vertices**:
  - Vertex $v$ with demand $b(v)$.

**Steps**:

1. **Adjust Capacities**:
   - For each edge, compute $c'(u, v) = c(u, v) - l(u, v)$.

2. **Adjust Demands**:
   - For each vertex, calculate $b'(v) = b(v) + L_{\text{in}}(v) - L_{\text{out}}(v)$.

3. **Solve Circulation**:
   - Find a flow $f'(u, v)$ that satisfies the capacity and conservation constraints in the adjusted network.

4. **Recover Original Flow**:
   - Compute $f(u, v) = f'(u, v) + l(u, v)$ to get the flow in the original network.

## Key Takeaways

- **Edmonds-Karp Algorithm**:
  - An efficient implementation of the Ford-Fulkerson method using BFS.
  - Guarantees polynomial-time performance ($O(V E^2)$).
- **Problem Reduction**:
  - A powerful technique to solve complex problems by transforming them into network flow problems.
  - Requires constructing a flow network, making a claim, and proving it in both directions.
- **Circulation with Demands**:
  - Extends the concept of flow to networks with supplies and demands at vertices.
  - Adjusting capacities and demands allows us to handle lower bounds on edges.
- **Applications**:
  - These concepts are widely used in transportation, logistics, and scheduling where supplies, demands, and capacity constraints are present.



