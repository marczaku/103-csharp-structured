# Slides 1 - Functions

Note for anyone with more experience: We're only looking at Local Functions here. Not at Class Methods (, yet)

## 1. Scopes

Scopes are a very important concept in C#. Imagine a huge application like World of Warcraft. The code must contain Millions of variables. You might imagine, that after a short amount of time, all variable names would be in use already. To avoid conflicts here, variables only exist within a limited scope of the application, where ever it is needed. 

### 1.1 Like Street Names

It is similar to Street Names. Apparently, Ringvägen is Sweden's most common street name. Does this cause packages to Ringvägen 1 to arrive at the wrong address every day?

Thankfully not, since each Ringvägen is uniquely defined within its "Scope", which in this case is its Zip Code. For example:

- Ringvägen 2, 117 26 Stockholm
- Ringvägen 2, 181 51 Lidingö

### 1.2 Scope Delimiter
- Scopes in C# are started using `{` and ended using `}`
```cs
{ // Scope Start
  int a = 5;
} // Scope End
```

### 1.3 Nested Scopes
- Scopes can be nested. Every `{` must have a matching `}`
- Each `}` closes the last opened, unclosed `}`:

```cs
{ // Scope A Start
   { // Scope B Start
   } // Scope B End
   
   { // Scope C Start
   } // Scope C End
} // Scope A End
```

### 1.4 Variable Scope
- A variable is valid within its scope only, that is, between the previous `{` and the matching `}`

```cs
{ // Variable `a` Scope Start
  int a = 5; // `a` is declared here, its scope is the closest, previous `{`
  {
    Console.WriteLine(a); // `a` is still valid within the nested scope
  }
} // Variable `a` Scope End
```

- Outside of the scope, you can NOT access the variable!
```cs
{
  { // Variable `a` Scope Start
    int a = 5;
  } // Variable `a` Scope End
  Console.WriteLine(a); // Error, a is not defined in this scope.
}
```

- You can NOT declare two variables with the same name within the same scope:
```cs
{
  int z = 2;
  int z = 3; // ERROR: Variable named `z` is defined already
}
```

- Also not, if they are nested:
```cs
{
  int z = 2;
  {
    int z = 3; // ERROR: Variable named `z` is defined already
  }
}
```

- But of course, you can still assign new values to existing variables:

```cs
{
  int z = 2;
  z = 3; // This is fine, we assign a new value to the existing variable.
}
```


## 2. Bare Functions

Here, we will learn about parameter-less functions without returned values.\
Functions allow us to pack Blocks of Code into reusable packages. 

### The problem

Imagine this Code for making a lasagna:

```cs
Console.WriteLine("Fry meat.");
Console.WriteLine("Cut onions.");
Console.WriteLine("Fry onions.");
Console.WriteLine("Add tomato sauce.");
Console.WriteLine("Add spices.");
Console.WriteLine("Boil.");
```

Now imagine that in our code, there's multiple occasions in which we want to make Lasagna:

```cs
Console.WriteLine("Time for breakfast.");
if(isHungry) {
  // insert code for making lasagna here.
}
// ...
Console.WriteLine("Time for lunch.");
if(isHungry) {
  // insert code for making lasagna here.
}
// ...
Console.WriteLine("Time for dinner.");
if(isHungry) {
  // insert code for making lasagna here.
}
```

If we were to actually insert the whole code for making Lasagna here, we'd end up with this program:

<details>
  <summary>Full Code Sample</summary>

```cs
Console.WriteLine("Time for breakfast.");
if(isHungry)
{
  Console.WriteLine("Fry meat.");
  Console.WriteLine("Cut onions.");
  Console.WriteLine("Fry onions.");
  Console.WriteLine("Add tomato sauce.");
  Console.WriteLine("Add spices.");
  Console.WriteLine("Boil.");
}
// ...
Console.WriteLine("Time for lunch.");
if(isHungry)
{
  Console.WriteLine("Fry meat.");
  Console.WriteLine("Cut onions.");
  Console.WriteLine("Fry onions.");
  Console.WriteLine("Add tomato sauce.");
  Console.WriteLine("Add spices.");
  Console.WriteLine("Boil.");
}
// ...
Console.WriteLine("Time for dinner.");
if(isHungry)
{
  Console.WriteLine("Fry meat.");
  Console.WriteLine("Cut onions.");
  Console.WriteLine("Fry onions.");
  Console.WriteLine("Add tomato sauce.");
  Console.WriteLine("Add spices.");
  Console.WriteLine("Boil.");
}
```

</details>

And now imagine that we'd want to change our favorite Lasagna Recipe to include Garlic... That'd be quite a few places to make the same change.

### The Solution

We can define a function like this:

```cs
void MakeLasagna()
{
  Console.WriteLine("Fry meat.");
  Console.WriteLine("Cut onions.");
  Console.WriteLine("Fry onions.");
  Console.WriteLine("Add tomato sauce.");
  Console.WriteLine("Add spices.");
  Console.WriteLine("Boil.");
}
```

And use it (invoke it) like this:

```cs
MakeLasagna();
```

Every time you invoke this function, it will be executed step by step before returning to where your code left off before.

```cs
MakeLasagna(); // This will first execute the Lasagna-Recipe Line-By-Line
// And then continue here:
Console.WriteLine("I'm done making Lasagna!");
MakeLasagna(); // This will again execute the Lasagna-Recipe Line-By-Line
Console.WriteLine("Oops, I did it again.");
```

This new function allows us update our previous code sample to look like this:

```cs
Console.WriteLine("Time for breakfast.");
if(isHungry) {
  MakeLasagna();
}
// ...
Console.WriteLine("Time for lunch.");
if(isHungry) {
  MakeLasagna();
}
// ...
Console.WriteLine("Time for dinner.");
if(isHungry) {
  MakeLasagna();
}
```

A lot better :)

### The Syntax

You define a Function like this:

```cs
RETURN_TYPE FUNCTION_NAME(PARAMETER_LIST)
{ // Function Body/Scope Start
  // <- Put the Code of the Function here
} // Function Body/Scope End
```

### void

In the easiest case for the Return Type, it is of Type `void`, which stands for "nothing":

```cs
void SayHello()
{
  Console.WriteLine("Hello.");
}
```

This means, that the function does not return anything. Which again means, that there is no result that you could assign to a variable:

```cs
int result = SayHello(); // Error, Type `void` can not be case to Type `int`
```

Now you might try to define a variable of Type `void` in order to fix above error, but that won't work either:

```cs
void result = SayHello(); // Error, can not define variable of Type `void`
```

This proves: `void` means that there is no result from this function.

### Empty Parameters

In the easiest case, the Parameter-List is empty. This means, that no Argument NEEDS TO and no Argument CAN be passed to the function:

```cs
SayHello(); // OKAY
```

Arguments for Parameters can be passed within the Parantheses. But only, if the function requires them:

```cs
SayHello(5); // Error: SayHello takes 0 Arguments, but 1 was given.
```

You have done this already, when using `Console.WriteLine`; You passed an Argument of Type `string` to the function:

```cs
Console.WriteLine("Hello");
```

## 3. Call Stack

It's important to understand, what's happening when we're calling a function and what's going to be the next line executed.

A small Puzzle: What will the output be?

```cs
/*01*/void A(){ 
/*02*/  Console.Write("A");
/*03*/}
/*04*/void B(){
/*05*/  Console.Write("B");
/*06*/}
/*07*/void C(){
/*08*/  B();
/*09*/  Console.Write("C");
/*10*/}
/*11*/C();
/*12*/A();
```

So, what's happening here, exactly?

<details>
  <summary>Step by Step</summary>

### Step 1

Well, first of all, the bodies of any of the three functions don't get executed, unless the function is invoked. Which means, that the program falls all the way through to line 11:

```cs
/*11*/C();
```

The CallStack will look something like this:


| Method-Name | Location     | Code |
|-------------|--------------|------|
| void Main() | Program.cs:11|`C();` |

Where Main() is the Function-Name that's enclosing our whole C#-Script, `Program.cs` is the File-Name of our C#-Script and `11` is the Line Number where the execution currently stands.

In this line, function `C()` will be invoked, which will put the function's routine on top of the stack:

### Step 2

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void C()    | Program.cs:8 |`B();` |
| void Main() | Program.cs:11|`C();` |

You can see, that the original Program routine, `Main()` is still in Line 11. It is waiting for the routine `C()`, on top of the stack, to finish execution.

What does Stack mean exactly? A Stack in Programming is a Data Structure, which always pushes new items on the top and only allows access to the top-most item. When you're done with the top-most item, you can pop it.

You can imagine a stack of cards or a stack of plates as an analogy. You usually put cards and plates on the top of the stack and also remove them only from the top.

Let's look at line 8 again:

```cs
/*08*/  B();
```

Oof, another Function-Invocation. Guess what's happening next?

### Step 3

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void B()    | Program.cs:5 |`Console.Write("B");` |
| void C()    | Program.cs:8 |`B();` |
| void Main() | Program.cs:11|`C();` |

Okay, we can see the new Method Invocation being pushed on top of the stack as well. So, both `Main()` and `C()` are paused, waiting for `B()`, which is on top of the stack, to finish.

In Line 5, we find:

```cs
/*05*/  Console.Write("B");
```

Oh no, actually we're invoking another function here.

Which means, that the Call Stack will look something like this:

### Step 3.1

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void WriteLine()    | ??? | ??? |
| void B()    | Program.cs:5 |`Console.Write("B");` |
| void C()    | Program.cs:8 |`B();` |
| void Main() | Program.cs:11|`C();` |

But since this is external code, we don't need to bother about what's exactly happening there. We know that some code will be executed, which will print a `B` to the console. And then, when that function has completed, it will be popped from the stack again, allowing our function to continue:

### Step 3.2

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void B()    | Program.cs:6 |`}` |
| void C()    | Program.cs:8 |`B();` |
| void Main() | Program.cs:11|`C();` |

And here, we can see, that function `B()` also ends right there, which will cause it to also be popped from the stack, allowing `C()` to continue:

### Step 4

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void C()    | Program.cs:9 |`Console.Write("C");` |
| void Main() | Program.cs:11|`C();` |

I believe that at this point, you have a good idea of how this will continue:

### Step 4.1

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void WriteLine()    | ??? | ??? |
| void C()    | Program.cs:9 |`Console.Write("C");` |
| void Main() | Program.cs:11|`C();` |

### Step 4.2

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void C()    | Program.cs:10 |`}` |
| void Main() | Program.cs:11|`C();` |

### Step 5

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void Main() | Program.cs:12|`A();` |

### Step 6

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void A()    | Program.cs:1 |`Console.Write("A");` |
| void Main() | Program.cs:12|`A();` |

### Step 6.1

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void WriteLine()    | ??? | ??? |
| void A()    | Program.cs:1 |`Console.Write("A");` |
| void Main() | Program.cs:12|`A();` |

### Step 6.2

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void A()    | Program.cs:2 |`}` |
| void Main() | Program.cs:12|`A();` |

### Step 6.3

| Method-Name | Location     | Code |
|-------------|--------------|------|
| void Main() | Program.cs:13|`}` |

### Step 6.4

| Method-Name | Location     | Code |
|-------------|--------------|------|

Now, the Call Stack is empty and the application will quit.

</details>

## 4. Return Keyword

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

## 5. Return Type

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

## 6. One Parameter

### 6.1 Introduction

We have seen previously, how to define and invoke a Method without Parameters:

```cs
void SayHello(){
  Console.WriteLine("Hello.");
}
SayHello();
```

This is very useful, if you want a function to do the same thing every single time.

But sometimes, you want a function to do very similar things, but slightly differently every time. For example, we'd like to define a method that returns the Absolute of a number.

Calculating and returning the absolute of a number follows the exact same mathematical rules every time. But the number that we'd like to have an absolute of changes every time.

We can achieve this using a parameterized function:

```cs
int Abs(int number){
  if(number < 0){
    return -number;
  }
  return number;
}
```

Above function can be invoked as follows:

```cs
int absolute = Abs(-5); // 5
absolute = Abs(3); // 3
```

### 6.2 Defining a Parameter

You define a Parameter as follows:

```cs
ReturnType MethodName(ParameterType parameterName){
  // Method Body here
}
```

### 6.3 Invoking a Function with parameter

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

### 6.4 Parameter Scope

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

### 6.5 Passing an Argument

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

## 7. More Parameters

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