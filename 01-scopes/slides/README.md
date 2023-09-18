# Slides 1 - Scopes

Scopes are a very important concept in C#. Imagine a huge application like World of Warcraft. The code must contain Millions of variables. You might imagine, that after a short amount of time, all variable names would be in use already. To avoid conflicts here, variables only exist within a limited scope of the application, where ever it is needed. 

## Like Street Names

It is similar to Street Names. Apparently, Ringvägen is Sweden's most common street name. Does this cause packages to Ringvägen 1 to arrive at the wrong address every day?

Thankfully not, since each Ringvägen is uniquely defined within its "Scope", which in this case is its Zip Code. For example:

- Ringvägen 2, 117 26 Stockholm
- Ringvägen 2, 181 51 Lidingö

## Scope Delimiter
- Scopes in C# are started using `{` and ended using `}`
```cs
{ // Scope Start
  int a = 5;
} // Scope End
```

## Nested Scopes
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

## Variable Scope
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
