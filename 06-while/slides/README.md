# Slides 6 - While Loops

### using goto

A very common scenario of using goto is the following:

```cs
int playerHealth = 10;
AttackStart:
if(playerHealth > 0){ // continue fight, if the player is still alive
  // simulate fight:
  int damage = Random.Shared.Next(0, 3);
  playerHealth -= damage;
  Console.WriteLine($"Player takes {damage} Damage and has {playerHealth} HP left.");
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
  Console.WriteLine($"Player takes {damage} Damage and has {playerHealth} HP left.");
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
  userAnswer = Console.ReadLine();
}
// We can only get here, if the user has agreed.
Console.WriteLine("Thanks for buying my game.");
```
