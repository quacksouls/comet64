# A4: striped_vertical

## Problem

Print the pattern:

```
#O#O
#O#O
#O#O
#O#O
#O#O
#O#O
#O#O
#O#O
```

{% youtube id="eGppSPxuh0Q", title="44. A4: striped_vertical, Comet 64" %}{% endyoutube %}

## Solution 1

Odd numbered squares are shaded, whereas even numbered squares are unshaded. We
have the pattern of shade-unshade repeated over and over.

```
int = 1;                    // Start from odd numbered square.
loop:                       // Start of "loop".
    check int = 0;          // Are we unshading?
    jump if true: unshade;  // If so, go to "unshade".
    output = true;          // Otherwise, we shade.
    int = 0;                // Switch to unshade.
    jump to: loop;          // Go to "loop".
unshade:                    // The "unshade" branch.
    output = false;         // Unshade.
```

## Solution 2

Use a string to encode the pattern. Test whether the character at index `i` is
`x` and print the boolean result.

```
str = xoxoxoxoxoxoxoxoxoxoxoxoxoxoxoxo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment the index.
```

## Solution 3

Let `x` be a shaded square and `o` an unshaded square. We have the pattern
`xoxo` repeated 8 times.

```
output = true;   // Shade.
output = false;  // Unshade.
output = true;   // Shade.
output = false;  // Unshade.
```

## Solution 4

Similar to [Solution 3](#solution-3). However, note that we have the pattern
`xo` repeated 16 times. This solution is optimal, according to the game.

```
output = true;   // Shade.
output = false;  // Unshade.
```
