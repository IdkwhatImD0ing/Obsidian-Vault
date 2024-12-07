**NP-Completeness Cheat Sheet**
- **To Show Problem P is in NP:**
    - Certificate: Proposed solution.
    - Verifier: Checks correctness in polynomial time.
- **To Show Problem P is NP-hard:**
    - Start with a known NP-complete problem Q.
    - Polynomial-time reduction Q → P.
        - **Forward (If) Direction:** If Q has a solution, then P’s constructed instance also has a solution.
        - **Backward (Only-If) Direction:** If P’s constructed instance has a solution, Q must have had a solution.
- **Conclusion:**
    - P ∈ NP and P is NP-hard ⇒ P is NP-complete.
**Maximum Flow Modeling Cheat Sheet**
- Represent constraints as capacities on edges.
- Find max flow using, e.g., Ford-Fulkerson or Edmond-Karp.
- Max-flow = feasible solution to original problem.
    - **Forward Direction:** Given a known solution, construct a flow respecting capacities.
    - **Backward Direction:** Given a max flow, interpret it as a valid solution.

**Cheat Code / Checklist for Linear Programming Problems**
**General LP Problem Formulation Steps:**
1. **Identify Decision Variables:**
    - Assign variables that represent the quantities you want to determine.
2. **Objective Function:**
    - Write a linear function of these variables to maximize or minimize.
3. **Constraints:**
    - Translate all resource limits, requirements, or restrictions into linear inequalities or equalities.
4. **Non-negativity / Integrality:**
    - Add x ≥ 0 (and x ∈ {0,1} or integers if needed).

Remember: Keep everything linear—no products of variables, no powers.
**For Dual Problems:**

- Primal (max): **Ax ≤ b, x ≥ 0**
    - Dual (min): **A^T y ≥ c, y ≥ 0**
- Reverse inequalities and free variables as needed for ≥, ≤, = constraints.

**Example Patterns:**

- **Minimize cost**: Objective = cost * variables.
- **Resource shortfall**: Turn requirements into inequalities (≥ or ≤).
- **Binary decisions (clique, set cover)**: x_i ∈ {0,1}, add pairwise constraints to enforce feasibility (e.g., xi + xj ≤ 1 if can’t choose both).

This high-level process applies to all LP/ILP problems: define variables clearly, set your linear objective, list out linear constraints from the problem conditions, and specify variable domains (nonnegative, binary, etc.).