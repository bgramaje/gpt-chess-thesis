* PROMPT

```python
    context = np.array([])

    # for training-dataset purposes
    for index, row in train_df_one.iterrows():
        # few shot learning
        if (index == 2):
            break
        context = np.append(context, process_training_row(row))

    messages = np.array([
        {
            "role": "system",
            "content": f"""You are a chess engine that solves chess puzzles. \n
                    Your objective is to do mate in one in the puzzle I provide you. \n         
                    The prompt input structure will be something like this delimited by the three backticks: \n

                    ```
                    "fen": <fen>
                    "valid_moves" : <valid_moves>
                    "history": <history>
                    ```

                    "<fen>" stands for chess board position in 'FEN (Forsyth–Edwards Notation)' format.\n
                    "<valid_moves>" stands for all legal moves available for that FEN board in UCI (Universal \Chess Interface) format.\n
                    "<history>" stands for all the moves that has been played in that puzzle in UCI (Universal \Chess Interface) format.\n
                                        
                    Your task is to pick a move from the "valid_moves" list above that maximizes your chance of doing checkmate
                    
                    Output the best move in UCI format (The format should be the source and destination square, e.g. {{"move": 'e2e4'}} to move \n
                    the pawn from e2 to e4. Analyze the position and return the best possible move to checkmate. 
                    Use the following single blob of JSON. Do not include any other information and remove any blank space you include.
                
                    ```
                    "{{"move": "<move>"}}"
                    ```
                """.replace('\n', ' ').replace('\r', '').replace('"', '\\"'),
        },
    ])

    context = np.append(messages, context)
    print(context)
````