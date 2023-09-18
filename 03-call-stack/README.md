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

## P03_1Triangle
Draw the Triangle again, but this time using a recursive function instead of `goto`

```csharp
#####
####
###
##
#
```