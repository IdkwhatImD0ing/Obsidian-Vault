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