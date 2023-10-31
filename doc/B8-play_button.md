# B8: play_button

## Problem

Print the pattern:

```
#OOO
##OO
###O
####
####
###O
##OO
#OOO
```

{% youtube id="ozy--5ulKf8", title="59. B8: play_button & B9: hiroshima, Comet 64" %}{% endyoutube %}

## Solution

Use a string to encode the pattern. Check whether the character at index `i` is
`x` and print the boolean result. This solution is optimal, according to the
game.

```
str = xoooxxooxxxoxxxxxxxxxxxoxxooxooo;  // Encoded pattern.
char = str[int];  // Character at index i.
check char = x;   // Is character = x?
output = bool;    // Print boolean result.
int++;            // Increment index.
```
