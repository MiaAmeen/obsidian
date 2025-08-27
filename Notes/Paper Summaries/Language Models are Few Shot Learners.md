#### Introduction
- shift in NLP from using task-specific models to large, task-agnostic pre-trained models.
	- *However*, this still requires the final task-specific step of fine-tuning the task-agnostic model on a large dataset of examples

Is this final step necessary? Short answer: No.
- with in-context learning, a pre-trained model can perform NLP tasks without need for finetuning!
	- disadvantage: performance still far from supervised baselines
	- advantage: there is a log-linear trend of improved performance on transfer tasks and "language modeling loss" with scaling of the model.
	- authors test this with GPT-3 - 175bil parameter lang model. RQ: *how well can GPT-3 perform in NLP tasks with few/zero shot learning, with purely pretrained knowledge?*
###### Findings:
- GPT-3’s _few-shot_ performance is sometimes competitive with or even better than state-of-the-art models that have been fine-tuned for specific tasks.
- Scaling model capacity leads to smooth performance gains.
- performance improves significantly from zero-shot to one-shot and further in the few-shot setting. 
- GPT-3 effectively performs _meta-learning_, meaning it can rapidly adapt to new tasks by processing examples within its context, rather than through explicit weight updates.
- the gap between zero-shot, one-shot, and few-shot performance grows with larger models, suggesting that larger models are more effective at _in-context learning_ (learning from examples provided in the input rather than adjusting weights via fine-tuning).

#### Approach
we systematically explore different settings for learning within the context:
- **Fine-Tuning**: advantage: strong performance. disadvantages: need for a new large dataset per task, poor generalization, and overfitting.
- **Few-shot:** The model receives multiple examples. advantage: reduction in need for task-specific data. disadvantage: performance is still worse than SOTA fine-tuned models.
- **One-shot:** The model receives one example before performing the task.
- **Zero-shot:** The model is only given a natural language description of the task.
###### Model/Architecture:
- GPT-3 is same model/architecture as GPT-2.
- Trained 8 different sizes of model, from 125M parameters to 175B parameters, with the last being GPT-3. 
	- (for the purpose of testing the scaling laws)
###### Training Dataset
- **filtered CommonCrawl** - "an open repository of web crawl data", selecting content similar to high-quality reference corpora. 
- **Fuzzy Deduplication:** removed duplicate documents within and across datasets
- **Augmented with High-Quality Corpora:** incorporated additional high-quality datasets

#### Results


#### Limitations
- **Poor text synthesis**: repetitive, contradicting, and containing non-sequitor sentences
- "**Unidirectional Architecture**": it generates text from left to right, limiting its performance on tasks that require looking both forward and backward, such as fill in the blanks, etc
- **Equal Token Weighting**: treats all tokens equally, prioritizing some entities may be more optimal
- **Poor Real World Understanding**: trained only on text, lacks grounded reasoning
- **Large size**: difficult to deploy


