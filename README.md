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