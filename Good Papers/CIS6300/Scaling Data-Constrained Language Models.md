### brief summary
This paper investigated several methods for scaling LMs in data-constrained regimes by quantifying the impact of data repetition and compute. They also find after 4 epochs, the performance will increase much slower. The repetition of using the data somehow also change the need for compute. They also proposed data augmentation that can mitigate the problem of data scarcity.
### influential part
The conclusion of repeating data can decrease the need for compute is very interesting. And may match the viewpoint that we don't actually need so much computation for LLMs these days given the result of Deepseek R1 Zero. They provide the result that training with 4 epochs is very helpful so that we don't need to train more epochs. With providing the relationship with adding repetition and 
### improvements?
The problem and perspective they proposed are very interesting and nice, especially investigating data repetition and compute, also how data repetition change the need for compute. I think the method they proposed which use data augmentation make sense too. It might be interesting if the method they propose better fit the conclusion they have. Augmenting data or remove filters doesn't seems very novel given that they already have a new perspective and some results.  
### discussion?
The perspective of "how data repetition may influence training in large models" is interesting. Are there any better ways to re-use this repetitions in training that can help boost performance? During the training process, some part of the data should be already learnt by models and adding them for training again may not be useful (from intuition). Curious whether this can help the problem of data scarcity.

