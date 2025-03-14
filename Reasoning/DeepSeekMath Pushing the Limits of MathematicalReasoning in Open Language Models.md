
Paper Link https://arxiv.org/pdf/2402.03300 
Interesting notes:
""
DeepSeekMath-Base is initialized with DeepSeek-Coder-Base-v1.5 7B (Guo et al., 2024), as we notice that starting from a code training model is a better choice compared to a general LLM. Furthermore, we observe the math training also improves model capability on MMLU (Hendrycks et al., 2020) and BBH benchmarks (Suzgun et al., 2022), indicating it does not only enhance the model’s mathematical abilities but also amplifies general reasoning capabilities.
""
![[Pasted image 20250314134045.png]]

This figure is also interesting:
![[Pasted image 20250314134639.png]]

math training will actually decrease the ability for code generation. Aligns with our observation. 
![[Pasted image 20250314135020.png]]
Why is data training on Math improve MMLU? What is exactly "general training here"? Is it fair to constrains data to similar training tokens? Or what are we generally looking for here?


Can we do something similar, like mixed ratio training improves general reasoning ability like the last one? Seems like a easier one.