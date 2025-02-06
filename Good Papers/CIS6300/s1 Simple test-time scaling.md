### Methods
Main Takeaway here


This paper introduces a simple method for achieving test-time scaling and strong reasoning performance in language models. The approach involves curating a small dataset of 1,000 questions with reasoning traces, and using budget forcing to control test-time compute.

**Key Concepts and Methods:**

- **Test-time scaling:** This refers to the idea of increasing compute during the testing phase to improve model performance.
- **s1K dataset:** A dataset of 1,000 questions paired with reasoning traces that are carefully selected for difficulty, diversity, and quality. The questions come from diverse sources, including math problems, Olympiad questions, and brain teasers. The dataset is created by first collecting 59,000 questions and then filtering down based on quality, difficulty and diversity.
    - **Quality**: The dataset is filtered to remove questions with API errors or formatting issues.
    - **Difficulty**: Questions that can be easily solved by smaller models are removed.
    - **Diversity**: The questions are classified into different domains using the Mathematics Subject Classification (MSC) system, and the final 1,000 samples are chosen to span 50 different domains.
- **Budget forcing:** This is a technique to control the amount of compute time a model spends on a problem. It works by:
    - **Forcing an end:** If the model generates more tokens than a desired limit, the thinking process is ended by appending an end-of-thinking token.
    - **Encouraging more exploration**: If more test-time compute is desired, the generation of the end-of-thinking token is suppressed and "Wait" is appended to the model's reasoning to encourage more exploration.
- **s1-32B Model:** The Qwen2.5-32B-Instruct language model is fine-tuned on the s1K dataset using supervised fine-tuning (SFT). This model, equipped with budget forcing, exhibits test-time scaling, meaning it improves with more compute during testing.

**Key Findings and Results:**

- **Superior Performance:** The s1-32B model exceeds the performance of OpenAI's o1-preview on competition math questions by up to 27% (MATH and AIME24).
- **Extrapolation:** Scaling s1-32B with budget forcing allows it to extrapolate beyond its training performance without intervention during test-time (for example, from 50% to 57% on AIME24).
- **Sample Efficiency:** The s1-32B model is very sample-efficient, achieving strong reasoning performance despite being trained on only 1,000 samples. This highlights the importance of careful data selection, and echoes findings for instruction tuning.
- **Importance of Data Curation:** The paper demonstrates that the combination of quality, diversity, and difficulty is crucial for creating an effective dataset.
- **Budget Forcing Effectiveness:** Budget forcing leads to the best scaling with perfect controllability and a clear positive slope, which leads to strong performance.
- **Sequential Scaling:** The paper focuses on sequential scaling, where later computations build on earlier ones, and shows that it is more effective than parallel scaling methods such as majority voting.
- **Comparison with other Models:** The s1-32B model is benchmarked against other models, including OpenAI's o1 series, DeepSeek's r1 series, and Qwen's QwQ-32B-preview. The s1-32B model performs competitively and is the most sample-efficient open data reasoning model.
- **Limitations:** The paper acknowledges limitations in further test-time scaling, such as the flattening of performance and the constraint imposed by the context window.
- **Metrics for Test-Time Scaling:** The paper defines metrics such as Control, Scaling, and Performance to evaluate test-time scaling methods.

**Ablation Studies:**

The paper includes ablation studies to investigate the impact of different aspects of their method. These studies include:

- **Data Ablations:** The paper tests the importance of quality, diversity, and difficulty when curating the dataset. The results show that combining these three criteria is key for sample-efficient reasoning training.
- **Test-time Scaling Method Ablations**: The paper examines the effectiveness of different test-time scaling approaches, such as token-conditional control, step-conditional control and class-conditional control, in comparison with budget forcing. Budget forcing is shown to be more effective because of its ability to control the thinking time. The paper also shows that rejection sampling leads to an inverse scaling trend.

**Additional Points:**

- The code, model, and data are open source.
- The paper discusses related work in sample-efficient reasoning, test-time scaling methods and benchmarks.
- The paper explores limitations of sequential scaling and ways that parallel scaling can be used to further improve performance.
- The paper includes a discussion of the impact of the work, acknowledging the potential for language models to enhance human productivity.

In summary, this paper presents a straightforward approach to achieve test-time scaling and strong reasoning performance using a small, carefully curated dataset and a simple technique called budget forcing. The findings highlight the importance of data selection and provide a valuable contribution to the field of language model reasoning.