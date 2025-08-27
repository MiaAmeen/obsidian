Pruning
- Unstructured: change weight values to 0
- Structured: Remove channels/neurons themselves

Dropout
- Applied probabilistically/temporarily removes units during training to prevent overfitting
- These units come back in the inference stage - nothing is "zeroed out"

These are both regularization techniques, but totally independent. 

Knowledge Distillation...?

Soft vs Hard labels: Probabilities vs binary assignments
Training vs Inference Cost: 
- May be better to save inference cost, because training is only a one time thing

Fairness
- Researchers found that a pruned network was more likely to misclassify minority class samples in an imbalanced dataset. This is unfair!
	- Data augmentation may be a good cure

Measuring "Consumption"
- Width/depth of the network ? Number of operations during training?


