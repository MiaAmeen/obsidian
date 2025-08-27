#### ABSTRACT

This paper discusses the effectiveness of different types of neurons in training deep neural networks, specifically comparing logistic sigmoid neurons, hyperbolic tangent (tanh) neurons, and rectifying neurons (also known as ReLU neurons).

**Logistic Sigmoid vs. Hyperbolic Tangent Neurons:**
- Logistic sigmoid neurons are considered more biologically plausible, meaning they resemble how real neurons in the brain might behave.
- However, hyperbolic tangent (tanh) neurons are known to perform better in training multi-layer neural networks, likely because they handle gradients more effectively during backpropagation.

**Rectifying Neurons (ReLU):**
- The paper argues that rectifying neurons (ReLU) are an even better model of biological neurons than logistic sigmoid neurons.
- ReLU neurons introduce a "hard non-linearity" (they output zero for negative inputs and the input value itself for positive inputs) and are non-differentiable at zero. Despite these properties, they perform as well as or better than tanh neurons.
- ReLU neurons create sparse representations (many activations are zero), which is particularly useful for data that is naturally sparse (e.g., data with many zero values, like in images or text).

Key Findings:
ReLU networks can achieve state-of-the-art performance without requiring unsupervised pre-training. This is significant because earlier deep learning models often relied on unsupervised pre-training (e.g., using autoencoders) to initialize weights before supervised training.
The results suggest that ReLU networks can perform well on purely supervised tasks, even with large labeled datasets, closing the performance gap between networks trained with and without unsupervised pre-training.
This work is a milestone in understanding why training deep supervised neural networks was historically difficult and how ReLU neurons help overcome these challenges.

#### Introduction

1. **Divergence Between Machine Learning and Neuroscience**:
   - **Machine Learning Goal**: The primary objective is to create computationally efficient models that generalize well to new data.
   - **Neuroscience Goal**: The focus is on understanding biological principles, making predictions, and guiding future experiments.
   - The paper identifies areas where these objectives overlap, suggesting that insights from neuroscience can improve artificial intelligence (AI) and vice versa.

2. **Rectifier Activation Function**:
   - The paper introduces the **rectifier activation function** (`max(0, x)`), also known as **ReLU**, as a way to bridge the gap between neuroscience and machine learning.
   - ReLU is a piecewise linear function that outputs zero for negative inputs and the input value itself for positive inputs. This simple function has interesting properties that make it effective for training deep neural networks.

3. **Inspiration from the Brain**:
   - The design of deep neural networks is partly inspired by the **mammalian visual cortex**, which processes visual input in stages (e.g., detecting edges, shapes, and more complex patterns).
   - Deep networks learn hierarchical features similar to those observed in the brain, with lower layers capturing simple features (e.g., edges) and higher layers capturing more complex, invariant representations.

4. **Breakthrough in Training Deep Networks**:
   - A major breakthrough in deep learning occurred in 2006 with the introduction of **Deep Belief Networks (DBNs)** and **unsupervised pre-training** (e.g., using autoencoders). This helped address the challenges of training deep networks.
   - The paper builds on this work by exploring the use of **rectifier nonlinearities** (ReLU) as an alternative to traditional activation functions like **hyperbolic tangent (tanh)** or **sigmoid**.

5. **Key Contributions of the Paper**:
   - The paper investigates the use of ReLU in deep networks and compares it to tanh and sigmoid activations.
   - It introduces **L1 regularization** on activations to promote sparsity and prevent numerical issues.
   - The experiments show that ReLU allows deep networks to achieve state-of-the-art performance **without requiring unsupervised pre-training**, which was previously considered essential.
   - ReLU networks also benefit from **semi-supervised learning** when large amounts of unlabeled data are available.

6. **Bridging Neuroscience and Machine Learning**:
   - ReLU units naturally lead to **sparse activations** (many neurons are "off" or zero), which is closer to how biological neurons operate.
   - This work helps bridge the gap between neuroscience and machine learning by proposing an activation function that is both biologically plausible and computationally effective.

#### Background

##### Neuroscience Observations
1. **Sparsity and Energy Efficiency in Biological Neurons**:
   - **Biological Insight**: Studies suggest that biological neurons encode information in a **sparse and distributed** manner. Only **1-4% of neurons** are active at any given time, which is a trade-off between representation richness and energy efficiency (since firing action potentials consumes energy).
   - **Machine Learning Gap**: Traditional feedforward neural networks (e.g., those using **sigmoid activation functions**) do not exhibit this sparsity. For example:
     - The **sigmoid activation function** has a steady-state regime around **0.5**, meaning neurons tend to fire at half their maximum rate, even with small initial weights.
     - This is **biologically implausible** and can hurt **gradient-based optimization** because it leads to less efficient learning.
   - **Proposed Solution**: The paper suggests that **rectifier activation functions (ReLU)** can address this gap. ReLU naturally produces **sparse activations** (many neurons output zero), which aligns better with biological sparsity and improves optimization.
2. **Non-Linearity in Activation Functions**:
   - **Biological Insight**: Biological neurons are often modeled using the **leaky integrate-and-fire (LIF)** model, which describes how neurons integrate incoming signals and fire action potentials.
   - **Machine Learning Gap**: The most commonly used activation functions in deep learning are the **logistic sigmoid** and **hyperbolic tangent (tanh)**:
     - **Tanh** is preferred over sigmoid because it has a steady state at **0**, which is better for optimization.
     - However, **tanh** enforces **antisymmetry** around 0 (i.e., `tanh(-x) = -tanh(x)`), which is not observed in biological neurons.
     - Biological neurons do not exhibit this strict antisymmetry, meaning their response to strongly inhibitory inputs is not simply the opposite of their response to strongly excitatory inputs.
   - **Proposed Solution**: The **rectifier activation function (ReLU)** is **one-sided** (i.e., it outputs zero for negative inputs and the input value for positive inputs). This property is more aligned with biological neuron behavior and avoids the antisymmetry imposed by tanh.

##### Advantages of Sparsity 
   - It was first introduced in neuroscience in the context of **sparse coding** in the visual system (Olshausen and Field, 1997), where it was observed that neurons in the visual cortex encode information sparsely.
   - Traditional models often use **sparsity penalties** (e.g., L1 regularization) to encourage sparse activations. However, these models typically produce **small but non-zero activations**, rather than true zeros.
   - The paper argues that **rectifier activation functions (ReLU)** naturally produce **true sparsity** (i.e., exact zeros) in activations, which is more biologically plausible and computationally advantageous.
**Advantages of Sparse Representations**:
   The section outlines several key benefits of sparse representations:
   - **Information Disentangling**:
     - One goal of deep learning is to **disentangle the factors** that explain variations in the data.
     - In a **dense representation**, small changes in the input affect most of the entries in the representation vector, making it highly entangled.
     - In contrast, a **sparse representation** is robust to small input changes, as the set of non-zero features remains roughly the same. This makes it easier to isolate and interpret individual factors.
   - **Efficient Variable-Size Representation**:
     - Different inputs contain different amounts of information, and sparse representations allow for **variable-size encoding**.
     - By varying the number of active neurons, a model can control the **effective dimensionality** of the representation for a given input, improving efficiency and precision.
   - **Linear Separability**:
     - Sparse representations are more likely to be **linearly separable** (or easier to separate with simpler models) because they operate in a high-dimensional space.
     - This is particularly useful in applications like **text processing**, where the raw data is already sparse (e.g., word counts in a document).
   - **Distributed but Sparse**:
     - **Dense distributed representations** are rich and efficient, but **sparse distributed representations** offer an even better trade-off.
     - Sparse representations are exponentially more efficient than purely local ones, with the efficiency depending on the number of non-zero features. They strike a balance between richness and computational efficiency.
 Nevertheless, forcing too much sparsity may hurt pre-
dictive performance for an equal number of neurons,
because it reduces the eﬀective capacity of the model.

#### Deep Rectifier Networks
##### Rectifier Neurons
1. **Rectifier Neurons in Neuroscience**:
   - Neuroscience literature suggests that **cortical neurons** are rarely in their maximum saturation regime. Instead, their activation can be approximated by a **rectifier function** (`max(0, x)`), which outputs zero for negative inputs and the input value for positive inputs.
2. **Properties of Rectifier Activation**:
   - **One-Sided Activation**: The rectifier function is **one-sided**, meaning it does not enforce symmetry or antisymmetry (unlike tanh or sigmoid). For example, the response to the opposite of an excitatory input is zero (no response).
   - **Symmetry/Antisymmetry**: If needed, symmetry or antisymmetry can be achieved by combining two rectifier units that share parameters.
3. **Advantages of Rectifier Neurons**:
   - **Sparse Representations**:
     - Rectifier neurons naturally produce **sparse activations** (many neurons output zero). For example, with uniform weight initialization, around **50% of hidden units** output zero.
     - Sparsity can be further increased using **sparsity-inducing regularization** (e.g., L1 penalty).
   - **Biological Plausibility**: Sparse activations align with how biological neurons operate, making rectifiers more biologically plausible.
   - **Mathematical and Computational Benefits**:
     - **Linearity on Active Paths**: For a given input, only a subset of neurons are active, and the computation is linear on this subset. This makes the network's output **piecewise linear**.
     - **Easier Gradient Flow**: Unlike sigmoid or tanh, rectifiers do not suffer from the **vanishing gradient problem** because gradients flow well along active paths.
     - **Cheaper Computations**: Rectifiers avoid expensive operations like computing exponentials (required for sigmoid/tanh) and can exploit sparsity for efficiency.
4. **Potential Problems and Solutions**:
   - **Hard Saturation at Zero**:
     - One concern is that the **hard saturation** at zero (i.e., outputting exactly zero for negative inputs) might block gradient backpropagation and hurt optimization.
     - To test this, the authors compare rectifiers to the **softplus activation** (`softplus(x) = log(1 + e^x)`), a smooth version of the rectifier. However, experiments show that **hard zeros** do not hurt training and may even help by focusing credit/blame on active (ON) units.
   - **Unbounded Activations**:
     - Rectifier activations are unbounded (they can grow arbitrarily large for positive inputs), which could lead to numerical issues.
     - To address this, the authors use an **L1 penalty** on activations, which promotes sparsity and prevents numerical problems.
   - **Ill-Conditioning**:
     - Rectifier networks can suffer from **ill-conditioning** of parameters, where biases and weights can be scaled in different ways without changing the overall function. This can make optimization more challenging.
5. **Comparison to Other Activation Functions**:
   - **Softplus vs. Rectifier**: While softplus is a smooth approximation of the rectifier, experiments show that **hard zeros** in rectifiers do not harm training and may even improve it.
   - **Symmetry/Antisymmetry**: Rectifier networks require **twice as many hidden units** as symmetric/antisymmetric activation functions (e.g., tanh) to represent symmetric or antisymmetric behavior in the data.
##### Unsupervised Pre training
idgaf

### Experimental Study

##### Image Recognition