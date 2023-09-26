## Search Problem

 - Initial State
	 - Empty assignment
 - Successor Function
	 - Value assigned to unassigned function
 - Goal Test
	 - Assignment is complete and consistent

## Types of CSPs:

### Discrete Variables
 - Finite Domains
	 - n variables
	 - Boolean CSPs, incluiding Boolean Satisfiability
 - Infinite Domains
	 - integers, stri

## Constraints

Used to express the relationships between variables and restrict the possible values that these variables can take.

### Unary constraints:
Unary constraints involve a single variable and restrict the values that this variable can take from its domain. Unary constraints can be represented as a function or a condition that a single variable must satisfy. For example, in a CSP for assigning colors to countries on a map, a unary constraint could be that a specific country must be colored red.

### Binary constraints:
Binary constraints involve two variables and restrict the possible value combinations that these two variables can take simultaneously. Binary constraints can be represented as a function or a condition that a pair of variables must satisfy. For example, in a map-coloring CSP, a binary constraint could be that two neighboring countries must have different colors.

### N-ary constraints:
N-ary constraints involve more than two variables (n variables, where n > 2) and restrict the possible value combinations that these variables can take simultaneously. N-ary constraints can be represented as a function or a condition that a group of variables must satisfy. For example, in a scheduling CSP, an n-ary constraint could be that a certain number of tasks must be completed within a specific time frame, and no two tasks can be executed at the same time.

## Arc Consistency

Arc consistency is a property of constraint satisfaction problems (CSPs) where, for every pair of variables connected by a constraint, each value in the domain of the first variable has at least one compatible value in the domain of the second variable, and vice versa. This means that when a variable is assigned a value, there is at least one possible value for each neighboring variable that satisfies the constraint between them.

Basically: Imagine you have a bag of differently shaped puzzle pieces. Each puzzle piece can only connect with certain other pieces, based on their shapes. Arc consistency is like making sure that for every puzzle piece, there is at least one other piece it can connect to without breaking the puzzle's rules. This way, you don't get stuck with a piece that can't connect to any other pieces when trying to solve the puzzle.