# Exercises 1 - Functions

## Goal
Learn about scopes and functions. See, how we can use functions to pack code into reusable and parameterized blocks.

## 1 - Scopes: 

### Goal
```
Output:Give me a number.
Input:9
Output:91
Output:Give me another number.
Input:9
Output:10
Output:Give me another number.
Input:9
Output::
```

### Instructions
- Create a Console Project named `P1Scopes` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Ask the user for a number and assign the result to a variable of type `string` named `input`.
- Add 1 to `input`.
- Print `input` to the Console.
- Ask the user for another number and assign the result to a variable of type `int` named `input`.
- Add 1 to `input`.
- Print `input` to the Console.
- Ask the user for another number and assign the result to a variable of type `char` named `input`.
- Add 1 to `input`. (Use `++`)
- Print `input` to the Console.

Need Help? [Here's The Slides!](slides/README.md#1-scopes)

## 2 Bare Functions

### Goal
```
Output:Move Forward.
Output:Move Forward.
Output:Move Forward.
Output:Turn Right.
Output:Turn Right.
Output:Move Forward.
Output:Move Forward.
Output:Move Forward.
Output:Turn Right.
Output:Turn Right.
Output:Turn Right.
Output:Move Forward.
Output:Move Forward.
Output:Move Forward.
Output:Turn Right.
Output:Turn Right.
Output:Turn Right.
Output:Move Forward.
Output:Turn Right.
Output:Turn Right.
Output:Move Forward.
```

### Instructions
- Create a Console Project named `P2BareFunctions` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- You are only allowed to print:
  - `"Move Forward."`
  - `"Turn Right."`
- Using those two prints, make a character:
  - run three steps forward.
  - then turn around and run three steps forward
  - then turn left and run three steps forward.
  - then turn left and walk one step forward.
  - then turn around and walk one step forward.
- Make sure to introduce functions in order to avoid repetitive code!

Need Help? [Here's The Slides!](slides/README.md#2-bare-functions)

## 3 Call Stack

### Goal
```
Output:5...
Output:4...
Output:3...
Output:2...
Output:1...
Output:0...
Output:Launch!
```

### Instructions
- Create a Console Project named `P3CallStack` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Create a local variable named `timer` of type `int` and assign `5` to it.
- Create a function named `Countdown`
  - return type `void`
  - without parameters
  - when called:
    - it prints the value of variable `timer` to the console
    - it reduces the value of variable `timer` by `1`
    - if the timer is not negative, the function calls itself again
- Call the function `Countdown`
- How large will the call stack be before at its highest?
- What happens after that?
- Run the code line by line using the debugger. 
- Observe the call stack. Can you confirm your guesses?


Need Help? [Here's The Slides!](slides/README.md#3-call-stack)

## 4 Return Keyword

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
- Create a Console Project named `P4ReturnKeyword` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
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

## 5 Return Type

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
- Create a Console Project named `P5ReturnType` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Implement a Rock-Paper-Scissors Mini-Game.
- Write one function that returns the Player's Choice
  - but only, after the player has made a valid choice
- Write one function that returns the AI's choice
- Use those functions in your Core Game Loop

Need Help? [Here's The Slides!](slides/README.md#5-return-type)

## 6 One Parameter

### Goal
```
Output:What Fibonacci number would you like?
Input:7
Output:13
Output:What Fibonacci number would you like?
Input:10
Output:55
```

### Instructions
- Create a Console Project named `P6OneParameter` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- A classic! Implement a function that implements the nth Fibonacci Number
- Fibonacci number is a number that grows increasingly faster for higher numbers of the sequence
- `Fibonacci(0)` is defined as: `0`
- `Fibonacci(1)` is defined as: `1`
- For every other one:
- `Fibonacci(n) = Fibonacci(n-1) + Fibonacci(n-2)`
- Implement this function as a function that takes `n` as an argument and returns the correct result.

Here's the first few numbers of the sequence:

Sequence Number (n) | Result (Fibonacci(n))
--------------------|----------------------
0|0
1|1
2|1
3|2
4|3
5|5
6|8
7|13
8|21
9|34
10|55
11|89

Need Help? [Here's The Slides!](slides/README.md#6-one-parameter)

## 7 More Parameters

### Goal
Make the program compile by providing correct definitions and implementations of the functions that are missing in the following Source Code:

<details>
   <summary>Show Code</summary>

```cs
// the const keyword makes it so the values assigned to the
// variables cannot be changed during runtime
// this makes it more obvious, that these are configuration variables
const int deltaTimeMs = 1000 / 30;
const float deltaTime = deltaTimeMs / 1000f;
const int width = 30; // Change, if you like :)
const float animationDuration = 1f; // Change, if you like :)
float start = 0f;
float end = width;
float position = start;
float timePassed = 0f;

// TODO: Implement the missing functions here :)

void Update()
{
    // we increase the passedTime by deltaTime
    // we divide the deltaTime by animationDuration
    // this causes time to reach value 1 (the end) within 1 seconds for 1 second duration
    // but in half the time (two seconds) if passing in 2 seconds for duration
    timePassed += deltaTime / animationDuration;
    // lerp will linearly interpolate the position between start and end
    // for value 0, it will be at start, for value 1, it will be at end
    // for value 0.5, it will be in the middle
    position = Lerp(start, end, timePassed);
    if (timePassed > 1f)
    {   // bounce back:
        // we set start to become end and end to become start:
        // ADVANCED: in case you're wondering, the technique used here are called ValueTuples
        (start, end) = (end, start);
        // we reset the timePassed, so it begins the animation
        timePassed = 0;
    }
}

void Render()
{
    // we need to find out the closest position for the player
    // e.g. the player might be at position 2.3f
    // in that case, we want to render him at dash number 2.
    int closestIndex = RoundToInt(position);
    Console.Write('|');
    for (int i = 0; i <= width; i++)
    {
        Console.Write(i == closestIndex ? 'O' : '-');
    }
    Console.WriteLine('|');
}

// A very typical game loop:
GameLoop:
Console.SetCursorPosition(0, 0); // first, we reset the cursor
Update(); // then, we update all of our game objects
Render(); // then, we render everything to the screen
Thread.Sleep(deltaTimeMs); // 30FPS is enough for us :)
goto GameLoop;
```

</details>

### Instructions
- Create a Console Project named `P7MoreParameters` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- You need to implement two functions in this complex code sample!
- `Lerp` is a function that has three parameters of type `float` and returns a value of type `float`.
  - First Argument `from` of type `float` is used to pass a start value to `Lerp`
  - Second Argument `to` of type `float` is used to pass an end value to `Lerp`
  - Third Argument `t` of type `float` is used to tell at what position (in percent) the interpolated value is supposed to be.
  - `Lerp` stands for Linear Interpolation. And it describes the process of linearly (at constant speed/velocity) moving from one point to another.
  - The Mathematics behind it is: You start at `start` and add the Difference between `end` and `start` multiplied with `t`.
  - We won't go into much more detail here in terms of the Maths behind it, but it's very useful for animation and can even be (sort of ab-)used for smooth dampening.
- `RoundToInt` is a function that has one parameter of type `float` and returns a value of type `int`
  - It is supposed to Round the `float` to the nearest Integer and then cast the result to type `int` before returning it.
  - You can try implementing the Rounding Part yourself, or use `float MathF.Round(float value)`.
- If you have implemented both methods correctly, you should see a ball roll from left to right and then back to the left again.
- Check out the remaining source code, if you're interested in some advanced C# skills.

Need Help? [Here's The Slides!](slides/README.md#7-more-parameters)

## Done?
Return to the [Overview](../../../#2-loops)
