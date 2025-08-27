Traditional Programming:
Data + Rules = Output
vs ML: 
Data + Output = Rules

ML = Study of algorithms that improve their performance P at some task T with experience E (<P, T, E>)

**Data Taxonomy**
- Structured: conforms to DB model, characterized by fields and data types
- Unstructured: images, video, web pages, no pre-defined data model
- Semi-structured: lacks a strict structure. For example, email, documents.
LOTS of data nowadays... leading to emergence of a "new paradigm", data guided discovery (industrial revolution, scientific revolution, now, data revolution)

# ATML (Advanced Topics ML)

- Statistical learning and theory
	- Probability distributions
	- Bayes’ theorem for Gaussian variables
	- Parameter estimation
	- Bayesian inference
	- Non-parametric methods (e.g., kernel density)
	- Mixture models and EM
	- Probably Approximately Correct (PAC) learning framework
- Neural networks and basic concepts in deep learning
	- basic feed forward (ff) neural networks (nn)
		- considered "universal function approximators"
	- Learning weights, and basics of backpropagation
	- Activations, cost functions, gradient descent
	- deep learning: types of layers and architectures
- Transfer learning
	- Takes advantage of common features between various learning problems
- Semi-supervised learning (weakly supervised)
	- Data is cheap, ground truth is not
	- Combines small labeled datasets with unlabeled samples to improve model performance
- Active learning... idk
- Multi-task learning
	- learn multiple tasks while exploiting commonalities and dissimilarities b/w them, at the same time achieving better learning efficiency and prediction accuracy when compared to individually learning those tasks separately
- Multi-instance learning... idk
- Knowledge/Physics guided learning
	- systematic approach to incorporate knowledge/physics into learning process (PiNNs)
- Representation learning... auto encoders!
- Federated learning
	- An ML setting where many clients (e.g. mobile devices or whole organizations) collaboratively train a model under the orchestration of a central server (e.g. service provider), while keeping the training data decentralized. FL embodies the principles of focused data collection and minimization, and can mitigate many of the systemic privacy risks and costs resulting from traditional, centralized machine learning and data science approaches.