# Exercises 4 - Return and Output

## 4.1 Return Keyword

### Goal
```
Output:What's your name?
Input:Marc
Output:How old are you?
Input:18
Output:Do you want to enter?
Input:Yes
Output:Do you want to turn back?
Input:No
Output:Congratulations, you made it in.
```

### Instructions
- Create a Console Project named `P04_1Return` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Create a function called `MyFunction`
  - Return Type `void`
  - No parameters
  - When called
    - Ask the user for his name. Only continue, if his name is not `"Neo"`.
    - Ask the user for his age. Only continue, if it is >=18.
    - Ask the user if he wants to enter. Only continue, if he says `"Yes"`
    - Ask the user if he wants to turn back. Only continue, if he says `"No"`
    - Say `"Congratulations, you made it in."`
- Make sure to call the function `MyFunction`
- Remember to use the `return` Keyword.


Need Help? [Here's The Slides!](slides/README.md#4-return-keyword)

## 4.2 Return Value

### Goal
```
Output:Pick Rock, Paper or Scissors.
Input:Spock.
Output:That's not a valid input.
Input:Rock
Output:I pick... Scissors.
Output:You win!
Output:Pick Rock, Paper or Scissors.
[...]
```

### Instructions
- Create a Console Project named `P04_2ReturnValue` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Implement a Rock-Paper-Scissors Mini-Game.
- Write one function that returns the Player's Choice
  - but only, after the player has made a valid choice
- Write one function that returns the AI's choice
- Use those functions in your Core Game Loop
