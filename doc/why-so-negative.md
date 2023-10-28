# Why so Negative?

## Problem

Each number from input is negative. Remove the negative sign and print the
result.

{% youtube id="aXWiBq33P84", title="2. Why so negative?, Comet 64" %}{% endyoutube %}

## Solution 1

Any non-zero number multiplied by -1 would have the opposite sign. Given a
negative number, multiplying the number by -1 would result in a positive number.
We can rule out the possibility of an input being zero because the problem
states that each input is a negative number.

```
int = -1;         // Store -1 in a register.
reg = input;      // Read an input number.
reg = reg * int;  // Multiply number by -1.
output = reg;     // Print the result.
```

## Solution 2

Similar to [Solution 1](#solution-1). There is no need to store -1 in the
register `int`. We can directly multiply the input by -1. This solution is
optimal, according to the game.

```
reg = input * -1;  // Multiply input number by -1.
output = reg;      // Print the result.
```
