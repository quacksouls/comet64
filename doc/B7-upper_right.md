# B7: upper_right

## Problem

Print the pattern:

```
####
O###
OO##
OOO#
####
O###
OO##
OOO#
```

{% youtube id="M_L1y-LVhkU", title="56. B7: upper_right, Comet 64" %}{% endyoutube %}

## Solution 1

Use a string to encode the pattern. Test whether the character at index `i` is
`x` and print the boolean result. This solution is optimal, according to the
game.

```
str = xxxxoxxxooxxoooxxxxxoxxxooxxooox;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment the character index.
```

## Solution 2

The first half of the pattern is the same as the second half. Use a loop to
print the first half. Each half has 16 boolean values. Encode each half as a
string. Test whether the character at index `i` is `x` and print the boolean
result. This solution is optimal, according to the game.

```
str = xxxxoxxxooxxooox;   // Pattern of each half.
loop:                     // Start of "loop".
    char = str[int];      // Character at index i.
    check char = x;       // Is character = x?
    output = bool;        // Print boolean result.
    int++;                // Increment the index.
    check int = 16;       // Printed 16 boolean values yet?
    jump if false: loop;  // If not, go to start of "loop".
int = 0;                  // Reset the character index.
```

## Solution 3

Directly print the pattern of the first 16 squares. Let the game implicitly loop
over the program to take care of the remaining squares. This solution is
optimal, according to the game.

```
output = true;  // Print the pattern xxxx.
output = true;
output = true;
output = true;
output = false;  // Print the pattern oxxx.
output = true;
output = true;
output = true;
output = false;  // Print the pattern ooxx.
output = false;
output = true;
output = true;
output = false;  // Print the pattern ooox.
output = false;
output = false;
output = true;
```
