Paper reading in Jan 31

### brief summary
The paper studied how LMs use the knowledge in itself and information in the context by studying their use on semantic priors and input-label mapping for ICL. They used flipped labels and semantically unrelated labels to study this. They also examine the effects of the scale of models and find that small models are more relied on the training data and ignores flipped labels, and big models can learn the new context better. They also find that instruction tuning help the model to learning mappings, they also reduce the model's adaptability and flexibility.  
### influential part
The most influential part might be that the scale of the model actually changes how the model works when meeting new contexts. This may indicate that larger models may 'learn' in a better way where in contrast smaller models seems to repeat or imitate to the priors. 
### improvements?
The scaling part seems to be a part of the paper, but is actually interesting. It would be nice if they check how big and small models deal with priors with a few experiments on which part of semantic priors big models succeed to override but small models don't might be interesting. It might be fun to check whether these priors are in the pretraining data of the large models and not covered by the smaller models.
### discussion?
