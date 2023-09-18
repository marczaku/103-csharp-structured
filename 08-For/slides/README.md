# Slides 8 - For Loops

### Introduction

Very often in programming, we encounter the situation, where we want to use a loop to iterate the same routine multiple times, e.g. 10 times, for each player:

### using goto

```cs
int counter = 0; // initial-statement
LoopStart:
if (counter < 10) // condition-statement
{ 
  Console.WriteLine("Hello, Player " + counter); // loop-body
  counter++; // iteration-statement
  goto LoopStart:
}
```

### using while

We can simplify above example using a `while`-loop:

```cs
int counter = 0; // initial-statement
while (counter < 10) // condition-statement
{ 
  Console.WriteLine("Hello, Player " + counter); // loop-body
  counter++; // iteration-statement
}
```

But even that is quite a lot of code for a task that we repeat so often. Is there a better solution?

### for loop

For this problem, a standardized has been introduced with the `for`-loop.\
Above sample would look like this:

```cs
int counter = 0; 
// initial-statement;condition-statement;iteration-statement
for(int counter = 0; counter < 10; counter++)) // 
{ 
  Console.WriteLine("Hello, Player " + counter); // loop-body
}
```

### Pattern: 

<img width="951" alt="image" src="https://user-images.githubusercontent.com/7360266/135169672-06abb667-5ebe-4371-bcbd-6c486339af0e.png">

```cs
for(initialStatement; conditionStatement; iterationStatement) 
{ 
  //for-loop-body 
}
```


`initial-statement` is executed ONCE when the `for` loop is started.
`condition-statement` is checked next EVERY loop.
- it is a `bool`-expression that needs to be `true` for the loop to continue.
- if it returns `false`, the body of the loop and the `iteration-statement`  are not executed (anymore)
`for-loop-body` is executed next after the `condition-statement` EVERY loop.
`iteration-statement` is executed next after the body EVERY loop.
the execution jumps back to the `condition-statement`

This is an example for one of the most traditional ways of using a for loop:
```cs
for (int i  = 0; i < 5; i++) {
  Console.Write(i);
}
```

Output:
```
01234
```

- initial statement: `int i = 0`
- condition statement: `i < 5`
- iteration statement: `i++`
- loop body code: `Console.WriteLine($"Iteration {i}");`


You can read a `for`-loop of this kind as "Repeat something 7 times":
```cs
// This will be executed for: 0123456
for(int i = 0; i < 7; i++) {
   // do something here
}
```

You could start counting at 1, too\
And/or use a different comparison operator `<=`\
But this is very uncommon, we usually start counting at `0`
```cs
// This will be executed for: 12345
for (int i  = 1; i <= 5; i++) {
  Console.WriteLine("Iteration" + i);
}
```

You could also go backwards by using `--` (the decrement-operator):
```cs
// This will be executed for: 43210
for (int i  =  4; i >= 0; i--) {
  Console.WriteLine("Iteration" + i);
}
```

Also, you can have a different step in the iteration:
```cs
// Will be executed for: i = 02468
for (int i  = 0; i < 10; i+=2) {
  Console.WriteLine("Iteration" + i);
}
```

You could even use completely different objects\
This is usually not recommended, as it may confuse developers:
```cs
// This could be a for loop that creates a monster, 
// runs for as long as the monster is alive 
// and has the monster attack every iteration.
for(Monster monster = new Monster(); monster.IsAlive(); monster.Attack()){
  UpdateUI();
}
```

You can nest for-loops, if you like to.\
This can be useful for example for checking all cells in a board game like chess:
```cs
for (int y = 0; y < 3; y++) { // iterate bottom-to-top
  for (int x = 0; x < 3; x++) { // iterate left-to-right
    Console.WriteLine($"Coordinate at x:{x}, y:{y}");
  }
}
```