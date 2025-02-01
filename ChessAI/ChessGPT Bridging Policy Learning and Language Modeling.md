**Overview**

- ChessGPT is a GPT model designed to bridge policy learning and language modeling by integrating data from chess games and language related to chess.
- The model uses a large-scale dataset of chess games and language.
- The goal is to advance exploration of the interplay between natural language understanding and policy learning, acknowledging that human decision-making involves both historical policy interaction and strategic considerations in natural language.
- The research provides a comprehensive pipeline that includes data, models (ChessCLIP and ChessGPT), and an evaluation framework.
- The work also aims to create models that can serve as effective chess AI assistants for humans.

**ChessGPT Dataset**

- The dataset includes game data from online chess databases, recording human and chess engine replays.
- It also includes language datasets that contain chess knowledge in a natural language format.
- A mixed game-language dataset provides interrelated data, including articles, discussions, or commentaries on specific chess game replays.
- The dataset is organized into four categories: game, language, mixed, and conversation datasets.
    - Game Datasets include modeling computer game, pro game online game and puzzle.
    - Language Datasets include Blog, Forum, Wiki, General Text and Book.
    - Mixed Datasets include YouTube Video Annotated Game.
    - Conversation Datasets include instruction-tuning and Reddit conversation.
- The dataset includes a synthetic chess modeling dataset created using the python-chess library. This dataset addresses the challenge that chess rule descriptions are usually conveyed in natural language, which requires a large volume of model data for accurate comprehension by machine learning models.
- The dataset also includes 245K annotated games with 1.3M board-language pairs.
- YouTube video transcripts with synchronized chessboard states (in FEN) are also used.
- Instruction-tuning and conversation datasets are included to enhance instruction-following and dialogue capabilities.

**ChessGPT Models**

- Two models are introduced: ChessCLIP and ChessGPT.
    - **ChessCLIP** is trained to bridge the modality of policy and language using contrastive learning on paired game trajectories and annotations. It can perform PGN/text retrieval and generate actions based on text descriptions by maximizing similarity.
    - **ChessGPT** is a GPT-like model trained using causal language modeling on chess data. It treats chess as a text game, allowing imitation learning for policy learning by predicting the next move from the game dataset. The model is fine-tuned in two stages, base-model fine-tuning using chess corpus and supervised fine-tuning using question/conversation data to create ChessGPT-Base and ChessGPT-Chat respectively.

**ChessGPT Evaluation**

- The models' abilities are evaluated across three dimensions: **modeling ability**, **value judgement**, and **policy ability**.
    - **Modeling ability** measures the proficiency in tracking game state. This includes tasks like state tracking in chess using UCI notation, and converting between PGN/UCI notations and FEN.
    - **Value judgement** measures the capacity for value assessment and chess knowledge. This is evaluated through state value multi-choice tasks, chess annotation multi-choice tasks, and opening multi-choice tasks.
    - **Policy ability** measures the capability in decision-making and generating optimal moves. This includes checkmate-in-one tasks and general policy tasks, assessing the model’s ability to generate the best move in a given position based on Elo rating.
- ChessGPT models outperform other LLM baselines in all evaluation tasks.
- The evaluation confirms that ChessGPT models are more effectively aligned with both the true value function and human judgement/knowledge.
- ChessGPT-Base and ChessGPT-Chat show great checkmate ability.
- ChessGPT has limitations with adapting to different Elo ratings, possibly due to the model's limited understanding of the nuances of different playing styles.
- Qualitative results show that ChessGPT-Chat gives more factual answers and demonstrates better performance when prompted to generate analysis and perform other chess-related tasks.
- ChessCLIP shows a surprising level of proficiency in the annotation and opening tasks, indicating its ability to extract human judgment and knowledge from annotations.

**Other Key Information**

- The models are trained on a large scale dataset created for this study, which is available for public use.
- Chess engines today achieve superhuman-level performance by utilizing human knowledge.
- There has been an increasing interest in improving the interpretability of chess systems and their alignment with human behavior.
- Chess rules are conveyed in natural language, which poses a challenge for machine learning models because they statistically require a large volume of data to understand the rules accurately.
- The training of ChessGPT includes both base-model fine-tuning and supervised fine-tuning.
- The ChessCLIP model has the ability to generate move sequences using beam search, a feature not available in the original CLIP model due to the high dimensionality of image and text spaces.
- The researchers used 8 x 80G A100 GPUs for training.
- The models are open sourced for public use.
