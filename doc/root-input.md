# Root Input

## Problem

Given a perfect square, determine its square root.

{% youtube id="eX1tHziQwc8", title="34. Root input, Comet 64" %}{% endyoutube %}

## Solution 1

Let `n > 0` be an integer. Use the fact that `n^2` can be written as the series

```
n^2 = 1^2 + 3^2 + 5^2 + 7^2 + ... + (2k + 1)^2
```

for some integer `k > 0`. There are `n` terms in the series. The above
expression tells us that `n^2` can be written as the sum of the first `n` odd
non-negative integers. To determine the square root of `n^2`, start from 1 and
note `n := n - 1`. Continue with `n := n - 3` and so on. Each time we subtract
the next odd integer until `n = 0`. The number of odd integers used in the
subtraction is the same as the square root of `n^2`. Refer to the following for
more details:

https://www.geeksforgeeks.org/how-to-find-square-root-of-a-number/

We use the string register `str` to help us keep track of how many odd integers
we consider.

```
str = ;                   // Empty string.
reg = input;              // Read in the perfect square n^2.
int = -1;                 // Start from -1.
loop:                     // Start of "loop".
    int = int + 2;        // Odd non-negative integer k.
    reg = reg - int;      // n := n - k
    str = str + a;        // Used another odd integer.
    check reg = 0;        // Is n = 0?
    jump if false: loop;  // If not, go to "loop".
int = str.length;         // How many odd integers used.
output = int;             // Print the square root.
```

## Solution 2

Similar to [Solution 1](#solution-1). Note that if `reg = 0`, then `int` holds
the largest odd integer such that the subtraction `reg - int` results in zero.
Then the number of odd integers used is

```
floor(int / 2) + 1
```

```
reg = input;              // Read in the perfect square n^2.
int = -1;                 // Start from -1.
loop:                     // Start of "loop".
    int = int + 2;        // Next odd integer k.
    reg = reg - int;      // n := n - k
    check reg = 0;        // Is n = 0?
    jump if false: loop;  // If not, go to "loop".
int = int / 2;            // floor(k / 2)
int++;                    // floor(k / 2) + 1
output = int;             // Print the square root.
```

## Solution 3

Similar to [Solution 2](#solution-2). However, instead of checking for
`reg = 0`, we check for `reg < 0`. If `reg < 0`, then `floor(int / 2)` yields
the number of odd integers used. This solution is optimal, according to the
game.

```
reg = input;              // Read perfect square n^2.
int = -1;                 // Start from -1.
loop:                     // Start of "loop".
    int = int + 2;        // Next odd integer k.
    reg = reg - int;      // n := n - k
    check reg < 0;        // Is n < 0?
    jump if false: loop;  // If not, go to "loop".
int = int / 2;            // floor(k / 2)
output = int;             // Print the square root.
```

## Solution 4

Let `n > 0` be a perfect square. The idea is to iterate over each integer
`i > 0` and determine whether `i^2 = n`.

```
reg = input;              // Read the perfect square.
int = 0;                  // Start i from zero.
loop:                     // Start of "loop".
    int++;                // Increment the integer i.
    char = int;           // Store current integer i.
    int = int * int;      // i^2
    check reg = int;      // Is n = i^2?
    int = char;           // Current integer i.
    jump if false: loop;  // If not, go to "loop".
output = int;             // Print the square root.
```

## Solution 5

Use an old Japanese method. This algorithm is described in the paper:

-   Ashley Frazer Jarvis. Square roots by subtraction. _Mathematical Spectrum_,
    volume 37, pp.119--122, 2006.

This solution is optimal, according to the game. Let `n` be a perfect square.

```
reg = 5 * input;          // a := 5*n
int = 0;                  // b := 0
loop:                     // Start of "loop".
    reg = reg - int;      // a := a - b
    int = int + 10;       // b := b + 10
    check reg < int;      // Is a < b?
    jump if false: loop;  // If not, go to "loop".
int = int / 10;           // b := b / 10
output = int;             // Print the square root.
```
