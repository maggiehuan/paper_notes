### Thoughts:
##### brief summary
This paper looks into the problem of dealing with low data problem by comparing between using prompts and head-based SFT in equal setting to check how prompt can be helpful. They found that quantitively worth 100s of data points on classification tasks and proofed with a bunch of tasks to . 
##### influential part
It is very critical to know quantitively or scientifically how prompts can help LLMs' performance and how each kind of prompts can help since everyone 'feels' that prompt is injecting information but don't know exactly how. 
##### do better?
I'm actually a bit confused why they used head-only finetuning. If we use more advanced SFT methods would the conclusion be that prompting is only help LMs to identify and focus on one domain (or the context) so that they don't need to search all over it's parameters? 
##### discussion?
I am also interested in how AI generated prompts would work differently than human written prompts. If they can work well then is it make sense to prompt a model to prompt a model? Like using a small LM to prompt a big one, and if the human given prompt can be a fixed one, then the systems seems more "automatic" with very little cost (running small models might be much cheaper than human)



### Summarization
This paper investigates the benefits of using prompts when fine-tuning pre-trained models for classification tasks. The authors compare the performance of models that use task-specific prompts with those that use a generic classifier head, in a variety of tasks and data sizes. They aims to quantify the advantage of using prompts in terms of how much additional training data would be needed to achieve comparable performance without prompts.


- **Prompting vs. Head-based Fine-tuning:** The paper explores two approaches to adapting pre-trained models for classification:
    - Head-based fine-tuning uses a generic classifier head layer.
    - Prompt-based fine-tuning uses task-specific prompts to encourage the model to produce textual outputs corresponding to a given class.
- **Task-specific Prompts:** The use of custom prompts for each task is a key element of the prompt-based method. Prompts are composed of a pattern and a verbalizer. The pattern turns the input text into a cloze task, with a masked token to be filled, and the verbalizer maps the masked word prediction to a class.
- **Quantifying the Benefit of Prompts:** The paper introduces a metric, the average data advantage, to quantify the impact of a prompt in practice. It determines how many additional data points a head-based model would need to achieve the same performance as a prompted model.
- **Experimental Setup:** The experiments use the roberta-large pre-trained model and evaluate performance on the SuperGLUE and MNLI datasets. The evaluation includes a variety of tasks such as entailment, multiple-choice question answering, and common-sense reasoning. The models were compared across a range of available data, starting with 10 data points and increasing exponentially.
- **Key Findings:**
    - Prompting generally offers a substantial advantage over head-based fine-tuning across most tasks.
    - The advantage of using prompts can be quantified in terms of data points, varying depending on the task. For instance, the paper finds that using a prompt is worth approximately 3500 data points on MNLI, 280 on RTE and 750 on BoolQ.
    - Prompting is mostly robust to pattern choice.
    - Prompts can still be beneficial even when the verbalizer does not provide semantic information.
    - The choice of prompt is not as significant as the variance across random training runs.
- **Null Verbalizer Analysis:** The researchers investigated the importance of the verbalizer by replacing it with a non-sensical mapping. This shows that while verbalizers contribute to the benefits of prompting, the pattern itself still provides an inductive bias.
- **Reporting Method:** The study used the accumulated maximum performance across runs for every model. The authors also note that using the mean performance instead of the maximum can lead to significant variance in results.
- **Data Efficiency:** The main benefit of using prompts is data efficiency, which could be particularly helpful in low-resource language applications. However, there is a risk of introducing human biases or repeating biases already present in the language model.
