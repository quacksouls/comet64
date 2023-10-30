# A1: full_on

## Problem

Print the following grid pattern:

```
####
####
####
####
####
####
####
####
```

{% youtube id="Fj6ISUvILEw", title="41. A1: full_on, Comet 64" %}{% endyoutube %}

## Solution 1

Make these definitions:

```
x := shaded
o : unshaded
```

Encode the pattern as a string. Check each character of the string and print the
boolean result.

```
str = xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx;  // Encoded pattern.
loop:                 // Start of "loop".
    char = str[int];  // Character i.
    check char = x;   // Is character i = x?
    output = bool;    // Print boolean value.
    int++;            // Increment index i.
    jump to: loop;    // Go to "loop".
```

## Solution 2

Each cell in the grid is shaded. All we need to do is output `true`. This
solution is optimal, according to the game.

```
output = true;
```
