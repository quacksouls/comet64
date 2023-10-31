# B4: middle_path

## Problem

Print the pattern:

```
O##O
OOOO
##OO
OOO#
#OOO
OO##
OOOO
O##O
```

{% youtube id="QazlB6o8aQg", title="53. B4: middle_path, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the pattern. Test whether character at index `i` is `x`
and print the boolean result.

```
str = oxxoooooxxoooooxxoooooxxoooooxxo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment index.
```

## Solution 2

We have the following pattern:

```
oxxoooo
```

Print `oxx`, then use a loop to print `oooo`.

```
output = false;          // Print the pattern oxx.
output = true;           //
output = true;           //
loop:                    // Start of "loop".
    output = false;      // Unshade a square.
    int++;               // How many squares have we unshaded.
    check int < 4;       // Have we unshaded < 4 squares?
    jump if true: loop;  // If so, go to start of "loop".
int = 0;                 // Otherwise, reset counter.
```

## Solution 3

Similar to [Solution 2](#solution-2). However, we print out the pattern
`oxxoooo` and let the game loop over the code. This solution is optimal,
according to the game.

```
output = false;  // Print the pattern oxxoooo
output = true;   // over and over.
output = true;   //
output = false;  //
output = false;  //
output = false;  //
output = false;  //
```
