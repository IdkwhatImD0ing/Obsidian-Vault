# Types of Problems in AI Search:

Search algorithms aim to solve various types of problems. These problems can be categorized as follows:

## Single-State Problem:

These problems are both deterministic and accessible. In such scenarios, the agent has complete information about the world's state and can calculate the optimal sequence of actions to reach the goal.

**Example**: A puzzle like the 8-puzzle, where the agent can see the entire board and knows the rules. It can calculate the optimal path to solve the puzzle.

## Multiple-State Problem:

In these problems, the environment is deterministic but not fully accessible. The agent needs to reason about actions and predict states to find a solution.

**Example**: A robotic arm that needs to pick up an object, but its sensors can't fully observe the whole environment. The robot needs to reason about its actions to successfully pick up the object.

## Contingency Problem:

These are non-deterministic and inaccessible problems. Here, the agent has to employ sensors during execution and often needs to switch between search and execution phases to adapt to new information.

**Example**: A self-driving car navigating through traffic. The car needs to adapt its path in real-time based on sensor input, as both the environment and the car's actions have uncertain outcomes.

## Exploration Problem:

These problems involve an unknown state space. The agent must explore and learn about the environment while taking actions to solve the problem.

**Example**: A Mars rover exploring unknown terrain. The rover doesn't have a pre-defined map and must discover the landscape, learning to navigate while avoiding obstacles.

---
# Search Algorithms:

**Idea**: Exploring a simulated state space by generating successors to states already explored.
## Uninformed Search (Blind Search)

**Characteristic**: Explores in every direction until the goal is found.
### BFS (Breadth-First Search)

- **Description**: Explores all neighbor nodes at the present depth prior to moving on to nodes at the next depth level. Good for finding the shortest path but can be memory-intensive.

### DFS (Depth-First Search)

- **Description**: Explores as far as possible along each branch before backtracking. Less memory-intensive than BFS but not guaranteed to find the shortest path.

### Uniform Cost Search

- **Description**: Similar to BFS but sorts the frontier using the cost of the path to reach each node rather than the number of steps. It ensures the shortest path in terms of cost.

### Depth-limited Search

- **Description**: A variation of DFS with a predetermined depth limit, preventing infinite loops but possibly missing the solution.

### Iterative Deepening

- **Description**: Combines benefits of DFS and BFS. It performs depth-limited searches with increasing depth limits until the goal is found.

---
## Informed Search (Goal-Based)

- **Idea**: Estimate "desirability" for each state, then expand the most desirable ones.
### Heuristic Function

- **Role**: Estimates how good a state is or how far it is from the goal.
## Types of Heuristics:

### Greedy Best First Search

- **Mechanism**: Uses heuristics like Manhattan distance to minimize the estimated distance from the current state to the goal.
- **Limitation**: Not guaranteed to be optimal.

### A* Search (Informed Search)

- **Mechanism**: Combines cost and heuristic to find the most efficient path.
- **Termination**: Stops when the goal state is reached or all states are explored.
- Complete and Optimal

## Properties of Heuristics:

### Admissibility

- **Rule**: Must not overestimate actual cost $$ h(n) \leq h^*(n) $$, where $$h^*(n)$$ is the true cost.
- **Application**: Most efforts in optimal searching focus on devising admissible heuristics.

### Consistency

- **Definition**: $$h(n) \leq c(n, n') + h(n')$$, meaning the heuristic's estimate should never exceed the actual cost plus the estimated cost from the successor.
- **Implication**: Consistency implies admissibility but not vice versa.

### Simple Explanation

- **Admissibility**: Like a friend giving you the shortest or equal-to-shortest route.
- **Consistency**: Like a game rule ensuring you don't expend more energy than you save by moving to a new square.

---
## Function Optimization (Form of Informed Search)

The path to the goal state is irrelevant; the focus is on finding the optimal state itself.

### Iterative Improvement

- **Description**: Maintains a single current state and iteratively improves it.
- **Example**: Maximizing the value of a function \( f(x) \) by adjusting \( x \) in small steps.

### Hill Climbing

- **Description**: Continually improves the "value" of the current state by replacing it with a better successor state.
- **Drawback**: Can get stuck in local maxima.
- **Example**: Climbing a hill where each step taken is in the direction that ascends most steeply.

### Simulated Annealing

- **Description**: An extension of hill climbing. Allows "bad moves" with a certain probability to escape local maxima.
- **Example**: For the traveling salesman problem, you might randomly swap two cities in the current route and accept the new route based on a probability function.

### Genetic Algorithm

- **Description**: Models a population of individual solutions and evolves them over time using operations like mutation and crossover.
- **Use-Case**: Effective when the problem has many local maxima and the problem space is poorly understood.
- **Example**: Evolving a set of parameters to optimize a machine learning model. 