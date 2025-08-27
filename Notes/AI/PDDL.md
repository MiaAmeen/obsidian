[[lecture15.pdf]]

**Classical Planning**: assumes discrete, deterministic, static, and fully observable environment
vs
**Planning domain definition language** (**PDDL**) is a language for representing a planning problem: Initial state, Actions with preconditions and effects, Goal test
###### PDDL State
Conjunction of ground and functionless fluents?
- Ground means having no variables
- Fluent means an aspect of world that changes over time
Follows database semantics:
- Unique-names assumption, Closed world assumption, Domain closure assumption

Action Schema (when variables are substituted for constants, this becomes ground action)
![[Screenshot 2025-03-06 at 8.43.33 AM.png]]
- Action name: Fly
- List of variables: p, from, to
- Precond: Preconditions of the action (conjunction of positive or negative fluents)
- Effect: Effects of the action which can be divided into add and delete lists
Applicable
- A ground action is applicable in a state if that state entails the action’s precondition
	- (a ∈ Actions(s)) ⇔ s |= precond(a)
	- Every positive literal in the precondition is in the state
	- Every negative literal in the precondition is not in the state
	- example: ![[Screenshot 2025-03-06 at 8.48.52 AM.png]]
	- this state s is applicable
Action Effect:
	- s′ = result(s, a) = (s − del(a)) ∪ add(a)
	- eg: s′ = Plane(P1) ∧ Airport(SFO) $\land$ Airport(JFK ) ∧ Plane(P2) ∧ At(P2, JFK ) ∧ At(P1, JFK )
###### Example Problem
- Planning domain is a set of action schemas 
- Planning problem contains a domain with an initial state and a goal 
- Initial state is a conjunction of ground fluents with closed world assumption
![[Screenshot 2025-03-06 at 9.03.20 AM.png]]

##### Algorithms for Planning
- state space search?... state space may be too big for many problems
- forward state space (progression planners)
	- start at initial state and apply all APPLICABLE actions until goal is reached.
- backward state space search (regression planners; opposite)
	- consider only relevant actions - unifies with any of the goal literals and does NOT negate any of them.




  
