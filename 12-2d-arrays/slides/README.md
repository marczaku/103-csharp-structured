# Slides 12 - 2D-Arrays

## Two-Dimensional Array

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

## One-Dimensional 2D-Array?
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

## Jagged Arrays
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