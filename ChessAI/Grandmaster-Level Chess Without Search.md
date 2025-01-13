This paper investigates if **training a transformer model at scale, using supervised learning on a massive chess dataset, can result in a strong chess-playing policy without explicit search**. The researchers focused on distilling the knowledge of Stockfish 16, a powerful search-based chess engine, into a feed-forward neural network.

Here's a detailed explanation of their approach:

**1. ChessBench Dataset Creation**

- The researchers created a dataset, referred to as **"ChessBench,"** consisting of **10 million chess games downloaded from Lichess**.
- From these games, they **extracted all unique board states** and discarded duplicates, resulting in a diverse set of positions.
- Crucially, they **annotated each board state with action-values (win percentages for all legal moves) using Stockfish 16 as an oracle**.
    - Stockfish 16 was allotted a **time limit of 50ms per move** for evaluation, achieving an estimated Lichess blitz Elo of 2713.
    - This resulted in **15.32 billion action-value estimates** for the training dataset.
- **For testing, they used games from a different month (1,000 games) and a separate set of 10,000 challenging Lichess chess puzzles** with known solutions. This ensured the model was evaluated on unseen data.

**2. Data Preprocessing and Tokenization**

- The **win percentages (action-values) were converted into discrete classes (bins) to frame the problem as classification rather than regression**. This involved dividing the 0% to 100% win percentage range uniformly into 128 bins.
- **Board states were tokenized using the standard FEN notation**, a 77-character string representation of a chess position. Each character in the FEN string was treated as a separate token.
- **Actions were represented using UCI notation** (e.g., "e2e4"). The researchers determined all possible legal actions (1968) and assigned a unique index to each, using this index as the token for each action.

**3. Model Architecture and Training**

- The researchers chose a **decoder-only transformer architecture**, a powerful neural network design commonly used in language modeling, with roughly **270 million parameters** for their largest model.
- The model was trained to **predict the bin index corresponding to the Stockfish-estimated action-value** for a given board state and action.
- **They minimized cross-entropy loss (log loss) using the Adam optimizer and mini-batch stochastic gradient descent**.
- The model was trained for **10 million steps** with a batch size of 4096, which translates to approximately **2.67 epochs** for the largest training set.

**4. Policy Construction and Evaluation**

- **The trained transformer model was used to construct a "searchless" chess policy**. Given a board state, **the policy simply selected the action with the highest predicted action-value**.
- To assess the policy's performance, they utilized the following metrics:
    - **Action Accuracy:** The percentage of times the policy chose the same move as Stockfish 16.
    - **Action Ranking (Kendall's τ):** A statistical measure that quantifies the correlation between the model's predicted action ranking and Stockfish's ranking.
    - **Puzzle Accuracy:** The percentage of chess puzzles the policy solved correctly by playing out the correct sequence of moves.
    - **Elo Rating:** The model's playing strength was evaluated on Lichess by playing blitz games against both human players and bots.

**Key Findings:**

- **The largest model achieved a Lichess Blitz Elo of 2895 against human players, demonstrating grandmaster-level performance.**
- It also performed well on the puzzle test set, showcasing its ability to reason strategically without explicit search.
- The researchers observed that **increasing both the model size and dataset size consistently led to improved performance**.

This research offers compelling evidence that **sophisticated, search-based algorithms like those used in Stockfish can be effectively approximated by large transformer models trained through supervised learning**. By leveraging the vast amount of data in ChessBench and the power of transformer architectures, this "searchless" approach presents a promising alternative to traditional chess engines.


这篇论文研究了**在大规模国际象棋数据集上使用监督学习训练 Transformer 模型，能否在没有显式搜索的情况下实现高水平的国际象棋博弈策略**。研究人员的重点在于将 Stockfish 16（一款强大的基于搜索的国际象棋引擎）所蕴含的知识，提炼并转移到一个前馈神经网络中。

以下是他们具体的研究方法：

**1. ChessBench 数据集的构建**
• 研究人员构建了一个名为 **ChessBench** 的数据集，其中包含了 **从 Lichess 下载的 1000 万局国际象棋对局**。
• 他们从这些对局中**提取了所有独一无二的棋盘状态**并剔除重复项，从而得到一个多样化的棋局集合。
• 核心步骤是：他们利用 **Stockfish 16 作为“先知”**（oracle），为每个棋盘状态添加了**动作价值**（即所有合法走法的赢面百分比）。
• 在对每一步走法进行评估时，Stockfish 16 有 **每步 50 毫秒**的思考时间，其预估 Lichess blitz（快棋）Elo 水平约为 2713。
• 最终，数据集中共获得 **153.2 亿** 个动作价值估计。
• **在测试阶段**，研究人员选取了一个**不同月份**的 1000 局对局，以及一组**1 万个具有已知解答的 Lichess 高难度国际象棋习题**，用于评估模型在未见过的数据上的表现。

**2. 数据预处理与分词**
• 为了将问题视为分类任务而非回归任务，研究人员**将赢面百分比（动作价值）进行离散化**，把从 0% 到 100% 的赢面范围均匀地分为 128 个区间。
• **棋盘状态使用标准的 FEN 表示法进行标记（tokenize）**。FEN 以 77 个字符来描述棋盘，每个字符分别视为一个 token。
• **走法（action）则采用 UCI 格式**（如 “e2e4”）。研究人员枚举出所有可能的合法走法（共 1968 个），并为每个走法分配一个唯一的索引号，将其用作相应的 token。

**3. 模型架构与训练**
• 研究人员选用的是**仅包含解码器部分（decoder-only）的 Transformer 架构**——这是一种常用于语言建模的强大神经网络设计，在最大规模的模型中约有 **2.7 亿个参数**。
• 模型的训练目标是**预测某个棋盘状态与走法对应的 Stockfish 评估动作价值所处的区间（bin）**。
• **他们采用 Adam 优化器和小批量随机梯度下降（mini-batch SGD）来最小化交叉熵损失（log loss）**。
• 模型总共训练了 **1000 万个步骤**，批大小为 4096，相当于在最大数据集上完成了约 **2.67 个 epoch**。

**4. 策略构建与评估**
• **训练完成的 Transformer 模型被用来构建一个“无搜索”（searchless）的国际象棋策略**。在给定的棋盘状态下，**策略会直接选取模型预测中动作价值最高的落子**。
• 为了评估该策略的表现，研究人员采用了如下指标：
• **动作准确率（Action Accuracy）**：策略与 Stockfish 16 选择同一个走法的比例。
• **动作排序相关（Action Ranking, Kendall’s τ）**：衡量模型对走法排序与 Stockfish 排序之间的相关性。
• **习题准确率（Puzzle Accuracy）**：在那组国际象棋习题测试集中，策略能正确解出的比例（通过实际走出正确解法序列）。
• **Elo 等级分（Elo Rating）**：在 Lichess 上，与人类玩家和机器人进行快棋对弈来评估模型的对弈水平。

**主要发现**
• **最大规模的模型在与人类玩家的 Lichess Blitz 对弈中达到了 2895 的 Elo，展现出特级大师水平的实力。**
• 它在国际象棋习题测试集中也表现优秀，展示了**无需显式搜索**就能进行战略推理的能力。
• 研究人员注意到，**增大模型规模和数据规模都会带来性能的持续提升**。

总体而言，这项研究提供了有力的证据表明，**类似 Stockfish 这样基于复杂搜索算法的国际象棋引擎，其知识与能力能够通过监督学习，被大型 Transformer 模型有效地近似**。借助庞大的 ChessBench 数据集和 Transformer 架构的强大能力，这种“无搜索”方法为传统的国际象棋引擎提供了一种颇具前景的替代方案。