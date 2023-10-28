# Easier Than It Looks

## Problem

Read an integer `x` from input and print the number `x * (x - 1)`.

{% youtube id="qw5tnvLDkmU", title="21. Easier than it looks, Comet 64" %}{% endyoutube %}

## Solution

Given an integer `x`, calculate `x * (x - 1)`. This solution is optimal,
according to the game.

```
int = input;      // Read the integer x.
reg = int - 1;    // x - 1
int = int * reg;  // x * (x - 1)
output = int;     // Print result.
```
