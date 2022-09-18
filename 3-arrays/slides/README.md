# Slides 3 - Conditions

## 12. Arrays

### The Problem

Often, in our code, we want to store multiple of things. For example, multiple item slots that the player can have:

```cs
public string item1;
public string item2;
public string item3;
// ...
```

Accessing these items will require a lot of code:

```cs
void UseItem(int number){
  if(number == 1 && item1 != ""){
    Use(item1);
    item1 = "";
  }
  if(number == 2 && item2 != ""){
    Use(item2);
    item2 = "";
  }
  if(number == 3 && item3 != ""){
    Use(item3);
    item3 = "";
  }
  // ...
}
```

- Now imagine that for a 100 item slots...
- And then for 1000
- How about having 1.000.000 Players?
- And what happens, if the number of item slots can vary (depending on the player's level)?

### The solution

The solution to this problem are arrays. They allow storing multiple items of the same kind in one collection:

```cs
// 10 item slots:
string[] items = new string[10];
```

And what's even better: They allow accessing each item using a numeric index:

```cs
void UseItem(int number){
  if(item[number] != ""){
    Use(item[number]);
    item[number] = "";
  }
}
```

### Definition

An `Array` can be defined for ANY Type using the syntax:

```cs
VARIABLE_TYPE[] variableName;
```

### Initialization

It can be initialized using the syntax:

```cs
variableName = new VARIABLE_TYPE[length];
```

e.g.:

```cs
int[] numbers = new int[5];
```

You can even initialize the Array with values by using the Array Initializer Syntax:

```cs
string[] options = {"Rock", "Paper", "Scissors"};
```

```cs
int[] numbers = {0, 1, 2, 3, 4, 5};
```

You can read an `Array`'s `Length`

```cs
Console.WriteLine(numbers.Length); // 5
```

And then use a `for`-loop:

```cs
for(int i = 0; i < numbers.Length; i++){
  Console.WriteLine(numbers[i]);
}
```

Creating an Array of 3 Elements:
```cs
int[] array = new int[3];
```

| Index   |   0  |   1  |   2  |
| :-----: | :--: | :--: | :--: |
|  Value  |   0  |   0  |  0   |


Assigning a value to the Array:
```cs
array[1] = 5;
```
| Index   |   0  |  >1< |   2  |
| :-----: | :--: | :--: | :--: |
|  Value  |   0  | **5** |  0   |

The first element has the index zero:
```cs
array[0] = 3;
```
| Index   |  >0< |   1  |   2  |
| :-----: | :--: | :--: | :--: |
|  Value  | **3** |   5  |  0   |

Invalid, array only has the size of 3:
```cs
array[5] = 2;
```
| Index   |   0  |   1  |   2  |
| :-----: | :--: | :--: | :--: |
|  Value  |   3  |   5  |  0   |

Invalid too, array only starts at 0:
```cs
array[-2] = 2
```
| Index   |   0  |   1  |   2  |
| :-----: | :--: | :--: | :--: |
|  Value  |   3  |   5  |  0   |

Invalid too, int array can only have ints:
```cs
array[3] = "Hello";
```
| Index   |   0  |   1  |   2  |
| :-----: | :--: | :--: | :--: |
|  Value  |   3  |   5  |  0   |

You can of course also read a value from the array:
```cs
Console.WriteLine(array[1]);
```
| Index   |   0  |  >1< |   2  |
| :-----: | :--: | :--: | :--: |
|  Value  |   3  |   5  |  0   |

Output:
```
5
```

This is valid: you have created a new Array with a different size, but all elements are empty again:
```cs
array = new int[5];
```
| Index   |   0  |   1  |   2  |   3  |   4  |
| :-----: | :--: | :--: | :--: | :--: | :--: |
|  Value  | **0** | **0** | **0** | **0** | **0** |

You can initialize a new Array with values:
```cs
array = new int[3] {3, 5, 7};
```
| Index   |   0  |   1  |   2  |
| :-----: | :--: | :--: | :--: |
|  Value  | **3** | **5** | **7** |

This keeps all elements when resizing. Internally, it just copies all the values.
```cs
Array.Resize(ref array, 5);
```
| Index   |   0  |   1  |   2  |   3  |   4  |
| :-----: | :--: | :--: | :--: | :--: | :--: |
|  Value  |   3  |   5  |   7  | **0** | **0** |

You can read the length of an array
```cs
int length = array.Length; // 5
```
| Index   |   0  |   1  |   2  |   3  |   4  |
| :-----: | :--: | :--: | :--: | :--: | :--: |
|  Value  |   3  |   5  |   7  |   0  |   0  |

You can use the length to do a for loop:
```cs
for (int i = 0; i < array.Length; i++) {
  Console.WriteLine(array[i]);
}
```
| Index   |   0  |   1  |   2  |   3  |   4  |
| :-----: | :--: | :--: | :--: | :--: | :--: |
|  Value  |   3  |   5  |   7  |   0  |   0  |

Output:
```
3
5
7
0
0
```

---

## 13. 2D-Arrays

### Two-Dimensional Array

- You can create two-dimensional arrays as well, using the `[,]` symbol with the type:
```cs
string[,] grid2d = new string[2,2];
```
| v 2nd Index \ 1st Index ->  |   0  |   1  |
|              :-----:        | :--: | :--: |
|                 0           | null | null |
|                 1           | null | null |

To set values, you need to provide two indices separated by comma now `[x,y]`: 
```cs
grid2d[0,0] = "topLeft";
```
| v 2nd Index \ 1st Index ->  |  >0< |   1  |
|              :-----:        | :--: | :--: |
|                >0<          | "topLeft" | null |
|                 1           | null | null |

```cs
grid2d[0,1] = "bottomLeft";
```
| v 2nd Index \ 1st Index ->  |  >0< |   1  |
|              :-----:        | :--: | :--: |
|                 0           | "topLeft" | null |
|                >1<          | "bottomLeft" | null |
```cs
grid2d[1,0] = "topRight";
```
| v 2nd Index \ 1st Index ->  |   0  |  >1< |
|              :-----:        | :--: | :--: |
|                >0<          | "topLeft" | "topRight" |
|                 1           | "bottomLeft" | null |
```cs
grid2d[1,1] = "bottomRight";
```
| v 2nd Index \ 1st Index ->  |   0  |  >1< |
|              :-----:        | :--: | :--: |
|                 0           | "topLeft" | "topRight" |
|                >1<          | "bottomLeft" | "bottomRight" |

### One-Dimensional 2D-Array?
- Alternatively, you can use a one-dimensional array and a helper index to get the right cell.
- Two-dimensional arrays do the same internally.
- No advantage in doing this yourself.
- But UnityEngine for example can serialize One-Dimensional Arrays, but not Two-Dimensional ones:

```cs
string[] grid1d = new string[4];
static int GetIndex(int x, int y, int width) {
  return y * width + x;
}
```
| Index   |   0  |   1  |   2  |   3  |
| :-----: | :--: | :--: | :--: | :--: |
|  Value  | null | null | null | null |
```cs
grid1d[GetIndex(0, 0, 2)] = "bottomLeft"; // 0 * 2 + 0 = 0
```
| Index   |  >0< |   1  |   2  |   3  |
| :-----: | :--: | :--: | :--: | :--: |
|  Value  | "bottomLeft" | null | null | null |

```cs
grid1d[GetIndex(0, 1, 2)] = "topLeft"; // 1 * 2 + 0 = 2
```
| Index   |   0  |   1  |  >2< |   3  |
| :-----: | :--: | :--: | :--: | :--: |
|  Value  | "bottomLeft" | null | "topLeft" | null |

```cs
grid1d[GetIndex(1, 0, 2)] = "bottomRight"; // 0 * 2 + 1 = 1
```
| Index   |   0  |  >1< |   2  |   3  |
| :-----: | :--: | :--: | :--: | :--: |
|  Value  | "bottomLeft" | "bottomRight" | "topLeft" | null |

```cs
grid1d[GetIndex(1, 1, 2)] = "topRight"; // 1 * 2 + 1 = 3
```
| Index   |   0  |   1  |   2  |  >3< |
| :-----: | :--: | :--: | :--: | :--: |
|  Value  | "bottomLeft" | "bottomRight" | "topLeft" | "topRight" |

### Jagged Arrays
- Another solution is to use an array of arrays.
- It has worse performance though!
- The advantage is: its rows can have different size.
- Not recommended! (Unless you want to have rows of different sizes)

```cs
string[][] gridJagged = new string[2][];
```
| Index   |   0  |   1  |
| :-----: | :--: | :--: |
|  Value  | null | null |

```cs
for (var i = 0; i < gridJagged.Length; i++) {
  gridJagged[i] = new string[2];
}
```
| Index   |   0  |   1  |
| :-----: | :--: | :--: |
|  Value  | <table><tr><td>Index</td><td>0</td><td>1</td></tr><tr><td>Value</td><td>null</td><td>null</td></tr></table> | <table><tr><td>Index</td><td>0</td><td>1</td></tr><tr><td>Value</td><td>null</td><td>null</td></tr></table> |

```cs
gridJagged[0][1] = "bottomLeft";
```
| Index   |  >0< |   1  |
| :-----: | :--: | :--: |
|  Value  | <table><tr><td>Index</td><td>0</td><td>>1<</td></tr><tr><td>Value</td><td>null</td><td>"bottomLeft"</td></tr></table> | <table><tr><td>Index</td><td>0</td><td>1</td></tr><tr><td>Value</td><td>null</td><td>null</td></tr></table> |

---