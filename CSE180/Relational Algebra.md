## Basic Queries
 - Selection ( σ )
 - Projection ( π )
 - Set-theoretic operations:
	 - Union ( ⋃ )
	 - Set-difference ( - )
	 - Cross-product ( x )
	 - Intersection ( ⋂ )
 - Renaming ( ρ ) and Assignment (¬) 
 - Natural Join (|><|), Theta-Join (|><|theta )
 - Division ( / or ÷ ) ⧖

### 
![[Pasted image 20230227123941.png]]

 - Unary operation – Input: Relation with schema R(A1, …, An) 
	 - Output: Relation with attributes A1, …, An 
	 - Meaning: Takes a relation R and extracts only the rows from R that satisfy the condition
	 - Condition is a logical combination (using AND, OR, NOT) of expressions of the form:
	 - \<expr> \<op> \<expr> where is an attribute name, a constant, a string, and op is one of (=, ≤, ≥, <, >, <>)
		 - E.g., “age > 20 OR height < 6”, 
		 - “name LIKE ‘Anne%’ AND salary > 200000”
		 - “NOT (age > 20 AND salary < 100000)”

### Projection
![[Pasted image 20230227123929.png]]

 - Unary operation
	 - Input : Relation with schema R(A1, … , An)
	 - Output: Relation with attributes in attribute list, which must be attributes of R
	 - Meaning: For every tuple in relation R, output only the attributes appearing in attribute list 
 - May be duplicates; for Codd’s Relational Algebra, duplicates are always eliminated (set-oriented semantics) 
	 - Reminder: For relational database, duplicates matter.
	 - Why?

### Set Union R U S

- Binary operator 
	- Input: Two relations R and S which must be union-compatible 
		- They have the same arity, i.e., the same number of columns.
		- For every column i, the i’th column of R has the same type as the i’th column of S.
		- Note that field names are not used in defining union-compatibility.
			- We can think of relations R and S as being union-compatible if they are sets of records having the same record type. 
	- Output: Relation that has the same type as R (or same type as S).
	- Meaning: The output consists of the set of all tuples in either R or S (or both)

### Set Difference R-S

 - Binary operator.
	 - Input: Two relations R and S which must be union-compatible
	 - Output: Relation with the same type as R (or same type as S)
	 - Meaning: Output consists of all tuples in R but not in S

### Product RxS

 - Binary operator 
	 - Input: Two relations R and S, where R has relation schema R(A1, …, Am) and S has relation schema S(B1, …, Bn). – Output: Relation of arity m+n – Meaning: R x S = { (a1, …, am, b1, …, bn) | (a1, …, am) ∈ R and (b1, …, bn) ∈ S) }. • Read “|” as “such that” • Read “∈” as “belongs to”

