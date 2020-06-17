# Surrounded Regions
Given a 2D board containing 'X' and 'O' (the letter O), capture all regions surrounded by 'X'.

A region is captured by flipping all 'O's into 'X's in that surrounded region.

## Example:
```
X X X X
X O O X
X X O X
X O X X
```
After running your function, the board should be:
```
X X X X
X X X X
X X X X
X O X X
```
## Explanation:

Surrounded regions shouldn’t be on the border, which means that any 'O' on the border of the board are not flipped to 'X'. Any 'O' that is not on the border and it is not connected to an 'O' on the border will be flipped to 'X'. Two cells are connected if they are adjacent cells connected horizontally or vertically.

## Code 
```
class Solution {
    public void solve(char[][] board) {
        if (board == null || board.length <= 2 || 
            board[0] == null || board[0].length <= 2) {
            return;
        }
        
        int rows = board.length;
        int cols = board[0].length;
        for (int i = 0; i < rows; i++) {
            if (board[i][0] == 'O') {
                infect(board, i, 0, rows, cols);
            }
            if (board[i][cols - 1] == 'O') {
                infect(board, i, cols - 1, rows, cols);
            }
        }
        for (int j = 0; j < cols; j++) {
            if (board[0][j] == 'O') {
                infect(board, 0, j, rows, cols);
            }
            if (board[rows - 1][j] == 'O') {
                infect(board, rows - 1, j, rows, cols);
            }
        }
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (board[i][j] == '*') {
                    board[i][j] = 'O';
                } else if (board[i][j] == 'O') {
                    board[i][j] = 'X';
                }
            }
        }
    }
    private void infect(char[][] board, int i, int j, int rows, int cols) {
        if (i < 0 || i >= rows || j < 0 || j >= cols || board[i][j] != 'O') {
            return;
        }
        board[i][j] = '*'; 
        infect(board, i + 1, j, rows, cols);
        infect(board, i - 1, j, rows, cols);
        infect(board, i, j + 1, rows, cols);
        infect(board, i, j - 1, rows, cols);
    }
}
```
