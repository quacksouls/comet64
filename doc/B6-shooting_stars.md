# B6: shooting_stars

## Problem

Print the pattern:

```
OO#O
O#OO
#OO#
OO#O
O#OO
#OO#
OO#O
O#OO
```

{% youtube id="ZIhpK8QOHL4", title="55. B6: shooting_stars, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the pattern. Test whether the character at index `i` is
`x` and print the boolean result.

```
str = ooxooxooxooxooxooxooxooxooxooxoo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment the index.
```

## Solution 2

We have the pattern:

```
oox
```

Print this pattern over and over. Let the game implicitly loop over the program
to take care of the rest. This solution is optimal, according to the game.

```
output = false;  // Print the pattern
output = false;  // oox over and over.
output = true;   //
```
