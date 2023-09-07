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

## Admissible:

In order for a Heuristic to be admissible, it must never overestimate the actual cost.
h(n) < h*(n) where h*(n) is the true cost to a nearest goal

Manhattan Distance is always less than the true cost.

Most of the work in solving hard search problems optimally is coming up with admissable heuristics

Relaxed problems are where some constraints are removed. For example, removing walls in pacman.

### Inventing admissible heuristics

- Can be derived from the exact solution cost of a relaxed version of the problem
- Relaxed problem always easier to solve, hence admissible

## Consistency

A heuristic function h(n) is said to be consistent, or sometimes called monotonic, if for every node n and its successor node n', the estimated cost of reaching the goal from n is no greater than the step cost of getting to n' plus the estimated cost of reaching the goal from n'. This property is also known as the triangle inequality. In other words, a heuristic function is consistent if the estimated cost of reaching the goal from a node is always less than or equal to the sum of the actual cost of getting to its successor node and the estimated cost of reaching the goal from that successor node.

To explain why, let's consider the consistency property:

h(n) <= c(n, n') + h(n')

This inequality states that the estimated cost of reaching a node n from the start node (according to the heuristic function h) should be less than or equal to the actual cost of moving from node n to a neighboring node n' plus the estimated cost of reaching the goal from node n'.

## Admissible VS Consistency?
Consistency implies admissibility, but the reverse is not necessarily true. In other words, all consistent heuristic functions are admissible, but not all admissible heuristic functions are consistent. A* search with a consistent heuristic function is guaranteed to find the optimal solution, but this does not necessarily hold for admissible, non-consistent heuristic functions.

## Simple Explanation

### Admissibility:
Imagine you are trying to find the shortest route to a friend's house. A map can help you find the way. Now, let's say you have a friend who always gives you directions that are longer than the shortest route. That would not be helpful, right? A heuristic function that is admissible is like having a friend who always gives you directions that are the shortest or equal to the shortest route. In other words, an admissible heuristic never overestimates the true cost to get to the goal. This can help you find the best route more efficiently.

### Consistency:
Imagine you are playing a game where you can move from one square to another. You have to move from your starting square to the end square. The game has a rule: moving from one square to a neighboring square always costs the same. A consistent heuristic is like a game rule that says you can never spend more energy moving to a square than the energy you would save by using that square to reach the end square. In other words, if you know the estimated energy you need to reach the end square from one square and the estimated energy you need to reach the end square from a neighboring square, then the energy you save by moving to that neighboring square should always be more than or equal to the energy you spend moving there. This can help you make better decisions about where to move in the game.

