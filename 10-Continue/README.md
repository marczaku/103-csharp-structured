# Exercises 10 - Continue: 

## Final Exercise

## P10_1Skip

### Goal
```
Output:10 Health. What do you do?
Input:2
Output:12 Health. What do you do?
Input:-9
Output:3 Health. What do you do?
Input:Quit
Input:Okay. Game Over.
```

### Instructions
- Create a Console Project named `P10Continue` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Create this Minigame: The user starts with 10 Health.
- The Game continues while the user has more than 0 Health.
- Every turn, the user can pick, how to change the Health.
- If the user enters an invalid input, skip the turn.
- Otherwise, add the user's input to the Health.
- If the user enters `Quit`, the game ends before.

## Goal
```
Output:1
Output:3
Output:7
Output:9
Output:11
Output:Done.
```

Code Sample:
```cs
for(int i = 0;;i++){
    // -----------------------
    // only add code in between here...


    // ...and here
    // -----------------------
    Console.WriteLine(i);
}
Console.WriteLine("Done.");
```

### Instructions
- Create a Console Project named `P10_1Skip` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Copy above code into your project.
- Use `break` and `continue` in combination with `if` in order to:
  - Not print (skip) even numbers.
  - Not print (skip) numbers which are a multiple of `5`
  - Stop printing any more numbers before printing `13` (that'd be bad luck D:)


# Exercises 9 - Break:

