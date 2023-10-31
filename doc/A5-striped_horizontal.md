# A5: striped_horizontal

## Problem

Print the pattern:

```
####
oooo
####
oooo
####
oooo
####
oooo
```

{% youtube id="iQsvu3KtASs", title="45. A5: striped_horizontal, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the solution. Let `x` be a row of shaded squares and `o`
a row of unshaded squares. We have the pattern `xo` repeated 4 times.

```
str = xoxoxoxo;           // Encoded solution.
loop:                     // Start of "loop".
    char = str[int];      // The 4 squares in a row.
    int++;                // Increment the index.
    check char = x;       // Is the row shaded?
    jump if true: shade;  // If so, go to "shade".
    output = false;       // Otherwise unshade 4 squares.
    output = false;       //
    output = false;       //
    output = false;       //
    jump to: loop;        // Go to "loop".
shade:                    // The "shade" branch.
    output = true;        // Shade 4 squares.
    output = true;
    output = true;
    output = true;
```

## Solution 2

Use a string to encode the solution. Test whether the character at index `i` is
`x` and print the boolean result.

```
str = xxxxooooxxxxooooxxxxooooxxxxoooo;  // Encoded solution.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment the index i.
```

## Solution 3

Consider the following definitions:

```
x := shaded square
o := unshaded square
```

We have the pattern `xxxxoooo` repeated 4 times. This solution is optimal,
according to the game.

```
output = true;
output = true;
output = true;
output = true;
output = false;
output = false;
output = false;
output = false;
```
