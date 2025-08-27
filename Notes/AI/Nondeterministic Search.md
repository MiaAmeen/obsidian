[[lecture07.pdf]]
#### Nondeterministic Actions
- informed/uninformed search assume deterministic environment
- Now, agent doesnt know what state is reached after taking action
- Instead of sequential, solution is conditional plan
- Solutions of non deterministic problems are TREES instead of sequence
- Agent's choices are OR nodes. Environments choice of outcome of an action are AND nodes.
#### AND - OR Search Tree
##### Example: Erratic vacuum world
![[Screenshot 2025-02-01 at 1.48.57 PM.png]]
--> Solution is a subtree that:
- has a goal node at every lead
- specifies one action at each OR node
- Includes every outcome branch at each AND node
- variations of BFS DFS A* can be used!
##### Slippery vacuum world
![[Screenshot 2025-02-01 at 2.01.02 PM.png]]

#### Searching with no observations
- Sensorless problem: agent’s percepts provide no information 
- **Belief state** is a set of physical states that an agent believes are possible. Fully observable - agent always knows what it believes.
- ![[Screenshot 2025-02-24 at 1.10.01 PM.png]] ![[Screenshot 2025-02-24 at 1.10.08 PM.png]]
- Search in the space of belief states rather than physical states
#### Belief-state Problem
- State space: every possible subset of physical states; with N physical states, there can be 2^N belief states 
- Initial state: typically a set with all physical states 
- Actions: union of legal actions for all physical states in belief-state (Or intersection if illegal actions are possible) 
- Transition model: belief-state resulting from applying an action in a given belief-state b′ = result(b, a) = {s′ : s′ = result(s, a) and s ∈ b} 
- Cost function: (tricky) cost of executing an action can be calculated from the cost of applying an action in a physical state 
- Solution is a path from the start state to a goal state
##### Deterministic Sensorless Vacuum World
![[Screenshot 2025-02-01 at 7.34.37 PM.png]]

#### Searching in Partially Observable Environments
![[Screenshot 2025-02-01 at 7.37.55 PM.png]]
##### Transition Model in Partially Observable Search:
![[Screenshot 2025-02-01 at 7.41.40 PM.png]]
![[Screenshot 2025-02-01 at 7.53.26 PM.png]]

### Online Search
- we've exclusively looked at offline search so far (compute complete solution before acting)
- online search combines computation and action: useful for dynamic/semidynamic environments with penalties for delay
- useful for nondeterministic environments bc agent can focus on contingencies that actually happen than those that might happen
- necessary in unknown environments
	- eg: roomba learns floor plan as it cleans
- Agent knows the following:
	- ACTION(s): legal actions in state s
	- c(s, a, s'): cost of applying action a; agent cant use this until it knows that s' is the outcome
	- GOAL-TEST(s): heuristic function that estimates path cost to goal state
- Agent objective: reach goal state, minimize cost
- Competitive ratio: ratio of actual cost with optimal cost in known environment
- Vulnerable to dead ends. *No algorithm can avoid dead ends in all state spaces.*
- Assume that state space is **safely explorable**: a goal state is reachable from every state.
- agent can only explore the successors of current state
	- cannot bounce to distant state in different path like in A*
- DFS can be used assuming actions are reversible.
- Hill climbing can be used too - but random restart wont work (no random spawns possible.)
	- random walk hill climbing possible - but very slow. will eventually find goal in finite safely explorable state space. travels and reverses.


