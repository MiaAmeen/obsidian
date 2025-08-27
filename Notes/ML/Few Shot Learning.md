
- AKA N-ways, K-shot or simply K-shot classifier
- Works well when the model is pre-trained
- Falls under paradigm of "meta-learning"
- Support set: K (classes) x N (samples per class) demonstrations for training
- Query Set: The test input.

Machine Learning Training: 3 basic steps
1. Define the function $f(X) = Y$: what unknown are we solving for?
2. Define the loss $L(\theta)$: How do we penalize model performance ?
	1. $L(\theta) = \sum^{K}_{k=1} e_k$ where k are the samples, and e is the error.
	2. Must choose $\theta^* = arg\text{min}L(\theta)$ that is, find the set of parameters that minimizes the loss.
3. Optimize the model: SGD ? Adam ? --> $f_{\theta^*}$ the final function learned by learning the "rules" from the data

Limitations:
- lots of parameters to learn, but limited labeled training data = poor generalization and overfitting
- If the data is insufficient to constrain the problem, one possible solution is to gain experience from other simiilar problems; hence --> **meta learning**)

What is Meta-Learning?
- "learning to learn", performs learning through multiple training episodes.
	- i.e., can we lean the function ?
- During this process, it self-improves. 
- Demonstrates better generalization abilities, esp with limited data.

1. Step 1: idk
2. Define the loss function for learning algorithm
	1. Loss is computed from TEST samples
3. Optimize ?

ML vs Meta-Learning
- ML finds a function f
- Meta Learning finds a function F that finds f
- um

What is learnable in a learning algorithm?
- 