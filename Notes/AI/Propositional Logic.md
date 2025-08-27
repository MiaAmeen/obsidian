[[lecture11.pdf]] [[lecture12.pdf]]

- **Knowledge-base** is a set of sentences in a formal language (like logic)
	- **Syntax**: defines the "grammar" or sentences in the language, and **Semantics**: defines the meaning of the sentence
- **Entailment**: One thing follows from another...  $KB |= \alpha$ 
	- KB entails $\alpha$ iff $\alpha$ is true in ALL WORLDS where KB is true.
- **Models**
	- "formally structured world with respect to which truth can be evaluated"
		- basically the entire state space
	- $m$ is a model of a sentence $\alpha$ if $\alpha$ is true in $m$
	- eg: if a is x+2=y, m of a is a world where x=5, y=7
	- $M(\alpha)$ is a set of all models of $\alpha$
	- $KB |= \alpha \quad \text{iff} \quad M(KB) \subseteq M(\alpha)$
![[Screenshot 2025-03-31 at 11.10.28 AM.png]]

**Inference Procedures**
- $KB \vdash_i \alpha. \alpha$ derived from KB by procedure i
- **Soundness**: Procedure i is sound if it derives only entailed sentences
	- When $KB \vdash_i \alpha$ it is also true that $KB |= \alpha$
- **Completeness**: Procedure i is complete if it can derive any sentence that is entailed 
	- When $KB |= \alpha$ it is also true that $KB \vdash_i \alpha$ 

## Propositional Logic
- Syntax: variables (proposition), Negation (not), Conjunction (and), disjunction (or), implication (a implies b), biconditional (b also implies a) 
- Semantics: the model specifies true or false for each proposition, so $2^n$ possible models for $n$ propositions
- **Truth table**: or inference by enumeration. brute force search basically ![[Screenshot 2025-03-31 at 11.20.55 AM.png]]
Proof methods are of two types:
- model checking (truth table enumeration; always exponential, backtracking, heuristic search model space)
- application of inference rules (sound)
##### Logical Equivalence
![[Screenshot 2025-03-31 at 11.28.17 AM.png]]
- Modus Ponens
	- $\frac{\alpha \implies \beta, \quad \alpha}{\beta}$
- And-elimination
	- $\frac{\alpha \land \beta}{\alpha}$
- Resolution Inference
	- takes two clauses with at least one pair of complementary literals and produces a new clause containing all literals of the two original clauses except the two complementary literals
	- $\frac{a \lor b, \quad \lnot b}{a}$
##### Validity and Satisfiability
- a sentence is **valid** if it is true in all models eg: "True" is always true lol. 
	- $KB |= \alpha \quad iff \quad (KB \implies \alpha) \quad is valid$
- a sentence is **satisfiable** if it is true in some models
- **unsatisfiable** if it is true in no models eg: a and !a
##### Conjunctive Normal Form
- series of ors joined by ands
	- (a or b) and (c or !d)
- ANYTHING can be transformed into CNF
##### Proof by Resolution
- ***To show KB |= a, we should that KB and !a is unsatisfiable***.
- TODO HERE On
##### Forward and Backward Chaining
- Horn clause is disjunction of literals of which at MOST one is positive.
- (!a or !b or c) means that (a and b => c)
insert image
insrt code (and-or tree)
- backward chaining: start with what u wanna prove then check its dependents