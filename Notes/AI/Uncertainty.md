[[lecture17.pdf]]

- Decision Theory: rational decision-making under uncertainty = **probability theory + utility theory**
- Principle of **maximum expected utility** (MEU): A rational agent chooses an action to maximize its expected utility
###### Joint Distribution: $P(A\text{ and }B)$
- = $P(A) P(B)$  If A and B are **ABSOLUTELY** independent.
- = $P(A|B) P(B) = P(B|A) P(A)$  otherwise.
- Can be extended to any number of random variables:
	- $P(A,B,C) = P(A|B,C)P(B,C) = P(A|B,C)P(B|C)P(C)$
	- AKA Chain Rule.
###### **Conditional** probability
- $P(A | B) = \frac{P(A, B)}{P(B)}$
#### Summary
![[Screenshot 2025-03-18 at 9.40.00 AM.png]] 
**Conditional Independence 2: P(X | Z, Y) = P(X | Z)**
#### Bayes (Bae's) Rule
-  $P(A|B) = \frac{P(B | A) P(A)}{P(B)}$
	- P(X | Y) = Posterior probability, P(Y | X) = Likelihood, P(X) = Prior probability, P(Y) = Evidence
- $P(A|B) = \sum_{x} P(B|A) P(A)$
-  $P(A|B) = \alpha P(B | A) P(A)$
###### Probabilistic Inference by Enumeration
![[Screenshot 2025-03-18 at 8.58.07 AM.png]]





