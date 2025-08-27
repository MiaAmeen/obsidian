#### Perceptron
- y = WX - T
	- output of any perceptron = 1 if ( the weighted sum of its inputs - bias ) > 0 else 0
	- eg: $w_1x_1 + w_2x_2 - T$
- Can replace "threshold" with sigmoid
- Perceptron for logic gates:
	- AND: w1 = w2 = 1, T = 2 (single layer)
	- OR: w1 = w2 = 1, T = 1 (single layer)
	- XOR:  (multi layer, nonlinearly separable)
- Learning Rule: $w^{k+1} = w^k + \lambda [y_i - f(w^{k}, x_i)]x_i$
	- lambda is the learning rate
	- $[y_i - f(w^{k}, x_i)]$ is the error rate.
	- Because f(w, x) is a linear combination, perceptron fails for nonlinearly separable problems (complex decision bounds)
#### General ML Recipe
1. Training Data
2. Decision (linear, logistic, NN) and loss (MSE, Cross Entropy) functions
	1. Must be differentiable ! (for backpropagation)
	2. logistic: $f(x) = \frac{1}{1 + exp(-a)}, a=wx$
	3. linear: $f(x) = wx$
3. Goal (minimize loss?)
4. Train with SGD (Slope of cost function determines adjustment direction, learning rate determines "adjustment magnitude". take small steps OPPOSITE the gradient.)
#### Multi-Layer Perceptron
- can compose boolean functions, real-valued functions, etc. Universal classifiers; can capture any classification boundary. One-layer MLP is also universal, but no of neurons required could be arbitarily large.
- Deeper network preferred over just a couple hidden layers, because few layers mean potentially exponential no of neurons needed
- lower layers capture simple patterns, deeper layers = complex patterns

# CNN
- Learns feature abstractions in hierarchical layers. Shift invariant.
- Layers: Convolutional, Max-Pooling (or mean), Fully-connected Layer
- Convolution: kernel (filter), stride, padding
	-  2D: convnet. 1D: Time-delay NN
	- Output Size (after convolution) = $\frac{\text{InputSize } + 2\text{Padding } - \text{ KernelSize }}{\text{Stride}} + 1$
		- Number of Parameters:
	- Output Size (after pooling) =  $\frac{\text{InputSize } - \text{ PoolingSize}}{\text{Stride}} + 1$
- Receptive Field: size of the region in the input that produces the output feature
- Activation: ReLU, sigmoid, tanh
- Softmax: multiclass sigmoids, meaning they are used in determining probability of multiple classes at once. 
	- Since the outputs of a softmax function can be interpreted as a probability (i.e.they must sum to 1), a softmax layer is typically the final layer used in neural network functions.
- Architectures: LeNet (LeCun et. al. 1998), AlexNet (Aex et. al. 2012). ImageNet (ILSVRC winner)

# Transfer Learning

#### Supervised Learning/Classification
- labeled observations split into train and test sets, machine learner takes inputs (attributes) to predict output task.
	- assumes train/test set are from the same distribution
- Do we have to re-train the model on every new dataset, even if they are similar..?
	- Eg: Task: Dog/Cat classifier. Task similar but not directly related to original task: Elephant/Tiger Classifier, Dog/Cat cartoon classifier...
- Consists of three main sub-branches:
	1. Inductive: source and target models differ but share identical features.
		--> MTL, Self-taught Learning
	2. Transductive: source and target tasks are same, but their domains are different.
		--> Domain Adaptation, Covariance Shift
	3. Unsupervised Transfer Learning: supervised during pre-training, unsupervised during fine-tuning.
- Process:
	1. Delete the last layer (classification)
		1. NOTE: which layer can be transferred? speech --> usually last few layers; vision --> first few.
	2. Delete weights feeding into the last output layer (usually FC layer)
	3. Create new randomly intialized weights for removed layer
	4. use new dataset from target domain to train this classification layer.
		1. New dataset (target data) usually much smaller and more specific.
- Transfer Learning vs Fine-Tuning:
	- finetuning works better if new data is large enough and similar to the source dataset.
![[Screenshot 2025-03-20 at 1.34.06 PM.png]]
#### Domain Adaptation
- A classifier trained on one domain may perform poorly on another domain
	- The domain shift is defined as a difference in the distribution of the source and target samples, i.e., same features but different distributions (cartoons vs real images)
![[Screenshot 2025-03-20 at 1.39.33 PM.png]]

# Semi-Supervised Learning
1. Supervised Learning: Given object-label pairs, find predictive relationship between the two.
2. Unsupervised Learning: given only objects, find interesting structures in the data; group similar objects.
3. Semi-Supervised: Supervised learning + additional unlabeled data OR Unsupervised + labeled data
	1. Motivation: data is cheap/free, but ground truth is not.
	2. --> combine small, labeled dataset with lots of unlabeled samples to improve performance.
#### SSL
- Assumptions:
	- Smoothness: examples in high density area must have same class label, examples separated by low density area must be different.
- Process:
	1. Train supervised model on small labeled data.
	2. Make predictions on unlabeled data.
	3. From unlabeled dataset, select examples with label predictions of highest probability and add these high-confidence predictions to labeled dataset!
	4. Repeat til convergence.
- Advantages/Limitations
	- Can be applied to any base learning algo as long as it can produce "confidence weights"
	- Difference b/w cootraining and self training...
- Inductive vs Transductive:
- Yarowsky
	- Decision List: an ordered set of rules. Given an instance x, the first applicable rule determines the class label. Assign weight (parameters) to these rules instead of ordering them, based on priority. Self training with decision list base classifier. Predicted label is k if confidence of applied rule is above a threshold. instance may become unlabeled in the future.
		- modified version: threshhold is 1/(no of labels); instance STAYS labeled once it is labeled, but the label may change.
	- Used for WSD (word sense disambiguation): Specify the most appropriate sense (meaning) of a word in a given sentence.
	- Modified
- Co-training
	- Use when multiple sources of info come with respective rules that help determine label. Use small labeled sample to learn initial rules. Look for unlabeled examples where one rule is confident but other isnt. Training 2 classifiers, one on each type of info. Using each to help train the other.
#### Semi-Supervised Transductive SVM:
 ![[Screenshot 2025-03-20 at 1.03.03 PM.png]]
aim for separator w large margin (in low-density area) wrt labeled and unlabeled data
#### Expectation Maximization (EM)
3 key probabilities: 


# Active Learning
goal: machine automatically and adaptively selects most informative data for labeling. Example: Label a sample near best decision boundary based on labels seen so far


# Multi Task Learning
Task: Given Dataset D and loss function L, make a model f.
Single Task Learning: One input and output space, one task, one probability distribution.
**MTL**: Same domain (input/output space), different tasks and corresponding probability distribution
	Goal --> One classifier that works for all tasks?

Advantages of Deep Learning:
- No hand coded feature engineering
- Significant performance gains
Limitations:
- Large datasets and compute needed.
- large data? --> broad generalization
- breaks when theres "high variance" ?
What if we need to quickly learn something new? --> MTL fixes these limitations. Use MTL when:
- tasks share a common structure and are NOT highly distinct.
- New objective becomes to minimize the sum of losses for ALL tasks.
	- Vanilla MTL: objective function treats all tasks equally
	- Weighted Task Objective: gives different importance to tasks by either manually assigning weights (based on priority) or dynamically assigning (adjust throughout training)
Can MTL be reduced to STL by merging datasets?
- Model may not differentiate between tasks effectively
- Can be issues with aggregation, combining different datasets can lead to high variance.
Challenges
- Negative transfer: training multiple tasks harms performance. caused by:
	- Optimization challenges: cross-task interference and different learning rates
	- "limited representational capacity": MTL networks usually need to be much bigger than single task ones.
- Overfitting
	- In case of overfitting: share more parameters!
#### Conditioning
- Why might multiplicative conditioning be a good idea?
	- more expressive per layer
	- recall: multiplicative gating




