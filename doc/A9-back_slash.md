# A9: back_slash

## Problem

Print the pattern:

```
#OOO
O#OO
OO#O
OOO#
#OOO
O#OO
OO#O
OOO#
```

{% youtube id="vYsMM5J7b9Y", title="49. A9: back_slash, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the solution. Check whether the character at index `i` is
`x` and print the boolean result.

```
str = xooooxooooxooooxxooooxooooxoooox;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment index.
```

## Solution 2

The pattern for the first 16 squares can be created as follows. We have a single
`x`. This is then followed by the pattern `oooox` repeated 3 times. The
remaining 16 squares follow the same pattern as described above. We assume the
register `int` is initially zero. This solution is optimal, according to the
game.

```
output = true;           // The single x.
loop:                    // Start of "loop".
    int++;               // Increment the counter.
    output = false;      // Print the pattern oooox
    output = false;      // 3 times.
    output = false;      //
    output = false;      //
    output = true;       //
    check int < 3;       // Do we print oooox again?
    jump if true: loop;  // If so, go to "loop".
int = 0;                 // Reset counter.
```
