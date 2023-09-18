# Slides 7 - Do..While Loops

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
string userAnswer = Console.ReadLine();
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
  userAnswer = Console.ReadLine();
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

- This time, the number `100` was still printed, because it was printed first, and afterwards it was checked, whether `101 < 3`
- While the `while` loop would first check the condition `100 < 3` and then not print the number at all.
