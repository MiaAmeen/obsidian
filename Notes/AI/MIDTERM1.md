1. AI Use Case
	- Agents, agent function, agent program, agent architecture. *A rational agent maximizes its performance measure.*
	- PEAS: Performance, Environment, Agents, Sensors
	- Task Environment properties: fully vs partially observable, deterministic vs stochastic, multi vs single agent, episodic vs sequential, fully known vs unknown, discrete vs continuous, static vs dynamic.
	- Problem description: initial and goal states, transitions, percept, actions, costs
	- Types: Simple reflex agent, model based reflex agent, goal based agent, utility based agent, learning agent (model, goal, utility agents can learn): has a learning element (makes improvements), performance element (responsible for selecting actions), critic (how well is the agent doing?), problem generator (suggests exploratory actions).
2. State space (set of all possible states, including start and goal state) search
	- **Completeness**: always returns either a solution if one exists or failure (no infinite loop). **cost optimality**: always returns cheapest solution.
	- [[UNINFORMED SEARCH]]: BFS, DFS, UCS
		- BFS: FIFO, queue. O(b^d), complete, cost optimal when edge weights are uniform
		- DFS: LIFO, stack. O(bm). m is max depth. Not complete or cost optimal.
		- UCS (Djikstra): Cheapest out, priority queue. O(b^(C* / e)) ??? complete, cost optimal.
		- Iterative Deepening Search: Combines cost optimality of BFS with space optimality of DFS
	- [[LOCAL SEARCH]] 
		- Only cares about final state. Doesn't keep track of paths/states that've been reached. Can get stuck at local maxima, plateaus, and "ridges"
		- stochastic hill climbing: randomly select uphill moves, probability proportional to steepness
		- random-walk hill climbing:
			- Greedy: with probability p, move to a neighbor with largest value
			- Random: With probability 1 - p, move to a random neighbor
		- random-restart hill-climbing:
			- multiple times with a randomly generated initial state (which is the best maxima?)
		- Local Beam Search: Instead of keeping 1 state, keep $k$ best states, generate their successor, iteratively keep k best states again. Stochastic version is randomly biased towards k best successors.
		- Genetic algorithms: obvious
	- [[INFORMED SEARCH]]
		- Search Heuristics
			- h(n): estimated cost of the cheapest path from the state at node n to a goal state. example: euclidian distance.
			- **admissible**: 
				- 0 <= h(n) <= h*(n) where h*(n) is optimal cost.
				- h(n) that never overestimates the cost. 'dominant' heuristic is closer to h*(n)![[Screenshot 2025-02-24 at 9.09.38 AM.png]]
			- **consistent**: If the heuristic is consistent, then h(n) - h(n') $\leq$ c(n, a, n'). To check whether a heuristic is consistent, ensure that for all paths, h(N) − h(L) ≤ path(N → L), where N and L stand in for the actual nodes. **Consistency implies admissibility**.
		- Greedy Best First Search: always expands node with lowest h(n). Does not consider path cost.
		- A* Search
			- expands a node with least sum of costs: f(n) = g(n) + h(n)
			- complete, cost optimal if heuristic is admissible, but uses lots of memory.
		- RBFS
			- three numbers being kept track of: best, alt, f_limit !!!
	- [[Game Theory]] Game Tree/Minimax/Alpha-beta pruning
		- Minimax: Time: O(b^m); Space: O(bm)
		- Alpha-beta: christ almighty
3. Offline vs Online Search
	- offline computes complete solution before acting (all the search tree algorithms traverse to find entire sequence of solution nodes). Online combines computation and action?
4. Physical states vs. belief states
	- physical states: vacuum world-does a square have dirt or not?
	- belief state: set of physical states that an agent believes are possible. useful when agent's percepts provide little to no information.
	- could be every possible subset of physical states.
5. [[Constraint Satisfaction Problem (CSP)]]
	- Constraint graph
		- nodes are variables; edges represent constraints among variables. Binary CSP: each constraint relates at most two variables.
	- Consistency: 
		- k-consistency: A CSP is k-consistent if, for any set of k−1 variables and for any consistent assignment to those variables, a consistent value can always be assigned to any kth variable.
		- node: k=1; arc: k=2; path: k=3
	- AC-3 algorithm 
		- repeatedly revise binary constraints, update the domain, and then update affected constraints.
	- Backtracking algorithm: assign one variable at each step. check constraints at each step, only consider values that don't conflict previous assignments.
	- Forward checking: Keep track of domain, terminate search when any variables have no legal values remaining
	- Minimum remaining value (MRV) heuristic: choose a variable with fewest legal values
	- degree heuristic: choose a variable with most constraints on remaining variables

#### 

|     | Time          | Space         | Complete? | Optimal? |
| --- | ------------- | ------------- | --------- | -------- |
| BFS |               | b^d           | yes       | yes      |
| DFS |               | bm            | no        | no       |
| UCS | O(b^(C* / e)) | O(b^(C* / e)) | yes       | yes      |

