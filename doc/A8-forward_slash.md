# A8: forward_slash

## Problem

Print the pattern:

```
OOO#
OO#O
O#OO
#OOO
OOO#
OO#O
O#OO
#OOO
```

{% youtube id="BH_9v0Ay4iI", title="48. A8: forward_slash, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the pattern. Check whether the character at index `i` is
`x` and print the boolean result.

```
str = oooxooxooxooxooooooxooxooxooxooo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment index.
```

## Solution 2

The pattern for the first 16 squares can be created as follows. We have the
pattern `ooo` at the start. Then the pattern `xoo` is repeated 3 times, followed
by a single `o`. Repeat the above procedure for the remaining 16 squares. We
assume the register `int` is initially zero. This solution is optimal, according
to the game.

```
output = false;          // The pattern ooo at the start.
output = false;          //
output = false;          //
loop:                    // Start of "loop".
    output = true;       // The pattern xoo is repeated
    output = false;      // 3 times.
    output = false;      //
    check int < 3;       // Do we need to print xoo again?
    int++;               //
    jump if true: loop;  // If so, go to "loop".
int = 0;                 // Reset counter.
output = false;          // The single o at the end.
```
