First-Order Logic (FOL) is needed because Propositional Logic, while useful in some situations, has limitations that make it difficult to represent more complex information and relationships.

 1. **Individuals**: Propositional Logic cannot easily identify specific individuals, like a person (Mary) or a number (3). In FOL, we can use constants to represent individuals, making it easier to talk about specific entities.
	 1. Instead of just saying "someone" or "something," you can talk about a specific person, like Mary, or a specific number, like 3.
 2. **Properties and Relations**: Propositional Logic cannot directly express properties of individuals or relationships between individuals, like "Bill is tall." FOL allows us to use predicates to represent properties and relationships, such as `tall(Bill).
	 1. You can say things like "Bill is tall" or "Alice is friends with Bob" to show how different things are related or what their characteristics are.
 3. **Generalizations and Patterns**: Propositional Logic struggles to represent generalizations, patterns, or regularities. For example, expressing that all triangles have three sides is difficult in Propositional Logic. FOL introduces quantifiers, which allow us to represent such general statements. For instance, we can say "For all x, if x is a triangle, then x has three sides."
	 1. You can make statements that apply to lots of things at once, like "all triangles have three sides" or "every dog is an animal."

FOL is more expressive than Propositional Logic because it adds relations, variables, and quantifiers that allow us to represent complex situations concisely. For example:

-   "Every elephant is gray": ∀ x (elephant(x) → gray(x))
-   "There is a white alligator": ∃ x (alligator(x) ∧ white(x))
## Basic Rules

### Logical Entailment
KB :  a set of sentences
a : arbitrary sentence
KB *entails* a - written as KB |= a - iff every model of KB is a model of a, in other words, a is true in all worlds where kb is true


### [[Knowledge Representation#Inference|Inference (Click for more detailed explanation)]]
Inference is a process in which you draw conclusions based on the information or knowledge you have. It's like solving a puzzle or a mystery based on the clues you've been given.

 - "KB ⊢i α": A sentence (α) can be derived from a knowledge base (KB) using an inference procedure (i).
	 - "Soundness": A procedure (i) is sound if deriving α from KB (KB ⊢i α) guarantees that α is true (KB ⊨ α).
	 - "Completeness": A procedure (i) is complete if any true sentence α (KB ⊨ α) can be derived from KB (KB ⊢i α).

## Syntax

 - Constants
	 - 1, 5, A, B, USC
 - Predicates
	 - \>, Friend, Student
 - Function
	 - +, sqrt, SchoolOf
 - Variable symbols
	 - x, y, foo
 - Connectives
	 - Same as in PL: not (~), and (^), or (v), implies (=>), if and only if (<=>)
 - Quantifiers
	 - Universal ∀x or (Ax - this notation is used in some literature)
	 - Existential ∃x or (Ex)
 - Equality
	 - =

## Quantifiers

 - Universal quantification
	 - (∀x)P(x) means that P holds for all values of x in the domain associated with that variable
	 - E.g., (∀x) dolphin(x) => mammal(x)
 - Existential quantification
	 - (∃ x)P(x) means that P holds for some value of x in the domain associated with that variable
	 - E.g., (∃ x) mammal(x) ^ lays-eggs(x)
 - Permits one to make a statement about some object without naming it

## Scope

 - Switching the order of universal quantifiers does not change the meaning:
	 - (∀x)(∀y)P(x,y) <=> (∀y)(∀x) P(x,y)
 - Similarly, you can switch the order of existential quantifiers:
	 - (∃x)(∃y)P(x,y) <=> (∃y)(∃x) P(x,y)
 - Switching the order of universals and existential does change meaning:
	 - Everyone likes someone: (∀x)(∃y) likes(x,y)
	 - Someone is liked by everyone: (∃y)(∀x) likes(x,y)

## Inference

### [[Knowledge Representation#Forward Chaining|Forwards Chaining]]
Idea: Trigger rules with satisfied premises in the KB, add conclusions to KB until the query is found.

1. Start with facts and rules in the KB.
2. Apply rules with satisfied premises.
3. Add conclusions to KB.
4. Repeat 2-3 until query is found or no rules apply.

### [[Knowledge Representation#Backwards Chaining|Backwards Chaining]]
Idea: Begin with query, work backward to prove it.

1. Start with a target query.
2. Check if query is known in KB.
3. If not, find rule with query as conclusion.
4. Prove rule's premises recursively.
5. Query is proven if all premises are.
6. Track already-attempted goals to avoid loops and repeats.

## De Morgan's Laws

We can relate sentences involving ∀ and ∃ using De Morgan’s laws:
 - ~(∃x) P(x) <=> (∀x) ~P(x)
 - ~(∀x)P(x) <=> (∃x) ~P(x)
 - (∀x) P(x) <=> ~ (∃x) ~P(x)
 - (∃x) P(x) <=> ~(∀x) ~P(x)

## Automated Inference

1.  **Automated inference in FOL is harder than PL**: Inference is the process of figuring out new information based on what we already know. FOL (First-Order Logic) is more powerful and flexible than PL (Propositional Logic), but that also makes it harder to automatically figure out new information using FOL.
    
2.  **Variables can take on many values**: In FOL, variables can represent lots of different things. For example, a variable could be any person, any animal, or any number. This makes it more challenging to figure out new information because there are so many possibilities to consider.
    
3.  **Universal-Elimination rule**: One of the rules we use in FOL is called the Universal-Elimination rule, which helps us figure out what's true for specific things when we know something is true for everything in a group. Because there are so many possible values for variables, there are also lots of ways to apply this rule, making the process more complex.
    
4.  **Godel's Completeness Theorem**: This is a famous result in math and logic that tells us if a sentence is always true (logically valid), there's a way to prove it using a series of steps (a formal proof). In other words, there's always a way to show that something is true if it's actually true.
    
5.  **Resolution refutation**: This is a method for figuring out if a sentence is true based on a set of facts (axioms). If a sentence is true given these facts, resolution refutation is a procedure that can help us determine this. It's one way to deal with the challenges of automated inference in FOL.

# Converting FOL Sentences to Clausal Form
1. Eliminate all <=> connectives
	1. Replace "if and only if" with two separate "if" statements:
	2. (P <=> Q) ==> ((P => Q) ^ (Q => P))
2. Eliminate all => connectives
	1. Replace "if" (P => Q) with "not P or Q" (~P ∨ Q).
	2. (P => Q) ==> (~P v Q)
3. Reduce the scope of each negation symbol to a single predicate
	1. Simplify double negations and push negations inwards, so they only apply to single predicates:
	2. \~~P ==> P
	3. ~(P v Q) ==> ~P ^ ~Q
	4. ~(P ^ Q) ==> ~P v ~Q
	5. ~(∀x)P ==> (∃x)~P
	6. ~(∃x)P ==> (∀x)~P
4. Standardize variables: rename all variables so that each quantifier has its own unique variable name
	1. (∀x) P(x) ∧ (∀x) Q(x) becomes (∀x) P(x) ∧ (∀y) Q(y)
5. Eliminate existential quantification by introducing Skolem constants/functions
	1. (∃x)P(x) ==> P(c)
		1. c is a Skolem constant (a brand-new constant symbol that is not used in any other sentence)
	2. (∀x)(∃y)P(x,y) ==> (∀x)P(x, f(x))
		1. since ∃ is within the scope of a universally quantified variable, use a Skolem function f to construct a new value that depends on the universally quantified variable
		2. f must be a brand-new function name not occurring in any other sentence in the KB.
			1. E.g., (∀x)(∃y)loves(x,y) ==> (∀x)loves(x,f(x))
6. Remove universal quantifiers by (1) moving them all to the left end; (2) making the scope of each the entire sentence; and (3) dropping the “prefix” part
	1. Get rid of "for all" (∀x) symbols by assuming that they apply to the entire sentence.
	2. Ex: (∀x)P(x) ==> P(x)
7. Distribute v over ^
	1. Rearrange statements to distribute "or" (∨) over "and" (∧) symbols.
	2. (P ^ Q) ∨ R ==> (P ∨ R) ^ (Q ∨ R)
		1. (P ∨ Q) ∨ R ==>  (P ∨ Q ∨ R)
8. Split conjuncts into a separate clauses
	1. Separate each part of an "and" (∧) statement into its own clause.
	2. (A ∨ B) ∧ (C ∨ D) becomes two separate clauses: (A ∨ B) and (C ∨ D)
9. Standardize variables so each clause contains only variable names that do not occur in any other clause
	1. Make sure that each clause has unique variable names, not used in other clauses.
	2. If we have two clauses (A(x) ∨ B(x)) and (C(x) ∨ D(x)), we can rename the variables to have (A(x) ∨ B(x)) and (C(y) ∨ D(y))

In this case, f(x) specifies the person that x loves

## Why do we need this?
Resolution is a technique used in First-Order Logic (FOL) to figure out if a set of statements is consistent (can all be true at the same time) or not. It helps us determine if we can reach a contradiction (something that can't be true) using the given statements. Resolution is sound (only derives true conclusions) and refutation complete (will always find a contradiction if one exists).

### Refutation Complete
This means that if a set of statements is unsatisfiable (can't all be true at the same time), the resolution technique will always be able to find a contradiction, proving that the statements are inconsistent.

### Issues with Resolution
1.  **Clausal form:** Resolution only works with statements in a specific format, called clausal form, where each part of the statement is a simple predicate (like P) or its negation (like ~P). We need to convert all FOL sentences into this form before using resolution.
2.  **Choosing sentences to resolve:** The strategy for picking which pairs of sentences to combine during resolution is important. It determines how efficiently we can find a contradiction or prove consistency.
3.  **Choosing literals to unify:** Similarly, choosing which parts of the sentences to match up (unify) also affects the efficiency of the resolution process. This choice is part of the overall search strategy.