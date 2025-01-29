ICL - perform a new task via inference along by conditioning on a new input-label pairs (demonstrations). 
- ground truth demonstrations are not required - randomly replacing labels in the demonstrations don't hurt performance
but they provide:
- the label space
- the distribution of the input text
- overall format of the sequence
which part of demonstrations do contribute to the performance
label space and distribution of the input text specified by the demonstrations are both key to ICL, the overall formate is also crucial. 

### brief summary
This paper investigated how ICL contributes to LLMs by studying different possibilities of potential influential factors. They find that the label space, the distribution of the input text and format matters while ground-truth of demonstrations actually plays little. 
### influential part
This paper provides deeper understanding and new potential perspectives on how model learns and how we can utilize it, as well as providing more specific answers on how ICL helps and how we can better use ICL. It is also very interesting how they discussed test-time learning as early as 2022 by understand more on whether or how much pre-training's data plays at test time, and how much we can potentially utilize test time learning (although at that time it seems like their vision is a bit limited by ICL? it is still interesting that they discussed it back then). Also conclusion is fun from intuition that it seems like ICL can help models narrow down to what kind of domain they should focus on and how they can "communicate" with human using provided format (a bit like the model needs human to provide a channel for output so that human can understand?), while they don't really need to be taught by "ground truth labels" anymore.
### do better?
For the conclusion for the main topic the paper wants to discuss, I think the paper answers the question pretty well with very heavy and nicely-designed experiments. I also enjoy the section "Does the number of correct labels matter?" by how this experiment that seems a bit out of my intuition actually provide stronger answer on why demonstration matters little.  I also like the OOD part too.
### discussion?
This conclusion is interesting given now we are scaling these test-time training "our findings suggest that LMs do not learn new tasks at test time. Our analysis shows that the model may ignore the task defined by the demonstrations and instead use prior from pretraining." and "Our experiments indicate that the model does make use of aspects of the demonstrations and achieve performance gains." Is this because ICL is a very primarily kind of test time learning so that it's not working in this paper? Curious how would they find out test time is potentially working at that time in this work, what kind of experiment might help here?