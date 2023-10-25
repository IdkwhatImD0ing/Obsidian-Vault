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
		2. Unit REsolution Rule
	6. P ∧ Q) ⇒ R is a Horn clause.



