# Any Leftovers?

## Problem

Divide a number by 4 and print the remainder.

{% youtube id="ChQPZRgUQn0", title="11. Any leftovers, Comet 64" %}{% endyoutube %}

## Solution 1

Assume the input number `x` is at least 4. Let `x := x - 4`. If the result is
less than 4, we have the remainder. Otherwise, repeat the subtraction process.

```
int = input;                  // Read in x.
subtract:                     // The "subtract" branch.
    int = int - 4;            // x := x - 4
    check int < 4;            // Is x < 4?
    jump if false: subtract;  // If not, go to "subtract".
output = int;                 // Print the remainder.
```

## Solution 2

Given an input `x`, we want the remainder when `x` is divided by 4. The
remainder function is

```
f(x) := x mod 4
```

This can be implemented as follows. Define the quotient by

```
q := floor(x / 4)
```

where the `floor(x)` function is simply the integer part of a floating point
number `x`. Define the

```
n := 4 * q
```

and the remainder can be calculated as

```
r := x - n
```

This solution is optimal, according to the game.

```
reg = input;      // Read number x.
int = reg / 4;    // The quotient q := floor(x / 4).
int = 4 * int;    // The number n := 4 * q.
int = reg - int;  // The remainder r := x - n.
output = int;     // Print the remainder.
```
