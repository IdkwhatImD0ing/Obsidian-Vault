## Search Problem in CSPs

- **Initial State**: Empty assignment
- **Successor Function**: Assign a value to an unassigned variable
- **Goal Test**: Assignment is complete and satisfies all constraints
- **Variable**: Items that can be assigned values
- **Domains**: The set of values that can be assigned to variables
- **Constraints**: Rules that limit the domain values for variables

## Types of CSPs

### Discrete Variables
- **Finite Domains**: Boolean CSPs, map coloring
- **Infinite Domains**: Job scheduling; requires a constraint language
  
### Continuous Variables
- Relevant in time-series data analysis
- Polynomial-time solvable with linear constraints

## Constraints

### Unary Constraints
- Restricts values of a single variable. 
- **Example**: A country must be colored red.

### Binary Constraints
- Restricts combinations of values between two variables. 
- **Example**: Neighboring countries must have different colors.

### N-ary Constraints (Higher Order)
- Restricts combinations of values between three or more variables. 
- **Example**: Multiple tasks must be completed within a specific time frame.

## Solving CSPs

### Backtracking
- **Example**: Sudoku; assign numbers one at a time and backtrack if needed.

### Most Constrained Variable (MCV)
- Select the variable with the fewest legal moves.
- **Example**: Choose the country with the most neighbors to color first.

### Least Constraining Value
- Pick the value that imposes the fewest constraints on other variables.
- **Example**: Choose a meeting time that leaves the most free slots for other meetings.

### Forward Checking
- Eliminate future domain values that conflict with current assignments.
- **Example**: In Eight Queens Puzzle, place a queen and remove invalid cells for future queens.

### Arc Consistency
- Each value in the domain of one variable has a compatible value in the domain of another variable.
- **Example**: In SEND + MORE = MONEY, assigning 'S' to 9 removes 9 from the domain of other letters.

### Iterative Min-conflicts
- Start with an initial assignment and iteratively correct variables causing conflicts.
- **Example**: Timetable Scheduling; move conflicting classes to minimize conflicts.

---

CSPs are search problems where states are defined by the values of variables, and the goal is determined by constraints. Variable ordering and value selection heuristics can optimize the search process. Techniques like forward checking and arc consistency can prevent assignments that will lead to failure and can help in detecting inconsistencies more efficiently.