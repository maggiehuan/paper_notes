
Question: whether a skilled decision-maker plan more steps ahead. -> use model fitting to show that human behavior can be captured using heuristic search. 
- Validation: 
	- Predict human choices, response times, eye movements
	- Turing test
	- Reconstructed experiments (what is this?)
- Result:
	- Increased planning depth with expertise
	- Experts **memorize and reconstruct board features** more accurately

Human planning: goal-directed decision-making -> plan along multiple branches in a decision-tree -> eliminate unpromising branches by pruning.
- Human behavior consistent with planning several steps into the future.
- Human use prospective info to guide current choices, locate the representation of prospective info to cingulate and prefrontal cortices.
- Computation cognitive model for human decision-making
- Validate using choice response time and eye movement data
- Use the model to investigate nature of expertise in planning.

### Computational cognitive model
- using heuristic search
	- heuristic function: maps board state to value estimation -> weighted linear combination of board features. 
		- Value estimation: use BFS to iteratively expand nodes
- prune branches with low heuristic value
- add Gaussian noice and include feature dropout for modeling human selective attention
	- randomly ignores feature instances from heuristic function

### Model Validation
- 40 human played games against other human player. estimate:
	- model parameters using five-fold cross-validation
	- out-of-sample choices with 40% acc