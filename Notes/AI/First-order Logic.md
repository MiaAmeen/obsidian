[[lecture13.pdf]] [[lecture14.pdf]]

Assumes that world contains the following:
- **objects**: anything
- **relations**: unary, binary, etc
- **functions**: relations with one value for a given input
FOL models are infinite! Can contain infinite number of objs, rels, funcs.
$\rightarrow$ ***Not possible to do inference by enumeration.***

#### Quantification: Universal $\forall$ and Existential $\exists$
###### Common Mistake with Quantification:
![[Screenshot 2025-02-27 at 8.58.28 AM.png]]
![[Screenshot 2025-02-27 at 9.06.41 AM.png]]
![[Screenshot 2025-02-27 at 9.10.05 AM.png]]

REMEMBER the definition of implication:
- x => y
	- if x is true, y is true
	- if x is false, y could be anything!
##### Universal Instantiation
![[Screenshot 2025-02-27 at 9.29.10 AM.png]]
##### Existential Instantiation
![[Screenshot 2025-02-27 at 9.30.40 AM.png]]
##### Reduction to Propositional Inference
![[Screenshot 2025-02-27 at 9.38.21 AM.png]]lord

TODO FROM HERE ON bruh :(
###### Unification
Find a substitution that makes different sentences look identical...
UNIFY(a, b) = theta where a/theta = b/theta
- a: Knows(John, x) b: Knows(John, Jane)
	- theta: {x/Jane}
...wtf ?
##### Conversion to CNF
![[Screenshot 2025-03-31 at 12.27.09 PM.png]]

#### Forward Chaining in FOL
facts --> goal
![[Screenshot 2025-03-04 at 9.27.01 AM.png]]

Example:
*The law says that it is a crime for an American to sell weapons to hostile nations. The country Nono, an enemy of America, has some missiles, and all of its missiles were sold to it by Colonel West, who is American. We would like to prove: Colonel West is a criminal.*
![[Screenshot 2025-03-04 at 9.34.29 AM.png]]
##### Properties
- sound and complete for first order definite clauses
- may not terminate in general if a is not entailed
	- Unavoidable: entailment with definite clauses is semidecidable

#### Backward Chaining
goal --> facts (opposite of forward chaining duh)
- depth first recursive proof search
- incomplete due to infinite loops
- inefficient due to repeated subgoals