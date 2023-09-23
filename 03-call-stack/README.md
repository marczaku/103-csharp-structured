# Exercises 3 - Call Stack

## Final Exercise

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
- Create a Console Project named `P03CallStack` [How To?](https://gist\.github\.com/marczaku/a8b3c38c37e8876a46194a73ed24b1f2)
- Create a local variable named `timer` of type `int` and assign `5` to it.
- Create a function named `Countdown`
  - return type `void`
  - without parameters
  - when called:
    - it prints the value of variable `timer` to the console
    - it reduces the value of variable `timer` by `1`
    - if the timer is not negative, the function calls itself again
- Invoke the function `Countdown`
- How large will the call stack be before at its highest?
- What happens after that?
- Run the code line by line using the debugger. 
- Observe the call stack. Can you confirm your guesses?

## P03_2FunctionPuzzle
- Use the code sample below. Use the functions `F1`, `F2`, `F3` and `F4` in the correct oder to generate the output `BAA-BABBA-AAA-AA-BAB`
```csharp
void F1(){
    Console.Write("A"); // A
}
void F2(){
    Console.Write("B"); // BA
    F1();
}
void F3(){
    F1();
    Console.Write("-"); // A-BAB
    F2();
}
void F4(){
    Console.Write("-"); // -A
    F1();
}

// Use F1, F2, F3 and F4 in the correct order here.
```


## P03_1Triangle
Draw the Triangle again, but this time using a recursive function instead of `goto`

```csharp
#####
####
###
##
#
```