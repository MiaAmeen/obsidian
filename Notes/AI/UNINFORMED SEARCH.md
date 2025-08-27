[[lecture04.pdf]]
#### Uninformed Search
- No knowledge of how close a state is to the goal
- Systematically expands nodes from the start
- Path is redundant if it contains a cycle/lower cost path exists
- Tree search doesn’t check for redundant paths. Graph search does
- Frontier: set of unexpanded nodes
- Structure of search tree node: state, parent, action, path cost
#### General Tree Search Algorithm.. [insert image]
![[Screenshot 2025-02-23 at 4.20.18 PM.png]]
#### Search Algorithm Properties
- Completeness
	- Return a solution if one exists or returns failure
	- In a finite state space, an algorithm that systematically explores every state is complete
	- In an infinite state space, an algorithm that can eventually reach every reachable state is complete
- Cost Optimality
	- Returns solution with lowest cost
	- Cost optimality implies completeness !!!
- Time/Space complexity... u alr know
##### BFS search:
- Expands the shallowest node first (FIFO, queue)
- space complexity: O(b^d) where d is depth. eg: 2^n
##### DFS search:
- Expands deepest node first (LIFO, stack)
- space complexity: O(bm) eg: 2*m* where m is max depth.
The two above kind of assume there is no cycle. (Or would fail in that case)
##### Uniform cost search (Dijkstra): pick cheapest action
- Expands node with lowest path cost (priority queue)


BFS properties
- Complete (if b is finite and state space either has solution or is finite); cost-optimal if edge weights are all the same
- Time Complexity:
	- b is the “branching factor (eg: 2)”, d is the depth of solution..
	- —> O(b^d)
- Space Complexity: O(b^d)
DFS properties
- not complete, not optimal (stops search when goal node is found, is not motivated to find cheaper paths)
- Time complexity: (m is max depth) O(b^m)
- Space Complexity: O(bm) because once we’ve explored a node to its depth, we can discard it !
Iterative Deepening Search
- Combines BFS (complete, optimal) and DFS (low space complexity)
- Limit depth of DFS to prevent infinite paths
- Run DFS with depth limits 0, 1, 2, … L
	- Complete, Cost Optimal
	- Time Complexity: O(b^d), Space Complexity: O(bd)
Uniform Cost Search
- Expands nodes with cost less than cheapest solution
- If c* is cheapest cost and e is the least action cost, the tree depth will roughly be C*/e
- Complete, Optimal (this is dijkstra's shortest path algorithm!)
- Time/Space complexity: O(b^(C* / e))
- Uhh class exercise solution: abcecdf ??