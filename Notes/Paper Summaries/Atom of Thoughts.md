
KeyTerms:
- **train-time scaling**: improving a model’s performance by increasing resources (more data, larger models, longer training, more compute power) during training.
- **test-time scaling**: improves performance at inference time, without retraining the model. It includes techniques that help the model reason better when answering questions or solving tasks. eg: CoT, ToT, Self-Consistency, and now... AoT.
![[Screenshot 2025-03-21 at 1.56.05 PM.png]]
#### Introduction
- LLMs demonstrate significant scaling effects; predictable improvements as the model is scaled.
	- however, existing test-time scaling maintains excessive historical info during reasoning to generate every subsequent step.
		- *As the scale of reasoning increases, the accumulation of historical dependencies not only wastes substantial computational resources but also interferes with the model’s ability to reason effectively.*
- To solve a complex problem, identify and resolve self-evident subquestions first, then  incorporate these solutions to reformulate a simplified problem state, rather than keeping track of every intermediate reasoning step. 
	- Closely resembles a Markov process, where each state represents a question, and state transitions occur through resolving partial problems to form new, independent questions.
- Introducing: AoT
	- Inspired by markov nature of human reasoning.
	- **Key Insight**: each reasoning state can be defined as a simplified problem equivalent to the original one.
	- eliminates need for maintaining historical info when scaling compute resources.

#### Overview of AoT
1. Reasoning Chain: Each subquestion $Q_{i + 1}$  is only dependent on its immediate predecessor, achieving true Markov property.
2. Iterative decomposition-contraction cycle:
	1. AoT uses a temporary DAG structure; decomposing the current question into subquestions (nodes) and dependencies between subquestions (edges), to facilitate the subsequent contraction phase...
	2. Contraction: transforms the temporary DAG structure into the next atomic state while preserving the Markov property.
		1. ensures progress in the reasoning process while selectively discarding "resolved" information to maintain atomic states.
		2. *AoT addresses this by treating results from $Q_{ind}$ as either given conditions or eliminated process information, while contracting $Q_{dep}$ into an independent question as the next state.* 
	![[Screenshot 2025-03-21 at 1.12.59 PM.png]]

#### LLM Prompts
1. Direct Question Solver: "You are a precise math question solver... QUESTION: {question} ... freely reason in your response but enclose the final answer within "\<answer>" tags.
2. Dependency Annotation (Decomposition): For the original question: {OG Q}, we have broken it down into the following subquestions: {subquestions} and obtained a complete reasoning process for the original question: {response}. We define the dependency relationship between subquestions as: which info in the current subquestion description does not come directly from the original Q, but from the results of other sub Qs. You are a math question solver specializing in analyzing the dependency relationships between these subQs. Please return a JSON object that expresses a complete reasoning trajectory for the OGQ, including the description, answer, and dependency relationships of each subQ. The dependency relationships are represented by the indices of the dependent subquestions in subquestions, starting from zero.

#### Experiments/Results:
- 6 standard datasets: Math reasoning - **MATH** and **GSM8K**, knowledge-intensive reasoning - **MMLU-CF**, logical reasoning - MC subsets of **BBH**, and multi-hop reasoning - **HotpotQA** and **LongBench**.
- backbone model: gpt-4o-mini
- Baseline: CoT, CoT with self-consistency (CoT-SC), Self-Refine, Analogical Reasoning, agentic workflow (AFlow), Forest of Thought (FoT)
- Results: AoT crushes baselines ! ![[Screenshot 2025-03-21 at 1.23.51 PM.png]]
- Even more impressive... can beat deepseek R1 !!! ![[Screenshot 2025-03-21 at 1.25.44 PM.png]]
- **Test-Time Optimization Results**: AoT exhibits consistent accuracy improvements as the iteration depth increases (on MATH dataset), with diminishing returns. Suggests many problems can be effectively solved with fewer iterations.
- **Cost Analysis:** AoT demonstrates steepest performance-to-cost ratio among all compared methods
- **Ablation studies**: removed the decomposition phase, performance dropped. --> this structure is important ?



