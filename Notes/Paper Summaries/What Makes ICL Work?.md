Paper: *Rethinking the Role of Demonstrations: What Makes In-Context Learning Work?*

#### Introduction
- In Context Learning (ICL): there is little understanding of how it works and which aspects of the demonstrations contribute to task performance.

Key Findings:
1. **Ground Truth Labels Are Not Essential**: Replacing ground truth labels in demonstrations with random labels minimally impacts performance across classification and multi-choice tasks.
2. **Key Aspects of Demonstrations**
	1. The label space and input text distribution specified by demonstrations are crucial for ICL, regardless of label correctness.
	2. Specifying the overall format (e.g., using random words as labels) is vital, especially when the label space is unknown. 
	3. Meta-training with an ICL objective amplifies these effects, as models prioritize simpler aspects like format over input-label mappings.

#### Method
- **Models**: 12 models, including GPT-3 (the largest one). k = 16 examples used for few-shot. Compares BOTH "direct" and "channel" inference... need to look into what this means.
- **Evaluation Data**: evaluated performance on NLP tasks like sentiment analysis, sentence completion, etc. All datasets are either classification or MC tasks.
- **Settings**:
	- No demos: zero-shot training
	- Demos with gold labels: correct (input, label) training pairs (x, y)
	- Demos with random labels: incorrect pairs (x, z) where z is random label.

#### Ground Truth Matters Little
- replacing gold labels with random labels only marginally hurts performance. Not even the % of correct labels seem to matter:
![[Screenshot 2025-03-13 at 2.32.32 PM.png]]
- Model performance is fairly insensitive to the number of correct labels in the demonstrations !!
- always using incorrect labels STILL outperforms no demos at all !!
- "there is particularly little performance drop in MetaICL, suggesting that meta-training with an explicit in-context learning objective encourages the model to ignore the input-output label mapping and exploit other components of the demonstrations".... what does this mean ?
- model performance does not increase much as k increases when k ≥8, both with gold labels and with random labels.
- The result is consistent with better templates (templates written manually in a dataset-specific manner) but "using manual templates does not always outperform using minimal templates."

#### Why does ICL Work?
Four potential factors:
1. **Input-label mapping**: is x mapped to its correct y?
2. **Distribution of the input text**: what is the underlying distribution that x1...xk is from?
	1. authors experiment with out-of-distribution (OOD) text instead of inputs from unlabeled training data. (Light Purple: OOD + Random labels)
	2. significantly drops the performance of some models in both classification and MC
	3. sometimes, even worse than no demos!
	4. *suggests that in-distribution inputs in the demonstrations substantially contribute to performance gains.*
3. **Label Space**: space of y1...yk
	1. experiment with demos with random english words as labels for all k pairs. (Turquoise: Random English words)
	2. *indicates that conditioning on the label space significantly contributes to performance gains.*
4. **Format**: specifically, the use of input-label pairing as the format.
	1. Authors evaluated the impact of **demos with no labels** where the model is conditioned on the concatenation of inputs, and **demos with labels only** where model conditioned on concatenation of labels.
	2. *result: keeping the format of the input-label pairs is key*
5. Impact of meta-training: MetaICl is trained with an in-context learning objective
	1. ... what does this mean?

ALL RESULTS SUMMED UP:
![[Screenshot 2025-03-13 at 3.04.47 PM.png]]

#### Discussion
1. **Does the Model Learn at Test Time?**: Under a strict definition of learning (capturing input-label correspondence), LMs do not learn new tasks at test time, as they rely on pretraining priors rather than task-specific demonstrations. However, under a broader definition (adapting to input/label distributions and formats), LMs do learn from demonstrations, leveraging aspects like input space and label space to improve performance.
2. **Capacity of LMs**: demonstrations help locate tasks, while task performance is rooted in pretraining. --> ICL may fail for tasks whose input-label mappings are not already captured in the LM.
3. **Connection to Instruction-Following Models**: Demonstrations and natural language instructions likely serve similar roles, prompting LMs to recover existing capacities rather than learn new task semantics. This is supported by evidence that irrelevant or misleading instructions minimally degrade performance.
4. **Improved Zero-Shot Performance**: Pairing unlabeled inputs with random labels achieves near k-shot performance, significantly raising the zero-shot baseline. Future work can further enhance zero-shot performance by relaxing assumptions about access to unlabeled data.