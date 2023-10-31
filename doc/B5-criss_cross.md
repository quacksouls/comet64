# B5: criss_cross

## Problem

Print the pattern:

```
OO#O
O#OO
#OOO
O#OO
OO#O
OOO#
OO#O
O#OO
```

{% youtube id="XuQFUTj2hqA", title="54. B5: criss_cross, Comet 64" %}{% endyoutube %}

## olution 1

Encode the pattern as a string. Check whether the character at index `i` is `x`
and print the boolean result. This solution is optimal, according to the game.

```
str = ooxooxooxooooxooooxooooxooxooxoo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment index.
```

## Solution 2

Print the pattern `oox` 3 times. Then print the pattern `oooox` 3 times. Let the
game loop back to take care of the rest. This solution is optimal, according to
the game.

```
top:                       // Print the pattern
    output = false;        // oox 3 times.
    output = false;        //
    output = true;         //
    int++;                 //
    check int < 3;         //
    jump if true: top;     //
int = 0;                   // Reset counter.
bottom:                    // Print the pattern
    output = false;        // oooox 3 times.
    output = false;        //
    output = false;        //
    output = false;        //
    output = true;         //
    int++;                 //
    check int < 3;         //
    jump if true: bottom;  //
int = 0;                   // Reset counter.
```
