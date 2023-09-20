# Exercises 4 - Return and Output

## 4.1 Return Keyword

### Final Exercise

#### Goal
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

#### Instructions
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

### P04_1_1BuyGamePls
Write a function that asks the user to buy a game. If the user enters "Yes", the function says "Thank you" and `returns`. Otherwise, the function asks again.

### P04_1_2Countdown
Write the countdown exercise again, which recursively invokes itself. But instead of the function checking if the remaining timer is > 0 and if true, invoking itself, implement it the other way round: If the remaining timer is not > 0, have it `return`. Example:

Before:
```cs
if(health < 3){
   HealAgain();
}
```

After:
```cs
if(health == 3){
   return;
}
HealAgain();
```

### P04_1_3MakeTheMessageAppear
Look at the code sample below. Fix it by replacing the comment with code to make the magic message appear.

```cs
void MagicMessage(){
  Console.WriteLine("You're trying to find the magic message.");
  // Replace this comment with code.
  return;
  Magic:
  Console.WriteLine("You found the magic message.");
}
MagicMessage();
```

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

### P04_2_1Numbers
Write a function `Four` that returns the number `4` and a function `Five` that returns the number `5`. Invoke each function and assign their results to variables. Add both variables to a third variable. Print that variable to the console.

### P04_2_2UserInput
Write a function `GetUserMatches` that asks the user for how many matches he wants to draw. If the user enters a valid number (1, 2 or 3), it returns the users input as a number. Otherwise, it shows an error and asks again. Invoke that function and assign the result to a variable named `userMatches`. Print the value of the variable to the console.

### P04_2_3AIInput
Write a function `GetAIMatches` that asks the AI for how many matches it wants to draw. It returns a random valid number (1, 2 or 3). Invoke that function and assign the result to a variable named `aiMatches`. Print the value of the variable to the console.
