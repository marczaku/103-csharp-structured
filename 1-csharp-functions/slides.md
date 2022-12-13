
## 8. Math

- `System.Math` is a `static` class containing many useful functions for numbers
  - `static` means, it can not be instantiated, you can not write `Math math = new Math();`
- If you want to solve a mathematical problem, see, if there‘s a solution already
- Most of these functions exist for many data types (`int`, `float`, `double`, …)
- Here is an overview of the most commonly used ones:
- `int Max(int, int)` returns the higher of two numbers
```cs
int max = Math.Max(5, 3); // 5, because it is the larger number
```

Alright, I'm running out of Mut zur Lücke right now. It's time we do a quick

### 8.1 Introduction To Methods

`void WriteLine(string value);`

Means, that 
- the Method returns `void`, which stands for "nothing".
- the Method has one Parameter of Type `string` with the name `value`.
  - Parameters are written within `()`
  - The name of the Parameter is purely cosmetic and should help you understand, what the Method expects.
    - e.g. `void CreateUser(string userName);` makes it clear that it expects the user name. And not the family name or so.
  - The type of the parameter is important. If it does not match, you will get Errors.

`int Max(int a, int b);`

Means, that
- the Method returns a value of type `int`. Which you can assign to a variable:
  - `int a = Math.Max(3, 5);`
- Or Pass into another Method:
  - `Console.WriteLine(Math.Max(3, 5));`
- the Method has two Parameters. Both of type `int` with the names `a` and `b`.
  - Multiple parameters are separated by `,`

That's it for now. We will learn the details about Methods a bit further down the road.

### 8.2 More Math

- `int Min(int, int)` returns the smaller of two numbers
```cs
int min = Math.Min(5, 3); // 3, because it is the smaller number
```
- `double Sqrt(double)` returns the Square Root of a number. You remember? The number, that if multiplied with itself results in the number you put in.
```cs
double sqrt = Math.Sqrt(16); // 4.0, because 4 * 4 = 16
```
- `double Abs(double)` returns the absolute of a number, which is always positive. Useful for calculating distances.
```cs
double abs = Math.Abs(-4.3); // 4.3
```
- `double Round(double)` returns the rounded value of a number (closest integer). Uses statistical rounding, not the one you're used to. Test it for 1.5 and 2.5 :)
```cs
double round = Math.Round(12.6); // 13, because it's the closest integer (0.4 difference), closer than 12 (0.6 difference)
```
- `double Floor(double)` returns the value of the number rounded to the lower integer
```cs
double floor = Math.Floor(12.6); // 12 is the next lower integer
```
- `double Ceiling(double)` returns the value of the number rounded to the higher integer
```cs
double ceil = Math.Ceiling(12.1); // 13 is the next higher integer
```
- `int Clamp(int value, int min, int max)` returns the `value` made fit `min` and `max`
```cs
double clamp = Math.Clamp(15, 0, 10); // The value of 15 fits between 0 and 10 only up to the maximum of 10
```
- `double Pow(double value, double power)` returns the `value` to the power of `power`.
```cs
double pow = Math.Pow(2, 3); // 8, because 2^3 = 2 * 2 * 2 = 8
```

---

## 9. Strings

- There‘s a series of functions for working with strings.
- The most commonly used ones are shown in the code sample above. 
- You already know, how to define and assign strings
```cs
string firstName = "John";
string lastName = "Kane";
```
- We can get the length of a string returned
```cs
string length = firstName.Length; // 4
```
- We can make a string All-Uppercase or All-Lowercase
```cs
string upper = firstName.ToUpper(); // JOHN
string lower = firstName.ToLower(); // john
```
- We can combine strings into a larger string using the `+`-Operator
```cs
string fullName = firstName + " " + lastName; // John Kane
```
- We can combine strings using String-Interpolation. Put the `$`-operator before a string and variables between `{` and `}`
```cs
string interp = $"{firstName} {lastName}"; // John Kane
```
- You can get the character at any index of the string. The first index is `0`
```cs
char char1 = firstName[0]; // 'J'
```
- You can also get the index of the first occurrence of a character or string. Again, counting starts at `0`
```cs
int index = firstName.IndexOf("h"); // 2
```
- You can get a sub-part of a string starting at a certain index (1) until the end of the string
```cs
string sub = firstName.SubString(1); // "ohn"
```
- You can get a sub-part of a string starting at a certain index (1) with a certain length (2)
```cs
string sub = firstName.SubString(1, 2); // "oh"
```
- You can replace all occurances of a character or string with another one
```cs
string replace = fullName.Replace( 'n', 'd'); // "Johd Kade"
```
One thing to keep in mind:\
Strings are `immutable`\
That means: A `string` can never be changed.\
So, when you call a function on a variable, it never changes the variable itself.\
Instead, it returns a new string that you can or need to assign to the same, or a new variable.
In other words:
```cs
string fullName = "John Kane";
fullName.Replace('n', 'd');
Console.WriteLine(fullName);
```

```
Output:John Kane
```

```cs
string fullName = "John Kane";
fullName = fullName.Replace('n', 'd');
Console.WriteLine(fullName);
```

```
Output:Johd Kade
```



---
