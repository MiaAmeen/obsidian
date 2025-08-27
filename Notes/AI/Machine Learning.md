[[lecture21.pdf]] [[lecture22.pdf]]

Premise + Rules = Conclusion
- **Deduction**: drawing conclusions from premises using logical reasoning
	- always correct, infers the conclusion, sound VS
- **Induction**: drawing conclusions from observations (data). 
	- not always correct, infers the rule, approximate what ML does !

Types:
- Supervised Learning: discrete output: classification. Continuous output: Regression.
- Unsupervised learning: clustering, anomaly detection
- Reinforcement Learning: learn optimal policies.

- Linear regression: data, parameters, loss, goal: minimize loss
	- Loss: $J(\theta_0, \theta_i) = \frac{1}{2m} \sum_{i=1}^{m} (\hat{y_i} - y_i)^2$
		- $\hat{y_i} = b + wx_i$
	- gradient descent: derivative of loss w.r.t. parameters
		- derivative w.r.t. w: $\frac{1}{m} \sum_{i=1}^{m} \hat{y_i} - y_i$
		- derivative w.r.t. b: $\frac{1}{m} \sum_{i=1}^{m} (\hat{y_i} - y_i)x_i$
- Logistic Regression (technically classification)
	- Logistic function $g(z) = \frac{1}{1 + e^{-z}}$, $0 \leq g(z) \leq 1$
	- Loss function:  Cross Entropy! $J(\theta_0, \theta_1) = -\frac{1}{m} \sum_{i=1}^m (y_i \log \hat{y}_i + (1-y_i) \log(1 - \hat{y}_i))$
##### Regularization
- small data, too many parameters?
	- --> regularization addresses complexity and overfitting by minimizing absolute values of the parameters
	- accomplishes this by adding a penalty to the loss:
	- $J(\theta) += \lambda \sum_{j=1}^n \theta_j^2$
##### Training and Evaluation
- Train: 60%, validation (dev): 20%, and test: 20%
- Validation: used to tune hyperparameters such as learning rate, regularization parameter, etc.
- Bias vs Variance:![[Screenshot 2025-04-03 at 9.28.01 AM.png]]
	- meep
##### Evaluation Metrics: Confusion Matrices
- ![[Screenshot 2025-04-03 at 9.31.28 AM.png]]
	- accuracy = $\frac{TP + FN}{TP + FP + FN + TN}$
	- recall = $\frac{TP}{TP + FN}$
	- precision = $\frac{TP}{TP + FP}$
	- F_1 = $\frac{2 * Precision * Recall}{Precision + Recall}$
	Some more:![[Screenshot 2025-04-03 at 9.39.03 AM.png]]
	![[Screenshot 2025-04-03 at 9.39.22 AM.png]]

Example:
![[Screenshot 2025-04-03 at 9.43.32 AM.png]]

#### K-Means Clustering
- group unlabeled data into clusters
	- Cluster assignment: Assign a data point to a cluster whose center is closest to it
	- Update cluster centers: Update the cluster centers to the average of the data points assigned to the cluster
- ![[Screenshot 2025-04-08 at 8.45.14 AM.png]]
- $c_i$ = index of cluster to which example $x_i$ is assigned
- $\mu_{c_i}$ = cluster center of the cluster to which $x_i$ is assigned  
- $J(c_1, ..., c_m, \mu_1, ..., \mu_k) = \frac{1}{m} \sum^m_{i=1}||x_i - \mu_{c_i}||^2$ = loss
- minimize the above function over all examples. In case you get stuck at local minima, run K-means multiples times with different, random initial $c_i$
#### Naive (Stupid) Bayes Model
- typically used as baseline for comparison
- Assumes features are conditionally independent of each other given the class !! (No crazy joint distribution)
- $P(C | f_1, ..., f_n) = \alpha P(f_1, ..., f_n | C) P(C) = \alpha \prod_i P(f_i | C) P(C)$ ![[Screenshot 2025-04-08 at 9.00.07 AM.png]]

#### Neural Networks
- universal approximator
- neuron = activation_function(linear combination of all outputs from previous layer).
###### Logistic Regression
- imagine a NN where z (activation) is the logistic function (described above)
- How do we find partial derivatives of weight w.r.t. loss ? ![[Screenshot 2025-04-08 at 9.29.44 AM.png]]
###### Training
- gradient descent: forward pass to compute activations, backward pass to compute gradients
- hyperparameters (activation func, no hidden layers/units per layer, learning rate, etc) are manually specified/tuned.
- Activations:
	- Sigmoid/tanh. Advantages: continuous + derivable. Disadvantages: vanishing gradient problem...
- Vanishing gradient:
	- with sigmoid and tanh, when reaching $-\inf$ or $+ inf$ the curve is basically flat and the gradient gets closer to 0. 
- Leak ReLU: $a = max(\alpha z, z)$ where $\alpha$ is usually 0.01

