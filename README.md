```python
def is_puzzle_complete(board: chess.Board, moves: list) -> bool:
    """ 
    Function that given a fen an a list of moves checks 
    if the chess puzzle is complete
    args:
        board (chess.Board)
        moves (list)
    returns:
        bool  
    """
    for move in moves:
        if move in board.legal_moves:
            board.push(move)
        else:
            return {
                "board": board.fen(),
                "completed": board.is_checkmate(),
                "msg": f"""Illegal move {move}"""
            }

    return {
        "board": board.fen(),
        "completed": board.is_checkmate()
    }
```


```python
# training dataset builder

# train_df_one, test_df_one = train_test_split(
#     df_one, test_size=0.9999, random_state=42)

# train_df_one = train_df_one.reset_index(drop=True)
# test_df_one = test_df_one.reset_index(drop=True)

# print(len(train_df_one))

# training function row for training purposes
# def process_training_row(row):
#     board = chess.Board(row['FEN'])
#     move = chess.Move.from_uci(row['Moves'].split()[0])
#     board.push(move)

#     valid_moves = list(board.legal_moves)

#     return np.array([
#         {
#             "role": "user",
#             "content": json.dumps({
#                 "fen": board.fen(),
#                 "valid_moves": [move.uci() for move in valid_moves]
#             })
#         }, {
#             "role": "assistant",
#             "content": json.dumps({
#                 "move": row['Moves'].split()[1]
#             })
#         }
#     ])

```
as
d
asdadasda