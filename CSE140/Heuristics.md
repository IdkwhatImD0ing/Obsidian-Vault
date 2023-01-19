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
