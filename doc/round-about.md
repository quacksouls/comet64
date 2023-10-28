# Round About

## Problem

Read a floating point number from input, round it to the nearest integer, and
print the result.

{% youtube id="flykIEB8mdA", title="9. Round about, Comet 64" %}{% endyoutube %}

## Solution 1

This solution exploits how floating point numbers are represented and handled in
the Comet 64 computer. The computer allows for up to two decimal digits
following the decimal point. If a floating point number cannot fit in the
representation used by the computer, then the third decimal digit is rounded.
The rounding rule is rounding half up. For example, the number 1.123 is rounded
to 1.12 and 1.125 is rounded to 1.13. To round an input number to the nearest
integer, we divide the input by 100 so the computer would round the result to
two decimal places. Then multiply the rounded number by 100 to obtain the
rounded integer. This solution is optimal, according to the game.

```
reg = input / 100;  // Divide by 100 to trigger rounding.
int = reg * 100;    // Multiply by 100 to get rounded integer.
output = int;       // Print the rounded integer.
```

## Solution 2

We are rounding half up, i.e. round half toward positive infinity. Define our
rounding function as

```
round(x) := floor(x + 0.5)
```

where we use the `floor()` function. The `floor(x)` function of a floating point
number `x` is equivalent to the integer part of `x`. This solution is optimal,
according to the game.

```
int = input + 0.5;  // The floor(x + 0.5) function.
output = int;       // Print the rounded integer.
```
