# B2: checker_board

## Problem

Print the pattern:

```
#O#O
O#O#
#O#O
O#O#
#O#O
O#O#
#O#O
O#O#
```

{% youtube id="OIcDAyb1wSs", title="51. B2: checker_board, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string of `x` and `o` to encode the pattern.

```
x := true
o := false
```

The register `int` is used as an index `i` to each string character. Check
whether character at index `i` is `x` and print the boolean result.

```
str = xoxooxoxxoxooxoxxoxooxoxxoxooxox;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment index.
```

## Solution 2

Consider the pattern

```
x o x o
o x o x
```

This pattern is repeated 4 times. We need to print the above pattern 4 times.
This solution is optimal, according to the game.

```
output = true;   // The pattern xoxo.
output = false;  //
output = true;   //
output = false;  //
output = false;  // The pattern oxox.
output = true;   //
output = false;  //
output = true;   //
```
