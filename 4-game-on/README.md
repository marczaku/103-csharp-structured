# Exercises 4 - Game On

## Game 2: Tic, Tac, Toe (BONUS)

### Goal
```
Output:Welcome to Tic-Tac-Toe!
Output: | | 
Output:-----
Output: | |
Output:-----
Output: | |
Output:In what column do you want to place your X (1-3)?
Input:2
Output:In what row do you want to place your X (1-3)?
Input:2
Output: | | 
Output:-----
Output: |X|
Output:-----
Output: | |
Output:In what column do you want to place your O (1-3)?
...
Output: |O|X
Output:-----
Output:O|X|X
Output:-----
Output:O| |X
Output:Player X wins.
```

### Instructions
- Create a Console Project named `TicTacToe`
- 2 Players
  - Player 1: `X`
  - Player 2: `O`
- 3x3 Grid (use a two-dimensional array)
- players take turns choosing an empty grid cell and putting their symbol into it
- player that has three of his symbols either
  - horizontally
  - vertically
  - diagonally
- wins and the game ends instantly.
- make an ASCII-Art Display of the grid 
- Bonus: implement an AI-Player