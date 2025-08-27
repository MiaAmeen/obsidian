[[lecture19.pdf]]
### Markov Decision Process (MDP)
- models fully observable and stochastic sequential decision problem defined by:
	- set of states $s \in S$
	- set of actions $a \in A$
	- Transition function $P(s' | s, a) = T(s, a, s')$
	- Reward function $R(s, a, s')$
- Markov property: future state depends ONLY on current state.
- Policy: maps state to an action: $\pi: S \rightarrow A$
- Optimal Policy ($\pi^*$): maximizes expected utility
	- Generally: earlier rewards preferred over later ones. Future rewards discounted using discounting factor $\gamma: 0 \leq \gamma \leq 1$ which prevents issue of infinite rewards for infinite sequence of actions.  Later rewards are penalized by powers of $\gamma$ .
- *Solving an MDP means finding the optimal policy $\pi^*(s)$.*
- **Value of a state:** $V^∗(s)$ = expected utility starting in state s and acting optimally 
- **Q-value of a state: $Q^∗(s, a)$** = expected utility starting in state s and taking action a, and then acting optimally.
#### Example: Grid World
- results of actions are probabilistic, i.e., if you choose action a = move forward, there is a 80% chance you will, vs 10% you move either to the left or right instead.
![[Screenshot 2025-03-29 at 11.04.51 PM.png]]
**Bellman Equations**
- $Q^*(s, a)= \sum_{s'} T(s, a, s')[ R(s, a, s') + \gamma V^*(s') ]$
- $V^*(s) = \max_{a} Q^*(s, a)$
- $\pi^* (s) = argmax_a Q^*(s, a)$
##### Value Iteration
- Initialize $V_0^* (s)$ with zero or whatever
- then update $V_{i+1}^* (s)$ iteratively using the Bellman equation. Repeat until convergence.

### Reinforcement Learning
- Agent performs an action $a$ on the environment $\rightarrow$ environment gives agent a reward $r$ and the state transitions to next state $s$ .... cycle continues
- Agent learns to max expected rewards
- This is online learning vs MDP, which is offline learning because T (transition) and R (rewards) are given
- Model-based vs Model-free RL
	- Model-based learning involves estimating T and R (learn the probabilities from observed episodes) and then solving the MDP to obtain the policy. Model-free: no estimations, eg: "temporal difference learning"
- Passive vs active RL
	- In passive RL, policy is fixed and agent learns values of states
	- In active RL, policy is not fixed and agent selects the actions to execute; goal is to learn optimal policy

### 6 Axioms of Utility Theory

$\$

**Thm**: If an agent’s preferences satisfy the axioms, then a utility function exists such that:
- if i prefer A over B, A has more utility than B. Pretty obvious.

Utility of a lottery is the expected utility of its outcomes; p * Utility(event)
- $U(L) = pU(A) + (1-p)U(B)$
