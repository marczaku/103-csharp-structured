# Slides 3 - Call Stack

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

| Method-Name | Location      | Code   |
|-------------|---------------|--------|
| void Main() | Program.cs:11 | `C();` |

Where Main() is the Function-Name that's enclosing our whole C#-Script, `Program.cs` is the File-Name of our C#-Script and `11` is the Line Number where the execution currently stands.

In this line, function `C()` will be invoked, which will put the function's routine on top of the stack:

### Step 2

| Method-Name | Location      | Code   |
|-------------|---------------|--------|
| void C()    | Program.cs:8  | `B();` |
| void Main() | Program.cs:11 | `C();` |

You can see, that the original Program routine, `Main()` is still in Line 11. It is waiting for the routine `C()`, on top of the stack, to finish execution.

What does Stack mean exactly? A Stack in Programming is a Data Structure, which always pushes new items on the top and only allows access to the top-most item. When you're done with the top-most item, you can pop it.

You can imagine a stack of cards or a stack of plates as an analogy. You usually put cards and plates on the top of the stack and also remove them only from the top.

Let's look at line 8 again:

```cs
/*08*/  B();
```

Oof, another Function-Invocation. Guess what's happening next?

### Step 3

| Method-Name | Location      | Code                  |
|-------------|---------------|-----------------------|
| void B()    | Program.cs:5  | `Console.Write("B");` |
| void C()    | Program.cs:8  | `B();`                |
| void Main() | Program.cs:11 | `C();`                |

Okay, we can see the new Method Invocation being pushed on top of the stack as well. So, both `Main()` and `C()` are paused, waiting for `B()`, which is on top of the stack, to finish.

In Line 5, we find:

```cs
/*05*/  Console.Write("B");
```

Oh no, actually we're invoking another function here.

Which means, that the Call Stack will look something like this:

### Step 3.1

| Method-Name      | Location      | Code                  |
|------------------|---------------|-----------------------|
| void WriteLine() | ???           | ???                   |
| void B()         | Program.cs:5  | `Console.Write("B");` |
| void C()         | Program.cs:8  | `B();`                |
| void Main()      | Program.cs:11 | `C();`                |

But since this is external code, we don't need to bother about what's exactly happening there. We know that some code will be executed, which will print a `B` to the console. And then, when that function has completed, it will be popped from the stack again, allowing our function to continue:

### Step 3.2

| Method-Name | Location      | Code   |
|-------------|---------------|--------|
| void B()    | Program.cs:6  | `}`    |
| void C()    | Program.cs:8  | `B();` |
| void Main() | Program.cs:11 | `C();` |

And here, we can see, that function `B()` also ends right there, which will cause it to also be popped from the stack, allowing `C()` to continue:

### Step 4

| Method-Name | Location      | Code                  |
|-------------|---------------|-----------------------|
| void C()    | Program.cs:9  | `Console.Write("C");` |
| void Main() | Program.cs:11 | `C();`                |

I believe that at this point, you have a good idea of how this will continue:

### Step 4.1

| Method-Name      | Location      | Code                  |
|------------------|---------------|-----------------------|
| void WriteLine() | ???           | ???                   |
| void C()         | Program.cs:9  | `Console.Write("C");` |
| void Main()      | Program.cs:11 | `C();`                |

### Step 4.2

| Method-Name | Location      | Code   |
|-------------|---------------|--------|
| void C()    | Program.cs:10 | `}`    |
| void Main() | Program.cs:11 | `C();` |

### Step 5

| Method-Name | Location      | Code   |
|-------------|---------------|--------|
| void Main() | Program.cs:12 | `A();` |

### Step 6

| Method-Name | Location      | Code                  |
|-------------|---------------|-----------------------|
| void A()    | Program.cs:1  | `Console.Write("A");` |
| void Main() | Program.cs:12 | `A();`                |

### Step 6.1

| Method-Name      | Location      | Code                  |
|------------------|---------------|-----------------------|
| void WriteLine() | ???           | ???                   |
| void A()         | Program.cs:1  | `Console.Write("A");` |
| void Main()      | Program.cs:12 | `A();`                |

### Step 6.2

| Method-Name | Location      | Code   |
|-------------|---------------|--------|
| void A()    | Program.cs:2  | `}`    |
| void Main() | Program.cs:12 | `A();` |

### Step 6.3

| Method-Name | Location      | Code |
|-------------|---------------|------|
| void Main() | Program.cs:13 | `}`  |

### Step 6.4

| Method-Name | Location | Code |
|-------------|----------|------|

Now, the Call Stack is empty and the application will quit.

</details>
