# Exercises 11 - Arrays:

### Part 1

#### Goal
```
Output:How many numbers do you want to give me?
Input:5
Output:Okay, I'm listening...
Input:12
Input:5
Input:3
Input:7
Input:3
Output:What number are you looking for?
Input:5
Output:I found that number 1 times!
Output:What number are you looking for?
Input:11
Output:I found that number 0 times!
Output:What number are you looking for?
Input:3
Output:I found that number 2 times!
```

#### Instructions
- Create a Console Project named `P11_1Arrays`
- Ask the user, how many numbers he'd like to input.
- Create an array of that size.
- For each of the array's indices from `0` until `Length` (exclusive), do:
  - read input from the console
  - cast it to be a number
  - assign it to one of the slots of the array
- Continue asking the user, what number he's looking for.
  - Read the input from the console
  - Cast it to be a number
  - Count, how often that number exists in the array.
    - You can start counting at `0`
    - You can iterate over all elements like you did before (when filling it)
    - Then, if the number is the same, you can increase the count by 1
  - Print the count to the console
  

Need Help? [Here's The Slides!](slides/README.md#12-arrays)

### Part 2

#### Goal
```
Output:I will roll 10.000 numbers between 0 and 10:
Output:I rolled 0 a total of 987 times.
Output:I rolled 1 a total of 1002 times.
Output:I rolled 2 a total of 998 times.
...
```

#### Instructions
- Create a Console Project named `P11_2Arrays`
- Create an array to count the occurrences of random numbers
- roll 10.000 times for a number between 0 and 10 
- and count the number of times that you have rolled that specific number
- Afterwards, print the result to the console.

<details>
  <summary>Toggle, if you're stuck</summary>

  An array of Type `int` can be used to store `n` numbers. e.g. an array of size 5 can store 5 numbers. The indices of that array are: `0`, `1`, `2`, `3`, `4`. 

  Basically, the array will look like this:
  - 0: 0
  - 1: 0
  - 2: 0
  - 3: 0
  - 4: 0

  Now, if I roll a 4, I can simply increase the number at array index 4 by one `array[4]++;`:
  - 0: 0
  - 1: 0
  - 2: 0
  - 3: 0
  - 4: 1

  When I repeat that a few times, I should end up with an array looking something like this:
  - 0: 100
  - 1: 83
  - 2: 97
  - 3: 102
  - 4: 123

  Now, I can use a `for` loop to iterate over that array and print the index `i` and the number at each index `array[i]` to the console.

</details>

Need Help? [Here's The Slides!](slides/README.md#12-arrays)
