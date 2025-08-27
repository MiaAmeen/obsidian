[[lecture02.pdf]]
Agents
- perceives percepts through its environment through sensors and acts upon it through actuators
- agent function: maps percept sequence to an action
- agent program: concrete implementation; internal characterization
- qgent architecture: computing device with sensors/actuators
	- agent = architecture + program

Rational agents do the “right thing.” What is the right thing?
1. Performance Measure
	- How well does a rational agent perform?
	- Evaluates a sequence of environmental states

2. Rationality
	- For each possible perception sequence, the rational agent should select an action that is expected to **maximize its performance measure**, given the evidence provided by the perception sequence and knowledge the agent has.

3. PEAS description: 
	1. Performance measure, Environment (general description of what exists in the agent's world), Actuators (enables action), and Sensors (accepts input from the environment).
##### Task Environment
- Fully observable (board games) vs partially observable (can only perceive some part of the environment, eg, grocery store) vs unobservable (agent has no sensors)
- Single agent (everything else is the environment) vs multi agent (multiple agents influence each other’s performance measures)
- Deterministic: next state completely determined by current state and action; Stochastic: we know the probability distribution of the next state given current
- Episodic: agent experience is divided into separate, unrelated, atomic episodes each decision is independent of another; Sequential: agent current decision affects future (chess)
- Static environment unchanged while agent deliberates (chess) vs Dynamic: environment changes continuously (driving) vs Semidynamic
- Discrete (finite states) vs Continuous
- Known: outcomes/probabilities are known to agent; vs unknown. 
##### Function vs program vs architecture
- Agent function maps a percept sequence to an action
		f : p0, p1, p2, … pn —> a
- Agent program: concrete implementation of the function
- Architecture: computing device with sensors and actuators
	agent = architecture (body) + program (brain)