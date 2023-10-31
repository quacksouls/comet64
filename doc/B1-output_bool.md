# B1: output_bool

## Problem

Print the pattern:

```
OOOO
OOOO
OOOO
O###
####
####
####
####
```

{% youtube id="g9xZZ2AYB1k", title="50. B1: output_bool, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the solution. Check whether the character at index `i` is
`x` and print the boolean result.

```
str = oooooooooooooxxxxxxxxxxxxxxxxxxx;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment index.
```

## Solution 2

Grid cells are indexed from 1 onward. Each cell with index greater than 13 is
shaded. All other cells are unshaded. Compare the cell index, jump accordingly,
and shade as required. We assume the register `int` is initialized to zero at
the start.

```
int++;                // Increment index.
check int > 13;       // Is index > 13?
jump if true: shade;  // If so, go to "shade".
output = false;       // Unshade.
jump to: end;         // Go to "end".
shade:                // The "shade" branch.
    output = true;    // Shade.
end:                  // End of program.
```

## Solution 3

Similar to [Solution 2](#solution-2). However, we remove a jump instruction.
After checking for whether the index is greater than 13, we only need to print
the content of the register `bool`. Assume the register `int` is initially zero.
This solution is optimal, according to the game.

```
int++;           // Increment index.
check int > 13;  // Is index > 13?
output = bool;   // Print boolean result.
```
