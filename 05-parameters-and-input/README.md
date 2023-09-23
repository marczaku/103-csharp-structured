# Exercises 5 - Parameters & Input

## 5.1 One Parameter

### Final Exercise

#### Goal

```
Output:What Fibonacci number would you like?
Input:7
Output:13
Output:What Fibonacci number would you like?
Input:10
Output:55
```

#### Instructions

- Create a Console Project named `P05_1OneParameter` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- A classic! Implement a function that implements the nth Fibonacci Number
- Fibonacci number is a number that grows increasingly faster for higher numbers of the sequence
- `Fibonacci(0)` is defined as: `0`
- `Fibonacci(1)` is defined as: `1`
- For every other one:
- `Fibonacci(n) = Fibonacci(n-1) + Fibonacci(n-2)`
- Implement this function as a function that takes `n` as an argument and returns the correct result.

Here's the first few numbers of the sequence:

| Sequence Number (n) | Result (Fibonacci(n)) | 
|---------------------|-----------------------| 
| 0                   | 0                     | 
| 1                   | 1                     | 
| 2                   | 1                     | 
| 3                   | 2                     | 
| 4                   | 3                     | 
| 5                   | 5                     | 
| 6                   | 8                     | 
| 7                   | 13                    | 
| 8                   | 21                    | 
| 9                   | 34                    | 
| 10                  | 55                    | 
| 11                  | 89                    | 

### P05_0_FirstParam
Write a function that takes one string parameter. Print the parameter to the console. Invoke the function with the following arguments:
- `"Marc"`
- `"Game Programming"`
- `"Forsbergs"`

### P05_1_1Double
Write a function that takes one integer parameter. It prints double the value to the console. Invoke the function with the following arguments: 
- `5`
- `-2`
- `0`
- `100`
- `1_000_000_000`
- `2_000_000_000`

### P05_1_2Cubical
Write a function that takes one integer parameter. It prints the cubical of the number (the number to the power of three) to the console. Invoke the function with the following arguments:
- `1`
- `0`
- `2`
- `3`
- `-4`

### P05_1_3Square
Write a function that takes one rational number parameter. It returns the square of the number as a rational number. Invoke the function and assign the result to a variable, then print the value of the variable to the console for the following arguments:
- `0.5f`
- `-2f`
- `0f`
- `4.2f`

### P05_2_4PrimeNumber
Write a function that takes an integer argument and returns `true` if it is a Prime Number or `false` if it is not. Use recursive function calls instead of Loops.

### P05_1_5Countdown
Implement the countdown again by having a function invoke itself (recursively) printing the numbers while counting down. The function takes one argument of type integer. e.g.:
- Arguent: `10`
- Output: `10...9...8...7...6...5...4...3...2...1...0...`

## 5.2 More Parameters

### Final Exercise

#### Goal

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

// -----------------------------------
// TODO: Implement the missing functions between here...


// and here!
// -----------------------------------

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

#### Instructions

- Create a Console Project named `P05_2MoreParameters` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Copy Above Source Code into your `Program.cs`-File.
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

## P05_2_0FullName
Write a function that takes two string Parameters for first name and last name and then prints a welcoming message to the console. Invoke it with the arguments:
- `"Marc"`, `"Zaku"`
- `"James"`, `"Bond"`
- `"Michael"`, `"Jackson"`

### P05_2_1Average
Write a function that takes two integer arguments and prints the average of both numbers. Test it with the following arguments:
- `2`, `6`
- `0`, `10`
- `-12`, `12`
- `11`, `9`

### P05_2_2Power
Write a function that takes two integer arguments and prints the first argument to the power of the second number. Test it with the following arguments:
- `3`, `2`
- `5`, `1`
- `2`, `5`
- `2`, `10`
- `19`, `0`
- `13`, `1`

### P05_2_3NextDoubleBetween
Write a function that takes to double arguments and prints a random number between the first argument (inclusive) and the second argument (exclusive). Figure out a way of testing the function.

### P05_2_4GetUserNumberBetween
Write a function that takes two integer arguments and then asks the user repeatedly for a valid number until the user correctly entered a number between the first and second argument. Return the user's number.