This paper presents LLM.int8(), a new method for Int8 matrix multiplication specifically designed for transformer models. It significantly lowers memory usage during inference while keeping full precision performance. The main idea is to quantize the feed-forward and attention projection layers to 8-bit, which reduces memory needs by half. LLM.int8() also solves challenges related to quantization precision in large-scale models and directly handles the problem of outlier features that appear in transformer layers.

The most influential part might be showing how to apply 8-bit arithmetic to large-scale transformers. Which seems to become more and more important today when we try to squeeze more performance on limited computations. The paper is very technical solid and neat. I like these kind of very technical papers a lot. But also have to admit that it is way more harder to understand than an application type of paper (or maybe i'm not familiar with some basic concepts?)

I think I'm still confused about the phrase transition part. Would be nice if we can discuss a bit more on this.

