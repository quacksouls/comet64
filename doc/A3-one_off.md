# A3: one_off

## Problem

Print the following pattern:

```
####
####
####
####
####
####
####
###O
```

{% youtube id="6M4IQYDpoGU", title="43. A3: one_off, Comet 64" %}{% endyoutube %}

## Solution 1

Let `x` means a square is shaded and `o` means an unshaded square. Repeat the
pattern

```
xxxx
```

7 times, i.e. shade 28 squares. Then print the pattern

```
xxxo
```

```
loop:                    // Start of "loop".
    output = true;       // Shade the square.
    int++;               // How many squares shaded.
    check int < 28;      // Shade another square?
    jump if true: loop;  // If so, go to "loop".
output = true;           // Shade 3 squares.
output = true;
output = true;
output = false;          // Do not shade last square.
```

## Solution 2

Use a string to encode the solution. Check whether the character at index `i` is
`x` and print the boolean result. This solution is optimal, according to the
game.

```
str = xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment index.
```

## Solution 3

The first 31 squares are shaded, whereas square number 32 is unshaded. Print
`true` for the first 31 squares. This solution is optimal, according to the
game.

```
check int < 31;  // Have we shaded 31 squares yet?
output = bool;   // Print boolean result.
int++;           // Increment count.
```
