
Authors explore: how to better select in-context examples to unleash GPT-3’s few-shot capabilities ?

Contributions:
- Understanding of the sensitivity of GPT's few-shot capabilities w.r.t. the selection of in-context examples!
- a kNN retrieval module that finds nearest neighbors of a given test sample among all training instances available as the in-context examples. In-context examples that are closer to the test sample in the embedding space consistently give rise to stronger performance!
- fine-tuning the retrieval module boosts performance
- performance improves as number of examples available for retrieval increases
###### Method
Impact of in-context examples
- compared the performance of two selectors: one selected 10 nearest examples for ICL, the other selected the 10 farthest examples. Obviously, the former performed better.

Knn Augmented in conText Example selection (KATE)
![[Screenshot 2025-03-16 at 10.25.11 AM.png]]
1. sentence encoder converts both training and test set sources to vector representations
2. For ONLINE PREDICTION, test source can be converted on the fly!
3. For each test source x, k nearest neighbors are retrieved from training set
4. Given a pre-defined similarity measure (cosine) the neighbors are put in descending order of similarity.
5. k sources are concatenated with their targets (labels) to form the context which is sent to GPT3 along with the test input.
![[Screenshot 2025-03-16 at 10.46.43 AM.png]]

###### Experimental Setup
- KATE tested on sentiment classification, table to text generation, and QA.
	- Also compares the result of using KATE with pretrained transformed model fine-tuned to the specific task, vs model NOT fine-tuned.
- Two baselines:
	- Using random sampling for selecting in-context examples.
	- Using kNN: to "investigate whether the retrieval module is complementary to GPT3s few shot learning ability" simply use kNN to return the target associated with the first retrieved example (the one most similar to the test input)
###### Results Summary
- KATE works better when a pre-trained sentence encoder is fine-tuned on the specific dataset
- GPT3 model is critical to the final results, the retrieval module is complementary to GPT3 few-shot abilities
- KATE consistently outperforms kNN and random selection method even with few in-context examples.
- the retrieval module is helpful for both situations where the test set follows the distribution of the training set and where the test set is out of distribution of the training set
- As the size of training set for retrieval increases, the performance also increases.
![[Screenshot 2025-03-16 at 12.35.21 PM.png]]
- the order of in-context examples does not seem to have significant impact on KATEs performance (though this could be data dependent)



