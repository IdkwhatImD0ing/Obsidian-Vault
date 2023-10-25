## True / False

 - Hill climbing is a complete search algorithm for global solutions and it never looks ahead beyond the immediate neighbors of the current state.
	 - False
	 - It is not a complete search algorithm for finding global solutions. Its a local search algorithm that moves to a local neighbor
	 - Can get stuck in local minima or local maxima
 - “The sentence A entails the sentence B” if and only if, in every model in which B is true, A is also true.
	 - False
	 - Entailment is opposite way around, if A is true, then B is true
 - An inference algorithm f is complete means that if A can inference B using f, then A entails B
	 - True
	 - Completeness theory says if A inference f to B, then A := B
 - An inference algorithm f is sound means that if A entails B, then A can inference B using f.
	 - False
	 - Soundness theory states that f is sound if and only if, whenever f can infer B from A, then it must mean A := B
 - A sentence is valid if it is true in all models.
	 - True
	 - Valid means it must hold under all circumstances
	 - Eg P and Not P
 - “From Hates(Alice, Exam) we can infer ∃x Hates(x, Exam)” applies the Existential Elimination (EE) rule in First-order Logic.
	 - False
	 - This is actually Existential Introduction, as it introduces a new existential term
 - Logical agents apply entailment to a knowledge base to derive new information and make decisions.
	 - True
	 - Logical agents use reasoning to make decisions, they do that by using inference and reasoning can be entailed. Expanding their kb with facts that are logically entailed but not stated.
 - Every propositional formula can be converted into an equivalent formula that is in Conjunctive Normal Form.
	 - True
	 - CNF is a way of writing propositional formulas in And and Ors
 - After applying Skolemization to a sentence, the resulting formula is satisfiable if and only if the original sentence is satisfiable
	 - True
	 - Skolemization is a technique to remove existential quantifiers
	 - It preserves satisfiability
	 - Not logically equivalent though
 - Horn clause is a disjunction of literals of which at least one is positive.
	 - False
	 - Horn Clause contains at most one positive

## Propositional Logic

1. Translate the following English sentences to Propositional Logic. Let:
	1. E=Liron is eating
	2. H=Liron is hungry
	3. Choose from the following options
		1. E ⇒ ¬H
		2. ¬(H ⇒ ¬E)
		3. E ∧ ¬H
		4. E ⇔ H
	4. If Liron is eating, then Liron is not hungry.
		1. 1
	5. Liron is eating and not hungry.
		1. 3
	6. Liron is hungry and eating.
		1. 2
	7. Liron is eating if and only if Liron is hungry.
		1. 4
2. Are the following statements true or false? Type T for true and F for false.
	1. TRUE ⊨ FALSE
		1. False
		2. True can never entail False
		3. And False can never entail True
	2. (P ∧ Q) ⊨ (P ⇔ Q)
		1. True
		2. Only way for P and Q to be true is both is true, thus then P iif Q is also true
	3. (P ⇔ Q) ∧ (¬P ⋁ Q) is satisfiable.
		1. True
		2. if both P and Q is true, then its true
		3. if both p and q is false, then its true
	4. ((P ⋁ Q) ⇔ P) ⋁ (¬P ∧ Q) is a tautology.
		1. False
		2. If P and Q both false then results to false
		3. Tautology is formula that is universally true
	5. “P⇒Q” and “P”, we can infer “Q” by applying the Unit Resolution Rule.
		1. True
		2. Unit Resolution Rule
			1. If we have A and not A or B, then we can infer B
		3. We have, P, and P implies B, therefore Q is true
	6. (P ∧ Q) ⇒ R is a Horn clause.
		1. True
		2. At most one positive literal
		3. Need to rewrite the implies

## First Order Logic

### Problem 1

 - The first–order language of (directed) graphs is L = {r}, where r is a binary relation symbol.
 - The only terms are the variables ‘x’, ‘y’, ‘z’ etc.
 - Atomic formulas look like (rxy).Universal and Existential quantifiers work the same way as they normally do.
Sometimes, smart people have a hard time understanding the above points, and since, you all are smart people, we want to explain the above points in simple terms:
 - For nodes/vertices/terms x and y in a (directed) graph G, rxy denotes that there is
an edge going from node x to node y in G.

1. The graph has at least two vertices. 
	1. ExEy(x != y)
2. Every vertex has an edge attached to it. 
	1. AxEy(rxy OR ryx()
3. Every vertex has at most two edges directed from it to other vertices. 
	1. AxAyAzAw((rxy AND rxz AND rxw)) => (y = z or y = W or z = w)
4. Every vertex has at least two edges directed from other vertices to it. 
	1. AxEyEz(y != z AND ryx AND rzx) (**Important, r arguments is flipped!!!**)
5. Write T for True, F for False: 
	1. “Every vertex has exactly one edge entering it” can be written as:
		1. ∀x∃y rxy ∧ ∀w∀v∀u (( rvw ∧ ruw ) ⇒ (v = u))
		2. False

### Problem 2
Consider a domain with the following relation.
 - ISPRIME(n) : n is a prime number
 - HasSS#(x,n) : x has the social security number n
 - Person(x): x is a person

 - Write T for True, F for False: 
	 - “Every even natural number n has 2 as it’s factor” can be written as: 
		 - ∀n. ( (n > 2 ∧ ∃k. n = 2k)
	 - False, expresses even, but doesnt state two is a factor
 - Goldbach’s Conjecture says that “Every even natural number n > 2 can be expressed as the sum of two primes."
	 - Write Goldbach’s Conjecture in First Order Logic. 
	 - ∀n(n>2∧∃k(n=2k)⇒∃p∃q(ISPRIME(p)∧ISPRIME(q)∧n=p+q))
 - Write T for True, F for False: 
	 - “No two people have the same social security number.” can be written as:
		 - ¬∃x,y,n Person(x) ∧ Person(y) ∧ HasSS#(x,n)∧ HasSS#(y,n) .
	 - True

## Inference

### Problem 1

1. We designed an exam, which has three parts (P1, P2 and P3) for two types of
examinees (E and non-E). For each part, there are three ranks (A, B and C). The result for the
entire exam is either pass or not pass.
Given the following sentences:
1. Any E examinee who gets an A in both part P1 and P2 will pass the exam.
2. Any non-E examinee who gets a C in part P3 or P2 won’t pass the exam.
3. Some non-E examinees who get a C or B in part P2 and pass the exam.
4. Alex is an E examinee getting an A in part P1 and Steve is a non-E examinee getting an A in part P3.
Translate the above sentences into First Order Logic using the following predicates: E(x) which means x is an E examinee R(x, y, z) which means examinee x gets a y in part z, and P(x) which means x passes the exam

1. **Any E examinee who gets an A in both part P1 and P2 will pass the exam.**
   - $\( \forall x \, ((E(x) \land R(x, \text{'A'}, \text{'P1'}) \land R(x, \text{'A'}, \text{'P2'})) \Rightarrow P(x)) \)$

2. **Any non-E examinee who gets a C in part P3 or P2 won't pass the exam.**
   - $\( \forall x \, ((\lnot E(x) \land (R(x, \text{'C'}, \text{'P3'}) \lor R(x, \text{'C'}, \text{'P2'}))) \Rightarrow \lnot P(x)) \)$

3. **Some non-E examinees who get a C or B in part P2 and pass the exam.**
   - $\( \exists x \, ((\lnot E(x) \land (R(x, \text{'C'}, \text{'P2'}) \lor R(x, \text{'B'}, \text{'P2'}))) \land P(x)) \)$

4. **Alex is an E examinee getting an A in part P1 and Steve is a non-E examinee getting an A in part P3.**
   - $\( E(\text{'Alex'}) \land R(\text{'Alex'}, \text{'A'}, \text{'P1'}) \land \lnot E(\text{'Steve'}) \land R(\text{'Steve'}, \text{'A'}, \text{'P3'}) \)$



