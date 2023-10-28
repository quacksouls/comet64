# Doppelgänger 2

## Problem

Read two consecutive strings from input. If they are the same, print `true`.
Otherwise, print `false`.

{% youtube id="XW0SOw5PySs", title="15. Doppelgänger 2, Comet 64" %}{% endyoutube %}

## Solution 1

Read in a string. Check whether this string is the same as the next string.

```
str = input;        // Read an input string.
check str = input;  // Is current string same as new input?
output = bool;      // Print the result of comparison.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we do not need to read the first
string. This solution is optimal, according to the game.

```
check input = input;  // Is current input same as new input?
output = bool;        // Print the result of comparison.
```
