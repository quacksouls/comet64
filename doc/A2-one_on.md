# A2: one_on

## Problem

Print the following grid pattern.

```
#OOO
OOOO
OOOO
OOOO
OOOO
OOOO
OOOO
OOOO
```

{% youtube id="SJCjybQV_Rg", title="42. A2: one_on, Comet 64" %}{% endyoutube %}

## Solution 1

Only the first square is `true`. All other squares are `false`. Use a string to
encode the solution. Test whether the character at index `i` is `x` or `o`.
Print the boolean result. Assume the register `int` to be initially zero.

```
str = xooooooooooooooooooooooooooooooo;  // Encoded result.
char = str[int];  // The character at index i.
check char = x;   // Is character = x?
output = bool;    // Print the boolean result.
int++;            // Increment the index.
```

## Solution 2

Print `true` for the first square. Use a loop to print `false` for all other
squares.

```
output = true;       // Print true.
loop:                // Start of "loop".
    output = false;  // Print false.
    jump to: loop;   // Go to "loop".
```

## Solution 3

Assume the register `int` to be initially zero. Test the value of the register
and print the boolean result. Then increment the value of the register. This
solution is optimal, according to the game.

```
check int = 0;  // Is i = 0?
output = bool;  // Print boolean result.
int++;          // Increment i.
```
