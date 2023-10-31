# A6: outer_circle

## Problem

Print the pattern:

```
####
#OO#
#OO#
#OO#
#OO#
#OO#
#OO#
#####
```

{% youtube id="eGte5fDN-tA", title="46. A6: outer_circle, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the solution. Test whether the character at index `i` is
`x` and print the boolean result.

```
str = xxxxxooxxooxxooxxooxxooxxooxxxxx;  // Encoded solution.
char = str[int];  // Character at index i.
check char = x;   // Is character = "x"?
output = bool;    // Print boolean result.
int++;            // Increment the index.
```

## Solution 2

The first and last rows are shaded. As for the rows in between, we have the
pattern `xoox` repeated 6 times. This solution is optimal, according to the
game.

```
output = true;  // Shade the top row.  This also shade
output = true;  // the bottom row once the program
output = true;  // loops back to the top.
output = true;
loop:                    // Start of "loop".
    int++;               // How many rows have we processed?
    output = true;       // Shade.
    output = false;      // Unshade.
    output = false;      // Unshade.
    output = true;       // Shade.
    check int < 6;       // Have we processed all middle rows?
    jump if true: loop;  // If not, process the next row.
```
