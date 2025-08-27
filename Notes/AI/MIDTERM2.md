1. Propositional Logic
	1. vocab: knowledge-base: set of sentences; entailment: KB entails $\alpha$ iff $\alpha$ is true in ALL WORLDS where KB is true; Models: formally structured world with respect to which truth can be evaluated
	2. Inference Procedures: derive a from KB by procedure i
		1. **soundness**: procedure i only derives entailed sentence
		2. **completeness**: procedure i can derive ANY sentence that is entailed
	3. Important Laws: ![[Screenshot 2025-04-21 at 6.15.02 PM.png]]
	4. Validity vs Satisfiability
		1. **Validity**: a valid sentence is tru in all models.
		2. **Satisfiable**: true in some. **unsatisfiable**: never true. useful for proofs: 
			1. ***To show KB |= a, we should that KB and !a is unsatisfiable***
	5. **CNF**: series of ors joined by ands. (a and b) is NOT CNF. they become two separate statements. ![[Screenshot 2025-03-31 at 12.27.09 PM.png]]
2. FOL
	1. Assumes worlds contains objects, relations, and functions.
	2. **Quantification**: $\forall$ and $\exists$
		1. $\rightarrow$ is usually the connective used with $\forall$
		2. $\land$ is typically used with $\exists$
	3. forward chaining: facts --> goal. sound and complete for "first order definite clauses". may not terminate if a is not entailed. **Unavoidable**: entailment with definite clauses is semidecidable.
	4. backward chaining: goal --> facts. Depth first recursive proof search. incomplete due to infinite loops, inefficient due to repeated subgoals.
3. Uncertainty
	1. Joint Distribution: P(A, B, C)
		1. Product Rule: $P(X, Y) = P(Y|X)P(X) = P(X|Y)P(Y)$
			1. Absolute Independence: $X \bot Y$:  $P(A, B) = P(A)P(B)$
		2. Conditional Probability: $P(X | Y) = \frac{P(X, Y)}{P(Y)}$
			1. Conditional Indepence: $X \bot Y|Z$:  $P(X, Y|Z) = P(X|Z)P(Y|Z)$
				1. $P(X|Z, Y) = P(X|Z)$
		3. Chain Rule: $P(A,B,C) = P(A|B,C)P(B,C) = P(A|B,C)P(B|C)P(C)$
	2. Bayes Rule
		1. $P(Cause|Effect) = \frac{P(Effect|cause)P(Cause)}{P(Effect)}$ = diagnostic probability
			1. $Posterior = \frac{\text{likelihood } \times \text{ prior}}{\text{evidence}}$
4. Bayesian Networks
	1. eliminates need for full joint distributions by modeling variables as nodes in a graph where $P(X_i | X_{i-1}, ..., X_1) = P(X_i | parents(X_i))$
	2. Inference by: enumeration, variable elimination, sampling.
5. Sequential Decision Problems
	1. Markov decision process
		1. Example: Grid World. Results of actions are probabilistic. Future state depends only on current state, Rewards are preferred earlier rather than later (penalty applied to later rewards), how do we find optimal policy...?
		2. Bellman Ford Equations - repeat until convergence:
			- $Q^*(s, a)= \sum_{s'} T(s, a, s')[ R(s, a, s') + \gamma V^*(s') ]$: expected utility starting in state s and taking action a, and then acting optimally.
			- $V^*(s) = \max_{a} Q^*(s, a)$: expected utility starting in state s and acting optimally 
			- $\pi^* (s) = argmax_a Q^*(s, a)$: optimal policy, action that will maximize expected utility
6. HMM
	1. Markov models assume next state depends only on the previous one.
	