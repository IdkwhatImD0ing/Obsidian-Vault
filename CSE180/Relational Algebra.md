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
 - There are two “Housekeeping” operations that make Relational Algebra queries easier to write.
	 - Assignment: ¬
	 - Rename: r

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
	 - Input: Two relations R and S, where R has relation schema R(A1, …, Am) and S has relation schema S(B1, …, Bn).
	 - Output: Relation of arity m+n
	 - Meaning: 
		 - R x S = { (a1, …, am, b1, …, bn) | (a1, …, am) ∈ R and (b1, …, bn) ∈ S) }.
		 - Read “|” as “such that” 
		 - Read “∈” as “belongs to”

### Theta Join
![[Pasted image 20230227124112.png]]

 - Binary operator
	 - Input: R(A1, …, Am), S(B1, …, Bn)
	 - Output: Relation consisting of all attributes A1, …, Am and all attributes B1, …, Bn. Identical attributes in R and S are disambiguated with the relation names.
	 - Meaning of R ⋈ S: The θ-Join outputs those tuples from R x S that satisfy the condition θ.
		 - Compute R x S, then keep only those tuples in R x S that satisfy θ.
		 - Equivalent to writing sθ(R x S) 
 - If θ always evaluates to TRUE, then R S = sθ(R x S) = R x S.

### Natural Join 

![[Pasted image 20230227124212.png]]

 - Often a query over two relations can be formulated using Natural Join. 
 - Binary operator: 
	 - Input: Two relations R and S where { A1, …, Ak } is the set of common attributes (column names) between R and S.
	 - Output: A relation where its attributes are attr(R) U attr(S). In other words, the attributes consists of the attributes in R x S without repeats of the common attributes { A1, …, Ak } 
 - Meaning: 
	 - ![[Pasted image 20230227124317.png]]
 1. Compute R x S 
 2. Keep only those tuples in R x S satisfying: R.A1=S.A1 AND R.A2 = S.A2 AND … AND R.Ak=S.Ak 
 3. Output is projection on the set of attributes in R U S (without repeats of the attributes that appear in both

### Semi Join

 - Meaning: 
 - ![[Pasted image 20230227125451.png]]
 1. Compute Natural Join of R and S
 2. Output the projection of that on just the attributes of R
 - Find all courses that have some enrollment: Course ⧔ Enrollment
 - Find all faculty who are advising at least one student: Faculty ⧔ Student
 - How does Semi-Join relate to EXISTS in SQL

### Set Intersection

 - How would you write Dell_desktops ∩ HP_desktops in SQL? 
	 - SELECT * FROM Dell_desktops INTERSECT SELECT * FROM HP_desktops;
 - Intersection is a Derived Operator in Relational Algebra: 
	 - R ∩ S = R – (R – S) = S – (S – R)

### Division

 - Input: Two relations R and S, where both: 
	 - attr(S) ⊂ attr(R) and
	 - attr(S) is non-empty 
 - Output: Relation whose attributes are in attr(R) – attr(S).
 - Example: R(A,B,C,D), S(B,D).
	 - Meaning: R ÷ S = { (a, c) | for all (b,d) ∈S, we have (a,b,c,d) ∈R }
 - Example: Find the names of drinkers who like all beers 
	 - Likes(drinker, beer) ÷ πbeer ( BeersInfo(beer, maker) )
 - The Quotient (or Division) R ÷ S is the relation consisting of all tuples (a1,…,ar-s) such that: 
	 - For every tuple (b1,…,bs) in S, the tuple (a1,…,ar-s, b1,…,bs) is in R

## Independence

The five basic operators are independent of each other. In other words, for each relational operator o, there is no relational algebra expression that is built from the rest that defines o