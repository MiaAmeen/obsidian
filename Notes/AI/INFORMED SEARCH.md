[[lecture05.pdf]]
###### Search Heuristics
- h(n): estimated cost of the cheapest path from the state at node n to a goal state
- h(n) example: euclidian distance
###### Greedy Best-First Search
- expands the node with lowest h(n)
###### A* Search
- uniform cost search g(n) expands a node with least cost from start node to current node
- greedy best first search h(n) expands a node with least estimated cost from current node to goal node
- A* search expands a node with least sum of costs:
	- f(n) = g(n) + h(n)
- complete
- uses lots of memory... ![[Screenshot 2025-02-24 at 11.03.01 AM.png]]
###### Admissibility property
- heuristic h is admissible if 0 <= h(n) <= h*(n) where h*(n) is the optimal cost
	- i.e., it will never overestimate the cost (optimistic).
- 'dominant' heuristic is closer to h*(n)
![[Screenshot 2025-02-24 at 9.09.38 AM.png]]
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
###### Graph Search
- we do not want to expand a state twice.
- Before expanding a node check if it is in the "reached/closed" set. 
	- If reached: dont expand
	- If not reached: add to reached, then expand
###### Consistency Property
![[Screenshot 2025-02-23 at 5.36.10 PM.png]]
- Every consistent heuristic is admissible, but not vice versa.
###### A* Optimality
- Tree search
	- optimal if heuristic is admissible
- Graph search
	- optimal if heuristic is admissible
	- if heuristic is consistent, we'll never have to check/update reached state
###### Beam Search (memory efficient version of A*)
- Limits the size of the frontier size. Keeps only the k nodes with best f scores OR
- Keep only the nodes with the f(best) <= f(node) <= f(best) + s
###### Iterative-deepening A* search
- Initially, the f -limit is equal to f -value(start)
	- Repeat until a goal is found
	- Expand nodes using A∗ while f-value(node) ≤ f-limit
	- Increase f-limit to the smallest f-value of unexpanded node
###### Recursive Best First Search
- Linear space heuristic search algorithm
- Uses a dynamic f-limit to keep track of the f-value of the best alternative path from any ancestor
- If the current node exceeds f-limit, the recursion unwinds to the best alternative and replaces the f-value of each node along the path with a backed up value
###### Simplified memory-bounded A*
???