# 8-queens
this is the code of 8 queens which can be placed in  any place in a 8*8 box but they cant meet in a row or column or diagonal
def isSafe(board, row, col):
    # Check this row on the left side
    for i in range(col):
        if board[row][i] == 1:
            return False

    # Check upper diagonal on the left side
    for i, j in zip(range(row, -1, -1), range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    # Check lower diagonal on the left side
    for i, j in zip(range(row, len(board)), range(col, -1, -1)):
        if board[i][j] == 1:
            return False

    return True


def solveNQueens(board, col):
    if col >= len(board):
        return True

    for i in range(len(board)):
        if isSafe(board, i, col):
            board[i][col] = 1
            if solveNQueens(board, col + 1):
                return True
            board[i][col] = 0  # Backtrack

    return False


def printBoard(board):
    for i in range(len(board)):
        for j in range(len(board)):
            print(board[i][j], end=" ")
        print()
    print()


def solveQueens(N):
    board = [[0] * N for _ in range(N)]
    if not solveNQueens(board, 0):
        print("Solution does not exist")
        return False

    printBoard(board)
    return True


# Change N here
N = 8
solveQueens(N)

print("Arthi L S")
