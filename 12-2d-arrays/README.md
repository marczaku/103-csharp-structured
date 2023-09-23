# Exercises 12 - 2D Arrays

## Goal
<details>
  <summary>Toggle Me</summary>

```
Output:y
Output:4
Output:3
Output:2
Output:1
Output:0
Output:\01234x
Output:Give me a x coordinate.
Input:2
Output:Give me a y coordinate.
Input:3
Output:Give me a symbol.
Input:O
Output:y
Output:4
Output:3  O
Output:2
Output:1
Output:0
Output:\01234x
Output:Give me a x coordinate.
Input:1
Output:Give me a y coordinate.
Input:4
Output:Give me a symbol.
Input:E
Output:y
Output:4 E 
Output:3  O
Output:2
Output:1
Output:0
Output:\01234x
Output:Give me a x coordinate.
Input:2
Output:Give me a y coordinate.
Input:4
Output:Give me a symbol.
Input:Y
Output:y
Output:4 EY
Output:3  O
Output:2
Output:1
Output:0
Output:\01234x
```

</details>

## Instructions

We'll make a text-driven Painting Tool!

- Create a Console Project named `P2Paint`
- Create a two-dimensional array as the canvas. We want to be able to store letters in that array. What type do you need? An array of size 5x5 should be enough for this demo.
- Repeatedly:
  - Print all the contents of the two-dimensional array to the user by printing the complete array to the user. But also print the coordinates, so users understand which is the x and y coordinate and what values they have.
  - Ask the user for a x coordinate
  - Ask the user for a y coordinate
  - Ask the user for a symbol
  - Store the symbol at the correct index of the two dimensional array

Note: If you want to print a `\`, you need to escape the character: `\\`.

Need Help? [Here's The Slides!](slides/README.md#13-2d-arrays)

## Done?
Return to the [Overview](../../..#4-game-on)