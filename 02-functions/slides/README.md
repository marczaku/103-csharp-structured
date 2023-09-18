# Slides 2 - Functions

Here, we will learn about parameter-less functions without returned values.\
Functions allow us to pack Blocks of Code into reusable packages. 

## The problem

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

## The Solution

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

## The Syntax

You define a Function like this:

```cs
RETURN_TYPE FUNCTION_NAME(PARAMETER_LIST)
{ // Function Body/Scope Start
  // <- Put the Code of the Function here
} // Function Body/Scope End
```

## void

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

## Empty Parameters

In the easiest case, the Parameter-List is empty. This means, that no Argument NEEDS TO and no Argument CAN be passed to the function:

```cs
SayHello(); // OKAY
```

Arguments for Parameters can be passed within the Parentheses. But only, if the function requires them:

```cs
SayHello(5); // Error: SayHello takes 0 Arguments, but 1 was given.
```

You have done this already, when using `Console.WriteLine`; You passed an Argument of Type `string` to the function:

```cs
Console.WriteLine("Hello");
```
