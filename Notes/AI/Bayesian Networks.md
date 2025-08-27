[[lecture18.pdf]]

- A full joint distribution table requires exponential space $O(2^n)$ where n is the no of variables involved.
- Bayesian Network addresses this:
	- probabilistic DAG
	- node X represents random variable
	- an edge (X,Y) represent **direct** influence from X on Y
		- Make sure that each node $X_i$ has a minimal set of parents such that $P(X_i | X_{i-1}, ..., X_1) = P(X_i | parents(X_i))$ !!!!
	- Each node has a conditional probability table (CPT): $P(X_i | Parents(X_i)$ (where Parents return parent nodes). Generally, causes precede effects.
	- Join Distribution is now defined as: $P(X_i, ..., X_n) = \prod_{i=1}^{n} P(X_i | parents(X_i))$
Example: ![[Screenshot 2025-03-28 at 12.46.31 PM.png]]
![[Screenshot 2025-03-29 at 3.13.34 PM.png]]
**Note: $P(J | M, A, B, E) = P(J | A)$ because $parents(J) = A$ so that is the only variable J depends on!!**

### Inference
Of this form: $P(Q | e_1, ... e_k)$
- e are evidence variables (events we know happened), Q is the query variable (the probability of it happening is what we are solving for), and H are hidden variables (we don't know its influence yet)
##### Inference by Enumeration
![[Screenshot 2025-03-29 at 5.24.13 PM.png]]
![[Screenshot 2025-03-29 at 5.24.28 PM.png]]

#### Inference by Variable Elimination
???

#### Inference by Sampling
- Use several random samples from the bayes net to approximate probability
Example:![[Screenshot 2025-03-29 at 5.26.18 PM.png]]
For the following samples:
- c, -s, r, w
- c, s, r, w
- -c, s, r, -w
- c, -s, r, w
- -c, -s, -r, w
We can make these approximations:
- $P(W) =  <0.8, 0.2>$
- $P(C | W) = <0.75, 0.25>$
- $P(C|-r, -w)$ is undefined - do not have the corresponding sample

...do the exercise bitch