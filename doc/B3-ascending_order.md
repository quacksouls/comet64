# B3: ascending_order

## Problem

Print the pattern:

```
#O#O
O#OO
O#OO
OO#O
OOOO
#OOO
OOO#
OOOO
```

{% youtube id="bph3pxjlZA4", title="52. B3: ascending_order, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the given pattern. True is represented by `x` and false
is represented by `o`. The register `int` is initially zero. Use the register as
an index of the string. We check whether the character at index `i` is `x` or
`o`. The result should be in the register `bool`. This solution is optimal,
according to the game.

```
str = xoxooxoooxooooxoooooxooooooxoooo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = "x"?
output = bool;    // Print boolean result.
int++;            // Increment the index i.
```

## Solution 2

We want to print this pattern:

```
xo
xoo
xooo
xoooo
xooooo
xoooooo
xooooooo
```

The register `int` is a counter for how many squares we have unshaded so far.
The register `reg` keeps track of the maximum number of unshaded squares.

```
loop:                    // Start of "loop".
    check int < reg;     // Unshade another square?
    jump if false: end;  // If no, go to "end".
    output = false;      // Otherwise, unshade a square.
    int++;               // Increment counter.
    jump to: loop;       // Go to "loop".
end:                     // The "end" branch.
    output = true;       // Shade a square.
    reg++;               // Increment max. unshaded squares.
    int = 0;             // Reset counter.
```

## Solution 3

Similar to [Solution 2](#solution-2). Note that we can print `x` first. Next
comes as many `o` as we need to print. This solution is optimal, according to
the game.

```
output = true;           // Shade a square.
reg++;                   // Increment max. unshaded squares.
int = 0;                 // Reset counter.
loop:                    // Start of "loop".
    output = false;      // Unshade a square.
    int++;               // Increment counter.
    check int < reg;     // Unshade another square?
    jump if true: loop;  // If so, go to "loop".
```
