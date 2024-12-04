## Overview

**Linear Programming (LP)** is a mathematical method for determining the best outcome (such as maximum profit or lowest cost) in a mathematical model whose requirements are represented by linear relationships. LP is widely used in various fields like economics, business, engineering, and military applications to optimize processes within given constraints.

In this guide, we'll cover the key concepts of linear programming, how to formulate LP problems, understand their solutions, and delve into the concept of duality. We'll also work through examples to illustrate these concepts.

---

## Reducing Problems to Linear Programming

Before diving into LP, it's important to understand **problem reduction**. Reducing a complex problem to a known problem type allows us to apply existing methods to find solutions efficiently.

### Formal Definition of Reduction

To reduce a problem **Y** to a problem **X** (denoted as $( Y \leq_p X )$), we need:

1. A function $( f )$ that maps instances of $( Y )$ to instances of $( X )$.
2. $( f )$ must be **computable in polynomial time**.
3. For every instance $( y \in Y )$, $( y )$ is solvable **if and only if** $( f(y) \in X )$ is solvable.

---

## Formulating Linear Programming Problems

### Example: Maximizing Profit in Souvenir Production

**Problem Statement:**

A company produces two types of souvenirs:

- **Type-A**: Profit of $1.00 per unit.
- **Type-B**: Profit of $1.20 per unit.

Manufacturing requirements:

- **Type-A**: 2 minutes on Machine I and 1 minute on Machine II.
- **Type-B**: 1 minute on Machine I and 3 minutes on Machine II.

Available machine time:

- **Machine I**: 3 hours (180 minutes).
- **Machine II**: 5 hours (300 minutes).

**Question:** How many souvenirs of each type should the company make to maximize profit?

### Formulating the LP

1. **Define Variables:**

   Let:
   - $( x \geq 0 )$: Number of Type-A souvenirs produced.
   - $( y \geq 0 )$: Number of Type-B souvenirs produced.

2. **Objective Function:**

   Maximize profit $( P )$:
   $$
   \text{Maximize } P = 1.00x + 1.20y
   $$

3. **Constraints:**

   - **Machine I Time Constraint:**
     $$
     2x + y \leq 180
     $$
   - **Machine II Time Constraint:**
     $$
     x + 3y \leq 300
     $$
   - **Non-negativity Constraints:**
     $$
     x \geq 0, \quad y \geq 0
     $$

### Graphical Solution (Optional)

Plotting the constraints on a graph helps identify the feasible region and determine the optimal solution at one of the vertices (corner points).

---

## Key Concepts in Linear Programming

### Feasible Region and Optimal Solutions

- **Feasible Set (Region):** The set of all possible points that satisfy all constraints.
- **Vertex (Corner Point):** A point in the feasible region where constraint lines intersect.
- **Fundamental Theorem of LP:**
  - If a linear programming problem has a solution, it occurs at a vertex of the feasible set.
  - If the objective function is optimized at two adjacent vertices, it is optimized at every point on the line segment joining them, leading to infinitely many solutions.

### Existence of Solutions

Three cases for an LP problem with feasible set $( S )$ and objective function $( P )$:

1. $( S )$ is empty: No solution exists.
2. $( S )$ is unbounded:
   - LP may or may not have a solution.
   - If the objective function can increase indefinitely, there is no finite optimal solution.
3. $( S )$ is bounded:
   - LP has at least one optimal solution.

---

## Standard Form of Linear Programming

An LP is in **standard form** if:

- It's a **maximization** problem.
- All variables are **non-negative** $( x_i \geq 0 )$.
- All constraints are in the form of **inequalities** with "$( \leq )$" (less than or equal to).

**Standard LP Form:**

Maximize:
$$
Z = c_1x_1 + c_2x_2 + \dots + c_nx_n
$$

Subject to:
$$
\begin{align*}
a_{11}x_1 + a_{12}x_2 + \dots + a_{1n}x_n &\leq b_1 \\
a_{21}x_1 + a_{22}x_2 + \dots + a_{2n}x_n &\leq b_2 \\
\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \dots + a_{mn}x_n &\leq b_m \\
x_1, x_2, \dots, x_n &\geq 0
\end{align*}
$$

### Matrix Form

Using matrix notation:

- **Objective Function:**
  $$
  \text{Maximize } Z = \mathbf{c}^\top \mathbf{x}
  $$
  Where:
  - $( \mathbf{c} )$: Coefficient vector $( c_1, c_2, \dots, c_n )$.
  - $( \mathbf{x} )$: Variable vector $( x_1, x_2, \dots, x_n )$.

- **Constraints:**
  $$
  A\mathbf{x} \leq \mathbf{b}
  $$
  Where:
  - $( A )$: Coefficient matrix of size $( m \times n )$.
  - $( \mathbf{b} )$: Right-hand side vector $( b_1, b_2, \dots, b_m )$.

- **Non-negativity:**
  $$
  \mathbf{x} \geq 0
  $$

---
