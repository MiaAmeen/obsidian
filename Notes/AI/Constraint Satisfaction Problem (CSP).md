[[lecture09.pdf]]  [[lecture10.pdf]]
What about multiplayer instead of two-player games?
- states now have utility tuples; each player maximizes their own utiliity. No longer zero-sum. We need generalized minimax...
- "Factored representation of state"
- Three components of CSP:
	- X: set of variables
	- D: set of domains (technically, unary constraints)
	- C: set of constraints
- Solution is an assignment of value to each variable that satisfies all constraints [[Artificial-Intelligence-A-Modern-Approach-4th.pdf#page=194&selection=413,69,414,89|Artificial-Intelligence-A-Modern-Approach-4th, page 194]]
Example 1: Map Coloring Problem ![[Screenshot 2025-02-05 at 7.03.05 PM.png]]
C: States sharing a border cannot have the same color.

Example 2: N-Queens Problem![[Screenshot 2025-02-24 at 1.34.48 PM.png]]
##### Constraint graph
![[Screenshot 2025-02-05 at 7.04.45 PM.png]]
###### Variables
- Discrete variables(Finite domain D = {1, 2, 3} vs infinite domains D = {1... inf}) vs Continuous Variables
###### Constraints
- Hard constraints
	- Unary constraints involve a single variable, binary; two or more, higher-order; 3 or more. 
	- *Alldif - means all vars have different values*
- Preference constraints (eg, green better than red)
	- Can be encoded as costs, CSPs with preferences are constrained optimization problems which can be solved with linear programming methods
###### Cryptarithmetic
![[Screenshot 2025-02-05 at 7.17.17 PM.png]]
##### Node Consistency
-  single variable (corresponding to a node in the CSP graph) is node-consistent if all the values in the variable’s domain satisfy the variable’s unary constraints. A graph is node consistent if every variable in the graph is node consistent.
##### Arc Consistency
- arc: binary constraint
- Variable is arc consistent if every value in its domain satisfies the variable’s binary constraints
- *More formally, Xi is arc-consistent with respect to another variable Xj if for every value in the current domain Di there is some value in the domain Dj that satisfies the binary constraint on the arc (Xi, Xj).*
AC3:
![[Screenshot 2025-02-05 at 7.22.55 PM.png]]
repeatedly revise binary constraints, update the domain, and then update affected constraints.

How do we use arc3 for n-ary constraints ?
![[Screenshot 2025-02-05 at 7.45.31 PM.png]]
I dont get it.
##### Path Consistency
- tightens binary constraints by using implicit constraints that are inferred by looking at triples of variables.
- *A two-variable set {Xi, Xj} is path-consistent with respect to a third variable Xm if, for every assignment {Xi = a, Xj = b} consistent with the constraints (if any) on {Xi, Xj}, there is an assignment to Xm that satisfies the constraints on {Xi, Xm} and {Xm, Xj}.* 
##### K-Consistency
- A CSP is k-consistent if, for any set of k−1 variables and for any consistent assignment to those variables, a consistent value can always be assigned to any kth variable.
- For binary constraint graphs: node consistency = 1-consistency; arc consistency = 2-consistency; path consistency = 3-consistency.
#### Standard Search Formulation
States are defined by the values assigned so far 
- Initial state: no variables are assigned, 
- {} Successor function: assign a value to an unassigned variable 
- Goal state: assignment is complete and satisfies all constraints 
- Solution appears at depth n where n is number of variables
##### Backtracking Search
- Assign one variable at each step
- Variable assignments are commutative
	E.g. WA = red then NT = green is same as NT = green then WA = red 
- Check constraints at each step, Consider values that do not conflict previous assignments
- think of a tree where one specific variable is assigned possibles values from its domain at each level...
- Depth first search with above improvements is called as backtracking search for CSP 
![[Screenshot 2025-02-05 at 7.53.19 PM.png]]
![[Screenshot 2025-02-24 at 6.23.47 PM.png]]
##### Search Heuristics
- what order should we pick variables assign; what values should we pick?
- can we exploit problem structure/detect failure early?
- Following are strategies that approximate "closer" solutions but may not guarantee (in order)
1. Minimum Remaining Values (MRV)
	- choose a variable with fewest legal values
	- doesnt help at all with colorful map problem because every variable has same number of possible values
2. Degree Heuristic
	- choose a variable with most constraints on remaining variables
	- eg: SA has the highest degree, 5, in the map
3. Forward Checking
	1. Keep track of domain, terminate search when any variables have no legal values remaining
	2. does not provide early detection for all failures
	3. think of this as "pruning" the DFS tree when doing backtracking.
4. Constraint Propagation
	1. repeatedly enforces constraints locally




