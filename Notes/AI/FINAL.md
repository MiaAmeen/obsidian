1. Machine Learning: induction. learning rules from input and output
	1. supervised (classification, regression), unsupervised(clustering), reinforcement
	2. Linear Regression
		- Loss: $J(\theta_0, \theta_i) = \frac{1}{2m} \sum_{i=1}^{m} (\hat{y_i} - y_i)^2$
		- derivative w.r.t. w: $\frac{1}{m} \sum_{i=1}^{m} \hat{y_i} - y_i$
		- derivative w.r.t. b: $\frac{1}{m} \sum_{i=1}^{m} (\hat{y_i} - y_i)x_i$
	3. Logistic Regression: $g(z) = \frac{1}{1 + e^{-z}}$, $0 \leq g(z) \leq 1$
		1. Loss: $J(\theta_0, \theta_1) = -\frac{1}{m} \sum_{i=1}^m (y_i \log \hat{y}_i + (1-y_i) \log(1 - \hat{y}_i))$ 
	4. Regularization: reduce model complexity and overfitting.  $J(\theta) += \lambda \sum_{j=1}^n \theta_j^2$
	5. Clustering: K-means. Randomly initialize k centers. Assign nearest data points to each cluster. Update k centers. repeat. Loss: $J(c_1, ..., c_m, \mu_1, ..., \mu_k) = \frac{1}{m} \sum^m_{i=1}||x_i - \mu_{c_i}||^2$
	6. Naive Bayes: assumes all features are conditionally independent of each other given class.
	7. Neural Networks: "universal approximator". Forward pass + backpropagation.
		1. activations: sigmoid, tanh, relu, leaky relua
	8. Metrics
		- accuracy = $\frac{TP + FN}{TP + FP + FN + TN}$
		- recall = $\frac{TP}{TP + FN}$
		- precision = $\frac{TP}{TP + FP}$
		- F_1 = $\frac{2 * Precision * Recall}{Precision + Recall}$
	9. Training/Evaluation: remember, error vs model complexity curve...
2. CNN, Convolution (**valid** vs **same**):
	1. output size: $[\frac{h + 2p − f}{s} + 1] \times [\frac{w + 2p − f}{s} + 1]$. 
	2. kernel depth = input channels, output channels = no of kernels.
	3. Parameters per layer = $((f \times f \times inputChannels) + 1) \times numKernels$
	4. Loss: 
		- MSE: $\frac{1}{m} \sum_{i=1}^m (y_i - \hat{y_i})^2$
		- Cross Entropy for classification: $-\frac{1}{m} \sum_{i=1}^m \sum_{j=1}^k (y_{ij} - \hat{y_{ij}})^2$
3. NLP
	1. sentences --> N-grams. 
	2. Classification (spam ham?): use naive bayes, word is conditionally independent given previous N words. POS Tagging: 
	3. N-gram lang model: use start, end, and unk tokens to tokenize sentences. Then $P(w_n|w_{n-1}) = \frac{count(w_{n-1}, w_n)}{count(w_{n-1})}$
		1. k-smoothing: $P(w_n|w_{n-1}) = \frac{count(w_{n-1}, w_n) + k}{count(w_{n-1}) + k * |V|}$
4. RNN, LSTM, Transformers
5. Ethics
	1. Joint ACM/IEEE-CS SWE Code
		- SWE must act in the best interests of the (1) **Public**, (2) **Client and Employer**. Ensure (3) **Product** quality, maintain good (4) **Judgement**, advance their (5) **Profession**, be fair to their (5) **Colleagues**, and their (6) **Self**?.
	2. AI Risks: privacy, unemployment, bias + discrimination, murder !! eg: "Pause Giant AI Experiments: An Open Letter"... no pause.
		1. Reputational, Financial, and Legal risks.
	3. EEE Ethically Aligned Design for Autonomous and Intelligent Systems.
		- Don't infringe upon **human rights**
		- Prioritize **Well-being**
		- Make sure designers take **accountability**
		- ensure systems are **transparent**
		- Minimize **Misuse** and raise **Awareness** of risks