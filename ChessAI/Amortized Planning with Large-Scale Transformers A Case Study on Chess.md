This research explores the ability of large-scale transformers to learn complex planning algorithms through supervised learning. They trained transformers to predict the value of different actions on a chessboard using a massive dataset of chess games annotated with Stockfish 16 evaluations. Here is a step-by-step breakdown of their process:

1. **ChessBench Dataset Creation:**
    
    - The researchers compiled a vast dataset called **ChessBench** using 10 million chess games from Lichess.
    - They extracted all unique board states from these games and used **Stockfish 16, a powerful chess engine, to annotate each board state with a state-value (win probability) and action-values (win probabilities for each legal move).**
    - This resulted in a massive dataset with **15.3 billion action-value estimates, which took approximately 8864 days of unparallelized Stockfish evaluation time to generate.**
    - The dataset was split into training and test sets. The test set comprised games from a different month to ensure the model was tested on unseen data.
    - They also curated a separate test set of 10,000 challenging chess puzzles with known solutions.
2. **Data Preprocessing and Training:**
    
    - The researchers converted the continuous win probabilities (state and action values) into discrete classes via binning. This process divided the 0% to 100% win probability range into 128 bins, creating a classification problem.
    - They tokenized the board states using the standard FEN notation, a string representation of a chess position.
    - They employed a **decoder-only transformer architecture**, a powerful neural network architecture well-suited for sequence processing, to predict the bin containing the correct state or action value.
    - The largest transformer model they trained had **270 million parameters**.
    - They trained the models using the **HL-Gauss loss**, a classification loss function, and **Adam optimizer** through **mini-batch stochastic gradient descent**.
3. **Constructing Policies from Trained Predictors:**
    
    - The researchers used the trained transformers, which excelled at predicting action-values, to create **"searchless" chess-playing policies**. These policies relied solely on the quality of the value predictions without employing explicit search algorithms.
    - The policy would select the move with the highest predicted action-value, effectively making decisions based on a learned approximation of Stockfish's evaluation.
4. **Evaluation:**
    
    - The researchers evaluated their models using various metrics:
        - **Action Accuracy**: Measured the percentage of times the policy selected the same move as Stockfish.
        - **Action Ranking**: Assessed the correlation between the model's predicted move rankings and Stockfish's rankings.
        - **Puzzle Accuracy**: Determined the percentage of chess puzzles the policy could solve correctly.
        - **Elo Rating**: Gauged the playing strength of the policies by having them play against other chess engines, bots, and humans on Lichess.

By following this methodology, the researchers demonstrated that large-scale transformers could learn to play chess at a high level without any explicit search, solely by learning from a massive dataset of games annotated with expert evaluations. This work indicates the potential of large transformers in approximating complex algorithms through supervised learning.