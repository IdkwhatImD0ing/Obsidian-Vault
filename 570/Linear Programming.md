## Overview

**Linear Programming (LP)** is a mathematical method for determining the best outcome (such as maximum profit or lowest cost) in a mathematical model whose requirements are represented by linear relationships. LP is widely used in various fields like economics, business, engineering, and military applications to optimize processes within given constraints.

In this guide, we'll cover the key concepts of linear programming, how to formulate LP problems, understand their solutions, and delve into the concept of duality. We'll also work through examples to illustrate these concepts.

---

## Reducing Problems to Linear Programming

Before diving into LP, it's important to understand **problem reduction**. Reducing a complex problem to a known problem type allows us to apply existing methods to find solutions efficiently.

### Formal Definition of Reduction

To reduce a problem **Y** to a problem **X** (denoted as **\( Y \leq_p X \)**), we need:

1. A function **\( f \)** that maps instances of **Y** to instances of **X**.
2. **\( f \)** must be **computable in polynomial time**.
3. For every instance **\( y \in Y \)**, **\( y \)** is solvable **if and only if** **\( f(y) \in X \)** is solvable.

---

## Formulating Linear Programming Problems

### Example: Maximizing Profit in Souvenir Production

**Problem Statement:**

A company produces two types of souvenirs:

- **Type-A**: Profit of \$1.00 per unit.
- **Type-B**: Profit of \$1.20 per unit.

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
   - \( x \geq 0 \): Number of Type-A souvenirs produced.
   - \( y \geq 0 \): Number of Type-B souvenirs produced.

2. **Objective Function:**

   Maximize profit \( P \):
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

Three cases for an LP problem with feasible set \( S \) and objective function \( P \):

1. **\( S \) is empty:** No solution exists.
2. **\( S \) is unbounded:**
   - LP may or may not have a solution.
   - If the objective function can increase indefinitely, there is no finite optimal solution.
3. **\( S \) is bounded:**
   - LP has at least one optimal solution.

---

## Standard Form of Linear Programming

An LP is in **standard form** if:

- It's a **maximization** problem.
- All variables are **non-negative** (\( x_i \geq 0 \)).
- All constraints are in the form of **inequalities** with "\(\leq\)" (less than or equal to).

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
  - \( \mathbf{c} \): Coefficient vector \( (c_1, c_2, \dots, c_n) \).
  - \( \mathbf{x} \): Variable vector \( (x_1, x_2, \dots, x_n) \).

- **Constraints:**
  $$
  A\mathbf{x} \leq \mathbf{b}
  $$
  Where:
  - \( A \): Coefficient matrix of size \( m \times n \).
  - \( \mathbf{b} \): Right-hand side vector \( (b_1, b_2, \dots, b_m) \).

- **Non-negativity:**
  $$
  \mathbf{x} \geq 0
  $$

---

## Solving LPs: The Simplex Algorithm

- Developed by **George Dantzig** in 1947.
- An iterative method that moves along the edges of the feasible region to find the optimal vertex.
- **Process:**
  1. Start at an initial feasible vertex.
  2. Move to an adjacent vertex with a higher (for maximization) objective value.
  3. Repeat until no adjacent vertex improves the objective function.

**Note:** While the Simplex Algorithm is efficient in practice, it doesn't guarantee polynomial-time performance in the worst case.

---

## Example: Cargo Plane Optimization

**Problem Statement:**

A cargo plane has:

- **Maximum Weight Capacity:** 100 tons.
- **Maximum Volume Capacity:** 60 cubic meters.

Available materials:

| Material   | Density (tons/m³) | Maximum Volume (m³) | Price (\$/m³)   |
|------------|-------------------|---------------------|-----------------|
| Material 1 | 2                 | 40                  | \$1,000         |
| Material 2 | 1                 | 30                  | \$2,000         |
| Material 3 | 3                 | 20                  | \$12,000        |

**Question:** Determine how much of each material to transport to maximize revenue.

### Formulating the LP

1. **Define Variables:**

   Let:
   - \( x_1 \geq 0 \): Volume of Material 1.
   - \( x_2 \geq 0 \): Volume of Material 2.
   - \( x_3 \geq 0 \): Volume of Material 3.

2. **Objective Function:**

   Maximize revenue \( R \):
   $$
   \text{Maximize } R = 1000x_1 + 2000x_2 + 12000x_3
   $$

3. **Constraints:**

   - **Weight Capacity:**
     $$
     2x_1 + x_2 + 3x_3 \leq 100
     $$
   - **Volume Capacity:**
     $$
     x_1 + x_2 + x_3 \leq 60
     $$
   - **Material Availability:**
     $$
     0 \leq x_1 \leq 40 \\
     0 \leq x_2 \leq 30 \\
     0 \leq x_3 \leq 20
     $$

### Matrix Form (Optional)

- **Objective Coefficient Vector:**
  $$
  \mathbf{c} = \begin{bmatrix} 1000 \\ 2000 \\ 12000 \end{bmatrix}
  $$

- **Constraint Matrix \( A \) and Vector \( \mathbf{b} \):**
  $$
  A = \begin{bmatrix}
  2 & 1 & 3 \\
  1 & 1 & 1 \\
  1 & 0 & 0 \\
  0 & 1 & 0 \\
  0 & 0 & 1
  \end{bmatrix}, \quad
  \mathbf{b} = \begin{bmatrix} 100 \\ 60 \\ 40 \\ 30 \\ 20 \end{bmatrix}
  $$

---

## Duality in Linear Programming

**Duality** is a fundamental concept where every linear programming problem (the **primal**) has an associated **dual** problem.

### Primal and Dual Problems

- **Primal LP (Standard Maximization Form):**

  Maximize:
  $$
  Z = \mathbf{c}^\top \mathbf{x}
  $$
  Subject to:
  $$
  A\mathbf{x} \leq \mathbf{b} \\
  \mathbf{x} \geq 0
  $$

- **Dual LP (Standard Minimization Form):**

  Minimize:
  $$
  W = \mathbf{b}^\top \mathbf{y}
  $$
  Subject to:
  $$
  A^\top \mathbf{y} \geq \mathbf{c} \\
  \mathbf{y} \geq 0
  $$

Where:

- \( \mathbf{y} \): Dual variables corresponding to the primal constraints.
- \( A^\top \): Transpose of matrix \( A \).

### Relationship Between Primal and Dual

- **Weak Duality Theorem:**
  - The optimal value of the primal (maximization) problem is **less than or equal to** the optimal value of the dual (minimization) problem.
  $$
  Z_{\text{max}} \leq W_{\text{min}}
  $$
- **Strong Duality Theorem:**
  - If both the primal and dual problems have feasible solutions, their optimal values are equal.
  $$
  Z_{\text{max}} = W_{\text{min}}
  $$

---

## Example: Writing the Dual of a Primal LP

**Primal LP:**

Maximize:
$$
Z = 7x_1 - x_2 + 5x_3
$$

Subject to:
$$
\begin{align*}
x_1 + x_2 + 4x_3 &\leq 8 \quad (1) \\
3x_1 - x_2 + 2x_3 &\leq 3 \quad (2) \\
2x_1 + 5x_2 - x_3 &\leq -7 \quad (3) \\
x_1, x_2, x_3 &\geq 0
\end{align*}
$$

**Task:** Write the dual problem.

### Steps to Formulate the Dual

1. **Identify Primal Components:**

   - **Objective Coefficients (\( \mathbf{c} \)):**
     $$
     \mathbf{c} = \begin{bmatrix} 7 \\ -1 \\ 5 \end{bmatrix}
     $$

   - **Constraint Matrix (\( A \)):**
     $$
     A = \begin{bmatrix}
     1 & 1 & 4 \\
     3 & -1 & 2 \\
     2 & 5 & -1
     \end{bmatrix}
     $$

   - **Right-hand Side Vector (\( \mathbf{b} \)):**
     $$
     \mathbf{b} = \begin{bmatrix} 8 \\ 3 \\ -7 \end{bmatrix}
     $$

2. **Write the Dual Variables:**

   Let \( y_1, y_2, y_3 \geq 0 \) be the dual variables corresponding to the primal constraints.

3. **Formulate the Dual Objective Function:**

   Minimize:
   $$
   W = 8y_1 + 3y_2 -7y_3
   $$

   **Note:** The right-hand side vector \( \mathbf{b} \) has a negative component (\( -7 \)). In standard dual formulation, we consider \( \mathbf{b} \) as is.

4. **Write the Dual Constraints:**

   The constraints of the dual come from the coefficients in the primal objective function and the transpose of matrix \( A \).

   - **Transpose of \( A \) (\( A^\top \)):**
     $$
     A^\top = \begin{bmatrix}
     1 & 3 & 2 \\
     1 & -1 & 5 \\
     4 & 2 & -1
     \end{bmatrix}
     $$

   - **Dual Constraints:**
     $$
     \begin{align*}
     1y_1 + 3y_2 + 2y_3 &\geq 7 \quad (x_1) \\
     1y_1 - 1y_2 + 5y_3 &\geq -1 \quad (x_2) \\
     4y_1 + 2y_2 -1y_3 &\geq 5 \quad (x_3) \\
     y_1, y_2, y_3 &\geq 0
     \end{align*}
     $$

5. **Final Dual LP:**

   Minimize:
   $$
   W = 8y_1 + 3y_2 -7y_3
   $$

   Subject to:
   $$
   \begin{align*}
   y_1 + 3y_2 + 2y_3 &\geq 7 \\
   y_1 - y_2 + 5y_3 &\geq -1 \\
   4y_1 + 2y_2 - y_3 &\geq 5 \\
   y_1, y_2, y_3 &\geq 0
   \end{align*}
   $$

**Note on Negative Right-hand Side:**

- The presence of a negative \( b_i \) in the primal constraints can complicate the standard dual formulation.
- To handle negative right-hand sides, we can transform the primal constraints to have non-negative \( b_i \) by multiplying the entire constraint by \( -1 \) if necessary.

### Adjusting for Negative Right-hand Side

For the constraint:
$$
2x_1 + 5x_2 - x_3 \leq -7
$$
Multiply both sides by \( -1 \):
$$
-2x_1 - 5x_2 + x_3 \geq 7
$$
This transforms the inequality to a standard \( \geq \) form, suitable for dual formulation.

**Updated Primal Constraints:**

1. \( x_1 + x_2 + 4x_3 \leq 8 \)
2. \( 3x_1 - x_2 + 2x_3 \leq 3 \)
3. \( -2x_1 - 5x_2 + x_3 \geq 7 \)

Now, the third constraint corresponds to a dual variable \( y_3 \) without the need to adjust the dual formulation.

**Rewriting the Dual LP:**

Minimize:
$$
W = 8y_1 + 3y_2 + 7y_3
$$

Subject to:
$$
\begin{align*}
y_1 + 3y_2 -2y_3 &\geq 7 \\
y_1 - y_2 -5y_3 &\geq -1 \\
4y_1 + 2y_2 + y_3 &\geq 5 \\
y_1, y_2, y_3 &\geq 0
\end{align*}
$$

---

## Understanding Duality Theorems

### Weak Duality Theorem

For any feasible solution \( \mathbf{x} \) of the primal LP and \( \mathbf{y} \) of the dual LP:
$$
\mathbf{c}^\top \mathbf{x} \leq \mathbf{b}^\top \mathbf{y}
$$
- **Interpretation:** The value of the objective function for any feasible solution of the primal is less than or equal to that for any feasible solution of the dual.

### Strong Duality Theorem

If both the primal and dual problems have feasible solutions, then their optimal objective values are equal:
$$
Z_{\text{max}} = W_{\text{min}}
$$

**Implication:** Solving either the primal or dual provides the solution to both problems.

---

## Summary of Key Concepts

- **Linear Programming:** A method to achieve the best outcome in a mathematical model with linear relationships.
- **Standard Form:** LP problems are often converted to a standard form for ease of solving.
- **Simplex Algorithm:** An iterative method for finding the optimal solution by moving along the edges of the feasible region.
- **Duality:** Every LP problem has a corresponding dual problem; the solutions are interconnected.
- **Weak and Strong Duality Theorems:** Establish relationships between the primal and dual solutions.
