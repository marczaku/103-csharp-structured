# Exercises 4 - Game On

## The Real Nim Game

Implement Nim again. But this time using Three piles of variable Matches. You can randomize them, if you like, but you may for testing play with this composition:

```
O O O
| | | (Row 1)

O O O O
| | | | (Row 2)
    
O O O O O
| | | | | (Row 3)
```

The player can decide each turn, which Row he wants to draw from and how many matches he'd like to draw from it (at least 1, not more than three, but also not more than there are still left in the Row).

Next, it's the AI's turn.

Whoever draws the last match, leaving no matches behind, loses.

Things to consider:
- What game structure do you want to use for the Matches?
- Does it work well, if the number of Stacks changes?
- Can you make it so it's easy to change the game to have 10 stacks?
- What if the number of matches that the player can maximally draw changes?
- Can your game easily be changed?
- Does your AI still work well?

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