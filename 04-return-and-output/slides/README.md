# Slides 4 - Return and Output
## 4.1 Return Keyword

Using the `return` Keyword, you can end a Method Execution right away:

```cs
void SayManyThings(){
  Console.WriteLine("I can say one thing.");
  return;
  Console.WriteLine("But can I say many things?");
}
```

Output:
```
Output:I can say one thing.
```

This is very useful, if you have any exit conditions:

```cs
void StoryTime(){
  Console.WriteLine("Do you want to hear a Story?");
  if(Console.ReadLine() == "Nope"){
    return;
  }
  Console.WriteLine("Glad to hear that. Once upon a [...]");
}
```

Or:

```cs
void NimTurn(){
  PlayerTurn();
  if(matches <= 0){
    // AI can not draw matches anymore, if the Game is Over already.
    return;
  }
  AITurn();
}
```

## 4.2 Return Type

If we change the Return Type of our Function, it ALLOWS us and at the same time FORCES us to `return` a value from our Function. This way, whoever called this function is guaranteed, that a value will be received:

Remember the Syntax of a Function?
```cs
RETURN_TYPE FUNCTION_NAME(PARAMETER_LIST)
{ // Function Body/Scope Start
  // <- Put the Code of the Function here
} // Function Body/Scope End
```

If we use anything but `void` as a Return Type, it will force us to use the `return` Keyword to return something:

```cs
int GetFive() {
  
}// ERROR: Not all Code Paths return a value
```

To fix this, we need to make sure that we return a value of the correct type, `int`, from this function:

```cs
int GetFive() {
  return 5;
}
```

Cool! This allows us, to use this function, where ever we like:

```cs
int five = GetFive();
Console.WriteLine(five); // 5
Console.WriteLine(GetFive()); // 5
```

Note: All Code Paths have to return a value:

```cs
int GetPlayerStrength(){
  if(health > 0){
    return 10;
  }
} // ERROR: Not all Code Paths return a value
```

This is to avoid unexpected behavior when assigning the result:

```cs
int health = 0;
int strength = GetPlayerStrength();
```

What would be returned from the Function in this case? When the `health` is `0`, nothing is returned after all... Since this is uncontrolled and unintended, C# forces us to return a value on all Code Paths:

```cs
int GetPlayerStrength(){
  if(health > 0){
    return 10;
  }
  // Dead players are not so strong...
  return 0;
}
```

But wait... Won't above Code Sample return two values, if the player has a `health` of `100`? Won't it return `10` first and then `0`?

No, it won't, since the `return` keyword [causes the execution of the method to be stopped immediately](#4-return-keyword).
