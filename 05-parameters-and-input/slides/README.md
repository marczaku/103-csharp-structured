# Slides 5 - Parameters & Input
## 5.1. One Parameter

### Introduction

We have seen previously, how to define and invoke a Method without Parameters:

```cs
void SayHello(){
  Console.WriteLine("Hello.");
}
SayHello();
```

This is very useful, if you want a function to do the same thing every single time.

But sometimes, you want a function to do very similar things, but slightly differently every time. For example, we'd like to define a method that prints the double value of a number.

Calculating and returning the double of a number follows the exact same mathematical rules every time. But the number that we'd like to have double of changes every time.

We can achieve this using a parameterized function:

```cs
void PrintDouble(int number){
  Console.WriteLine(number*2);
}
```

Above function can be invoked as follows:

```cs
PrintDouble(3); // 6
PrintDouble(10); // 20
PrintDouble(-2); // -4
```

### Defining a Parameter

You define a Parameter as follows:

```cs
ReturnType MethodName(ParameterType parameterName){
  // Method Body here
}
```

### Invoking a Function with parameter

When you invoke a function with one Parameter, you need to pass an Argument of a matching type to the function:

```cs
MethodName(someValue);
```

e.g.:

```cs
Abs(3);
```

If the function requires one argument, but you don't pass one, your code won't compile and show an error:

```cs
Abs(); // ERROR: Function requires 1 argument, but is invoked with 0.
```

You can not pass an Argument of the wrong Type:

```cs
Abs("Hello"); // ERROR: No overload for Abs(string) exists.
```

### Parameter Scope

A parameter can be used within the scope of the function only:

```cs
void Print(string value){
  Console.WriteLine(value);
}
value = "Hello"; // ERROR: undefined variable `value` (it is only defined within the scope of the method)
```

A parameter can also have the same name as another variable outside its scope:

```cs
int value = 5;
void Print(string value){
  Console.WriteLine(value);
}
value = 6;
Print("Hello");
```

### Passing an Argument

The following concept is a very important one and often a topic of confusion for young developers.

When you pass a variable as an argument, its value gets copied to the function. This means, that the original variable will not be affected by any changes within the function:

```cs
int number = 5;
void Change(int number){
  number = 7;
  Console.WriteLine(number); // 7
}
Change(number);
Console.WriteLine(number); // 5
```

In above sample, the following happens:

<details>
  <summary>Step by Step</summary>

#### Step 1

First, the Variable named `number` is defined and the value `5` is assigned to it:

| Method-Name | Location     | Code | Variables |
|-------------|--------------|------|-----------|
| void Main() | Program.cs:1|`int number = 5;` | `int number: 5`|

#### Step 2

Then, the function named `Change` is invoked, passing the value of `number` (`5`) as an argument to the function:

| Method-Name | Location     | Code | Variables |
|-------------|--------------|------|-----------|
| void Main() | Program.cs:6|`Change(number)` | `int number: 5`|

#### Step 3.1

This means, that the value `5` gets copied to the parameter of the function:

| Method-Name | Location     | Code | Variables |
|-------------|--------------|------|-----------|
| void Change() | Program.cs:2|`{` | `int number: 5`|
| void Main() | Program.cs:6|`Change(number)` | `int number: 5`|

#### Step 3.2

When `7` gets assigned to `number`, this affects the function's parameter only. Not the original variable with the same name:

| Method-Name | Location     | Code | Variables |
|-------------|--------------|------|-----------|
| void Change() | Program.cs:3|`number = 7;` | `int number: 7`|
| void Main() | Program.cs:6|`Change(number)` | `int number: 5`|

#### Step 4

When printing `number` within the function `Change`, it will print the number of the function's parameter, which is `7`.

| Method-Name | Location     | Code | Variables |
|-------------|--------------|------|-----------|
| void Change() | Program.cs:4|`Console.WriteLine(number);` | `int number: 7`|
| void Main() | Program.cs:6|`Change(number)` | `int number: 5`|

#### Step 4.1

When the function ends...

| Method-Name | Location     | Code | Variables |
|-------------|--------------|------|-----------|
| void Change() | Program.cs:4|`}` | `int number: 7`|
| void Main() | Program.cs:6|`Change(number)` | `int number: 5`|

#### Step 4.2

It will pop the parameter `number` and its value `7` off the stack and make room again for the variable `number`, whose value is still `5`. `Console.WriteLine` in the `Main`-procedure also references the variable named `number`, not the parameter:

| Method-Name | Location     | Code | Variables |
|-------------|--------------|------|-----------|
| void Main() | Program.cs:7|`Console.WriteLine(number);` | `int number: 5`|

</details>

## 5.2 More Parameters

The case for two parameters is not much different from the case with one parameter:

```cs
void DrawCard(int number){
  // ...
}
```

```cs
DrawCard(5);
DrawCard(0);
DrawCard(-1);
```

If you want to have more than one Parameter, you need to specify each Parameter by Type and Name, separated by `,` (comma):

```cs
void CreateUser(string firstName, string lastName){
  // ...
}
```

When invoking the function, you need to pass arguments with the correct:
- number
- order
- type

```cs
CreateUser("Marc", "Zaku");
CreateUser("Anders", "Hejlsberg");
```

Each argument will be passed as a value to the property at the same position:

Argument `"Marc"` at first position -> Parameter `firstName` at first position

Argument `"Zaku"` at second position -> Parameter `lastName` at second position

A few examples, where things have gone wrong for the following Method:

```cs
void CreateUser(string name, int age, bool wantsNewsletter){
  // ...
}
```

Too few arguments:
```cs
CreateUser("Marc", 32); // ERROR: requires 3 arguments, but only two are given
```

Too many arguments:
```cs
CreateUser("Marc", 32, true, 12); // ERROR: requires 3 arguments, but 4 are given
```

Arguments with wrong types:
```cs
CreateUser("Marc", "32", "True"); // ERROR: expected argument of type `int`, but was given `string` "32"
```

Arguments in wrong order:
```cs
CreateUser(true, 32, "Marc"); // ERROR: expected argument of type `string`, but was given `bool` true
```
