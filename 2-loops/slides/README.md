# Slides 2 - Loops

Here, we will learn about using Loop-Keywords to structure our Program in repeatable iterations. This way, we can replace the use of the `goto`-Keyword with more standardized functions. Increasing our code's readability.

## 8. While Loops

### using goto

A very common scenario of using goto is the following:

```cs
int playerHealth = 10;
AttackStart:
if(playerHealth > 0){ // continue fight, if the player is still alive
  // simulate fight:
  int damage = Random.Shared.Next(0, 3);
  playerHealth -= damage;
  Console.WritLine($"Player takes {damage} Damage and has {playerHealth} HP left.");
  goto AttackStart; // and after those things, we return to the condition again.
}
Console.WriteLine("Unfortunately, the player has died.");
```

This can be reduced to:
```cs
LoopStart:
if(condition){
  // do something
  goto LoopStart;
}
// condition no longer true
```

For this standard scenario, C# has the following keyword:

### while

```cs
while(condition){
  // do something
}
// condition no longer true
```

The previous example would look like this:

```cs
int playerHealth = 10;
while(playerHealth > 0){ // continue fight, if the player is still alive
  // simulate fight:
  int damage = Random.Shared.Next(0, 3);
  playerHealth -= damage;
  Console.WritLine($"Player takes {damage} Damage and has {playerHealth} HP left.");
}
Console.WriteLine("Unfortunately, the player has died.");
```

You see, it saved us a few lines of code :)

<img width="893" alt="image" src="https://user-images.githubusercontent.com/7360266/135168452-01a877f2-47b4-480e-9169-e0bf70870248.png">

- You can use the `while`-keyword in combination with a `bool`-expression to form
  - a loop that repeats
  - as long as the `bool`-expression returns `true`
- The syntax is as follows:
```cs
while(conditionExpression){ // while-scope-start
  // put the code here, that you want to repeat while the bool-expression is true
} // while-scope-end
```
- In the following example, the numbers `0`, `1` and `2` are printed to the console
- When `i` reaches the value `3`
  - the expression `i < 3` 
  - becomes `3 < 3` 
  - which is `false`
  - therefore, the loop is interrupted and the code continues outside the loop
```cs
int i = 0;
while (i < 3)
{
  Console.WriteLine(i); // print i to the console
  i++; // increase i by 1
}
```
Output:
```
0
1
2
```

- Here is another example, where the application asks the user to agree.
- It repeats the request until the user finally types in `"Yes"`.

```cs
string userAnswer = "No";
// Repeat the loop while the user has not answered "Yes", yet.
while(userAnswer != "Yes")
{
  // Ask the uer to agree.
  Console.WriteLine("Do you want to buy my game? Yes or No?");
  // Assign the user's answer to `userAnswer`
  userAnswer = Console.ReadLine() == "Yes")
}
// We can only get here, if the user has agreed.
Console.WriteLine("Thanks for buying my game.");
```

## 9. Do..While Loops

### Some disadvantage of while...

The previous example has one small disadvantage:

```cs
string userAnswer = "No";
// Repeat the loop while the user has not answered "Yes", yet.
while(userAnswer != "Yes")
```

We need to initialize `userAnswer` in line 1, because else, in line 3, we'd access an uninitialized variable when comparing it to `"Yes"`. This would be invalid. Therefore, we need to initialize `userAnswer` with some value. In this case by using `= "No";`.

This is due to us checking the answer first and then asking the user. If only, there was a way of doing it the other way round. Like this:

```cs
AskAgain:
Console.WriteLine("Do you want to buy my game? Yes or No?");
string userAnswer = Console.ReadLine() == "Yes")
if(userAnswer != "Yes"){
  goto AskAgain;
}
Console.WriteLine("Thanks for buying my game.");
```

### do..while

In fact, there is (of course):

```cs
string userAnswer;
do
{
  Console.WriteLine("Do you want to buy my game? Yes or No?");
  userAnswer = Console.ReadLine() == "Yes")
} while (userAnswer != "Yes");
Console.WriteLine("Thanks for buying my game.");
```

That's it!

<img width="676" alt="image" src="https://user-images.githubusercontent.com/7360266/135168888-ef629d4b-5567-43a5-a3a7-fd06535ecc25.png">

- `do`..`while`-loops are very similar to `while`-loops
- but while `while`-loops first check the condition and then execute the code...
- `do`..`while`-loops first execute the code and then check the condition
  - Therefore, the code in the loop is guaranteed to execute AT LEAST once!

```cs
do { // while-scope-start
  // put the code here, that you want to repeat while the bool-expression is true
} // while-scope-end 
while (conditionExpression); 
```

- This example shows the difference pretty well:

```cs
int i = 100;

do {
  // First, print the current number
  Console.WriteLine(i);
  i++;
}
while (i < 3); // Then, check, if the current Number is still smaller than 3. If not, interrupt.
```

Output:
```
100
```

- This time, the number `100` was still printed, because it was printed first, and then it was checked, whether it's smaller than `3`.
- While the `while` loop would first check, whether 100 is smaller than 3 and then not print the number anymore.

## 10. For Loop

### Introduction

Very often in programming, we encounter the situation, where we want to use a loop to iterate the same routine multiple times, e.g. 10 times, for each player:

### using goto

```cs
int numberOfPlayers = 10;
int counter = 0; // initial-statement
LoopStart:
if (counter < numberOfPlayers) // condition-statement
{ 
  Console.WriteLine("Hello, Player " + counter); // loop-body
  counter++; // iteration-statement
  goto LoopStart:
}
```

### using while

We can simplify above example using a `while`-loop:

```cs
int numberOfPlayers = 10;
int counter = 0; // initial-statement
while (counter < numberOfPlayers) // condition-statement
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
int numberOfPlayers = 10;
int counter = 0; 
// initial-statement;condition-statement;iteration-statement
for(int counter = 0; counter < numberOfPlayers; counter++)) // 
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
- it is a `bool`-expression that needs to be true for the loop to continue.
- if it returns `false`, the body of the loop and the `iteration-statement`  are not executed (anymore)
`for-loop-body` is executed next after the `condition-statement` EVERY loop.
`iteration-statement` is executed next after the body EVERY loop.
the execution jumps back to the `condition-statement`

This is an example for one of the most traditional ways of using a for loop:
```cs
// Will be executed for 01234
for (int i  = 0; i < 5; i++) {
  Console.WriteLine("Iteration" + i);
}
```
- `initial-statement`: `int i = 0`
- `condition-statement`: `i < 5`
- `loop-body-code`: `Console.WriteLine($"Iteration {i}");`
- `iteration-statement`: `i++`


You can read a `for`-loop of this kind as "Repeat something 7 times":
```cs
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