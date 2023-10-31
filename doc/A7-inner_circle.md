# A7: inner_circle

## Problem

Print the pattern:

```
OOOO
OOOO
O##O
O##O
O##O
O##O
OOOO
OOOO
```

{% youtube id="yQqltF-5waY", title="47. A7: inner_circle, Comet 64" %}{% endyoutube %}

## Solution 1

The pattern `oooo` repeats two times at the top and at the bottom. In between,
the pattern `oxxo` repeats 4 times. This solution uses a string to encode the
middle pattern.

```
outer:                    // Loop to print the pattern
    output = false;       // oooo.
    int++;                //
    check int < 8;        //
    jump if true: outer;  //
int = 0;                  // Reset the counter.
str = oxxooxxooxxooxxo;   // Encoded pattern for middle.
inner:                    // Loop to print the pattern
    char = str[int];      // oxxo 4 times.
    check char = x;       //
    output = bool;        //
    int++;                //
    check int < 16;       //
    jump if true: inner;  //
int = 0;                  // Reset counter.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we do not use an encoded string
to print the inner circle.

```
outer:                    // Loop to print the pattern
    output = false;       // oooo.
    int++;                //
    check int < 8;        //
    jump if true: outer;  //
int = 0;                  // Reset the counter.
inner:                    // Loop to print the pattern
    output = false;       // oxxo 4 times.
    output = true;        //
    output = true;        //
    output = false;       //
    int++;                //
    check int < 4;        //
    jump if true: inner;  //
int = 0;
```

## Solution 3

Use a string to encode the pattern. Test whether the character at index `i` is
`x` and print the boolean result.

```
str = oooooooooxxooxxooxxooxxooooooooo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = "x"?
output = bool;    // Print the boolean result.
int++;            // Increment the index.
```

## Solution 4

Start by unshading 7 squares. Then we have the pattern `ooxx` repeated 4 times.
The program then starts from the beginning to unshade another 7 squares. The
remaining 2 squares can be unshaded by the code that print the pattern `ooxx`.
This solution is optimal.

```
output = false;          // Unshade 7 squares.
output = false;          //
output = false;          //
output = false;          //
output = false;          //
output = false;          //
output = false;          //
loop:                    // Start of "loop".
    output = false;      // Unshade.
    output = false;      // Unshade.
    output = true;       // Shade.
    output = true;       // Shade.
    int++;               // How many ooxx have we printed?
    check int < 4;       // Have we printed ooxx 4 times?
    jump if true: loop;  // If not, go to "loop".
```
