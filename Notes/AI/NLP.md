[[Lecture23.pdf]] [[Lecture24.pdf]]

- N-gram: sequence of N words
	- **Unigrams**: {I, am, excited, to, learn, NLP}
	- **Bigrams**: {I am, am excited, excited to, to learn, learn NLP} 
- can classify a sentence using naive bayes:
	- $P(Class|w_1, w_2, . . . , w_n) = P(w_1|Class)P(w_2|Class) . . . P(w_n|Class)P(Class)$
- An ideal probabilistic approach is to use markov chain approximation: a word is conditionally independent of all other words given the previous N words.
	- if N = 1: $P(w_1, w_2, ... , w_n) = P(w_1) \times P(w_2|w_1) \times P(w_3|w_2) \times ... \times P(w_n|w_{n-1})$
	- N = 2: $P(w_1, w_2, ... , w_n) = P(w_1) \times P(w_2|w_1) \times P(w_3|w_1, w_2) \times ... \times P(w_n|w_{n-2},w_{n-1})$
###### N-gram language model
- Create a vocabulary $V$ from the training corpus
	- Keep words with frequency greater than some threshold
	- Limit the size of the vocabulary 
- For words that are outside the vocabulary, use unknown token "unk"
- Use of tokens for start \<s> and end of sentence \</s> ![[Screenshot 2025-04-20 at 3.04.41 PM.png]]
Problem: missing N-grams of interest!
- $P(w_n|w_{n-1}) = \frac{count(w_{n-1}, w_n)}{count(w_{n-1})}$
Solution: Add k-smoothing:
- $P(w_n|w_{n-1}) = \frac{count(w_{n-1}, w_n) + k}{count(w_{n-1}) + k * |V|}$
###### Part of Speech (POS) Tagging
![[Screenshot 2025-04-20 at 3.09.24 PM.png]]
- used for text to speech and stuff ?
- Markov model for POS Tagging: ![[Screenshot 2025-04-20 at 3.10.13 PM.png]]

###### Grammar
- set of rules that sentences in a language follow
- natural language grammar: not deterministic!
- Sentence phrase structure can be parsed from grammar rules: ![[Screenshot 2025-04-20 at 3.11.56 PM.png]]
- Can be formulated as a search problem, where start state = list of words, goal state is single item S, and actions are grammar rules. costs are inverse of probability of rules in the search path.

###### Word Vectors
- one hot vector
- word by word co-occurrence mx ![[Screenshot 2025-04-20 at 3.14.18 PM.png]]
- word by category co-occurrence mx ![[Screenshot 2025-04-20 at 3.14.47 PM.png]]

###### Word Embeddings
- word2vec, GloVe, etc. better than one hot encoding.

#### RNN
- Benefits: shared weights for same inputs, flexible input size.
- Risks: vanishing/exploding gradients problem.
	- nearby context bias: hidden state has more information about closer than farther words
	- fixed context size limit ?
	- slower sequential processing
- Types: one to many, many to one, many to many.

#### LSTM
- ?
#### Transformers
- recurrence replaced with **self-attention** layer - computes how much attention each word should pay to every other word in the sequence
- single layer transformer has self attention, feedforward layer, and residual connections