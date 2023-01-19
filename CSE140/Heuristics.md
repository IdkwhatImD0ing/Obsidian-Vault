## Definition:

### Blind Search
BFS, DFS are all blind searches. They go in every direction until they find the goal.

### Goal-Based Search
Heuristics use a function to determine how far away they are from a goal. Then they try to lower that.

## Informed Decision:

Add domain-specific information to select the best path along which to continue searching.

### Heuristic Function
Determine "how good" a state is. How far the state is from the goal. Not true cost

## Different Heuristics:

### Greedy Best First Search

If using manhattan distance, minimizes distance from state to goal.

Not optimal.

### Informed Search (A* Search)

Combine Cost with Heuristics to Minimize Path
For example, add the cost along with the heuristic. That way an optimal path with a high cost would be considered suboptimal.

A* Search terminates when it reaches a goal state or visits all possible states

### Admissible:

In order for a Heuristic to be admissible, it must never overestimate the actual cost.
h(n) < h*(n) where h*(n) is the true cost to a nearest goal

Manhattan Distance is always less than the true cost.

Most of the work in solving hard search problems optimally is coming up with admissable heuristics

Relaxed problems are where some constraints are removed. For example, removing walls in pacman.

## Inventing admissible heuristics

- Can be derived from the exact solution cost of a relaxed version of the problem
- Relaxed problem always easier to solve, hence admissible
