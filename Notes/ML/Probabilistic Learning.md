**Statistics vs Probability:**
Statistics helps us make inferences about the population on the basis of a random sample, while probability allows us to make a judgement about the likeliness of a specific event.
##### Probability
![[Screenshot 2025-03-17 at 8.52.58 PM.png]]
Three types of probability:
- Marginal: P(A)
- Joint: P(A and B)
- Conditional: P(A | B)

Basic Rules:
- Product Rule: 
	- $P(A, B) = P(A|B)P(B) = P(B|A)P(A)$
	- Can be extended to any number of random variables:
		- $P(A,B,C) = P(A|B,C)P(B,C) = P(A|B,C)P(B|C)P(C)$
		- AKA Chain Rule.
- Sum Rule: 
	- $P(A U B) = P(A) + P(B) - P(A, B)$
- Total Probability: if Ai are mutually exclusive and their probabilities sum to 1, then:
	- $P(B) = Sum(P(B | Ai)P(Ai)), 1 <= i <= n$
- Two events A and B are independent if:
	- $P(A, B) = P(A)P(B)$
	- That is, $P(A | B) = P(A)$. Then apply the product rule.
- Bayes Thm ![[Screenshot 2025-03-17 at 9.32.45 PM.png]]
	- Can be used for classification: Suppose we have a feature vector x and we want to decide if A or B is more likely given x. Then we can apply Bayes formula:
		- $P(A|x) = \frac{P(x | A) P(A)}{P(x)}$
		- where $P(X) = Sum ( P(x|))$
		- 