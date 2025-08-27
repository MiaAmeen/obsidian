[[lecture03.pdf]]

1. Simple Reflex Agent
	- Select action based on the current percept
	- Does not track history of percept-action
	- Fails if the environment isn’t fully observable![[Screenshot 2025-01-16 at 12.26.10 PM.png]]![[Screenshot 2025-01-16 at 12.26.36 PM.png]]

2. Model based reflex agent
    - Keeps an internal state of the world to address partial observability
    - Internal state updated using 2 kinds of info :
	    - Transition model:
			- How does state change based on agent action ?
			- How does state change independent of agent action ?
		- Sensor Model:
			- What is the current state given the agent's percepts?
	![[Screenshot 2025-01-16 at 12.27.28 PM.png]]
	![[Screenshot 2025-01-16 at 12.27.49 PM.png]]

3. Goal based Agent
    1. Employs goal with world state, and transition/sensor models
    2. Compute SEQUENCE of actions to achieve goals using search and planning techniques
    3. More flexibility in building agents
	![[Screenshot 2025-01-16 at 12.28.23 PM.png]]
	![[Screenshot 2025-01-16 at 12.28.46 PM.png]]
	- FIRST(plan) pops the first action off of the plan to do.
    - The plan does NOT change. 

4. Utility based agent
    1. Issue with goals: they specify desired states but NOT the QUALITY of the plans.
    2. Employs utility function (cost?time?) while computing the plan
        1. An internalization of performance measure (rational agents maximize expected utlity)
	![[Screenshot 2025-01-16 at 12.29.00 PM.png]]
[End of chapter 2]

5. Learning Agent
    1. What are the physics of the world Im in? How do my actions affect its evolution?
    2. **Any agent (model, goal, utility) can learn**
    - learning element: responsible for making improvements
    - performance: responsible for selecting actions
    - critic: provides feedback on how well agent does based on performance standard
    - Problem generator: suggests exploratory actions to the agent
	![[Screenshot 2025-01-16 at 12.29.22 PM.png]]

1. Environment Representation
    1. Model it at an appropriate level of abstraction
    2. Atomic: black box without any internal structure (eg, CityA, CityB etc, no detail about city itself)
    3. Factored: vector of attributes including booleans, symbols, etc (CityA: 1.3mil, 500m^2, etc)
    4. Structured: objects related to other objects: {CarA: 5gal, lights_on}, {RoadA: }, CarA-on-RoadA

2. Problem solving agent
    1. Agent that plans ahead
    2. **Employs search to compute a plan**
    3. Problem solving process:
        1. Formulate goal, then problem, then search to find plan, execute plan

3. Problem definition
    1. State space: set of possible states
    2. Initial state: where do I start?
    3. Goal state: state where some desirable property holds
    4. actions: all available actions
    5. Transition function: state resulting from executing an action in a given state 
	    1. f: S x A —> S
    6. Cost function: expense of an action
4. Solution is a path from the start to goal state
5. Optimal solution is the lowest cost