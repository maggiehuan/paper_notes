### brief summary
This paper investigated several methods for scaling LMs in data-constrained regimes by quantifying the impact of data repetition and compute. They also find after 4 epochs, the performance will increase much slower. The repetition of using the data somehow also change the need for compute. They mixed code data as a way to augment data and find that the mixing result in twice increase in effective tokens. They also found that data filtering is effective for noisy datasets.
### influential part
The conclusion of repeating data can decrease the need for compute is very interesting. And may match the viewpoint that we don't actually need so much computation for LLMs these days given the result of Deepseek R1 Zero. They also provide the result that training with 4 epochs is very helpful so that we don't need to train more epochs. The result of mixing code data can also benefit natural language task is inspiring, can using more structured and logical data help too? 
### improvements?
The problem and perspective they proposed are very interesting and nice, especially investigating data repetition and compute, also how data repetition change the need for compute. I think the method they proposed which studied the mix of code data in natural language data increased effective tokens is novel. It might be interesting if the method they propose better fit the conclusion they have. Overall, I think the ideas in the paper are very interesting, but how they are arranged in the paper seems a bit loose? Or maybe I did not get the main philosophy yet.
### discussion?
The perspective of "how data repetition may influence training in large models" is interesting. Are there any better ways to re-use this repetitions in training that can help boost performance? During the training process, some part of the data should be already learnt by models and adding them for training again may not be useful (from intuition). Curious whether this can help the problem of data scarcity.

function fitness?? compute residuals, 
repeating data
complex functional bla? test laws? at loss

function form
scaling data vs delibrated/well-selected data??