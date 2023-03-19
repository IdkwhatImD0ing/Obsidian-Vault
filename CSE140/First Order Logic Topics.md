1.  **Syntax:** FOL is built on a set of symbols and rules that define its structure. Terms are the basic elements like variables, constants, and functions. Well-formed formulas (WFF) are combinations of terms and predicates that create meaningful statements. Quantifiers, like "for all" (∀) and "there exists" (∃), are used to express relationships between elements in a more general way.
    
2.  **New Inference rules for quantifiers:** FOL has additional inference rules to handle quantifiers. These rules include universal instantiation (UI), universal generalization (UG), existential instantiation (EI), and existential generalization (EG). They allow you to manipulate and reason with quantified statements.
    
3.  **Unification:** Unification is a process of finding a substitution that makes two expressions equal. In FOL, unification is used to match different parts of expressions, helping derive new conclusions during the inference process.
    
4.  **Horn clauses - Forward Chaining (FC) and Backward Chaining (BC):** Horn clauses are a specific type of FOL statement that are easy to work with in inference. FC is a reasoning method that starts with known facts and applies rules to derive new conclusions. BC is a reasoning method that starts with a goal and works backward to find facts that support it.
    
5.  **Resolution Refutation:** Resolution is a powerful inference method used in FOL to prove statements or find contradictions. It works by combining pairs of statements with opposite parts (e.g., P and ~P) and deriving new statements until a contradiction is found or no more conclusions can be drawn.
    
6.  **Converting to clausal form:** Before using resolution, FOL sentences need to be converted into clausal form. This involves simplifying the expressions and standardizing variables, among other steps. Once in clausal form, the resolution process can be applied more easily.