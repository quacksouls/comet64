# Just Around

## Problem

Round each integer to the nearest tens.

{% youtube id="hFxiiWRX3kM", title="10. Just around, Comet 64" %}{% endyoutube %}

## Solution 1

To round a floating point number to the nearest tens, we divide the number by 10
and treat the problem as if we are rounding the number to the nearest integer.
Then multiply the result by 10 to obtain the desired number. The algorithm for
rounding to the nearest integer is

```
round(x) := floor(x + 0.5)
```

where the `floor(x)` function of `x` is the same as the integer part of a
floating point number `x`. This solution is optimal, according to the game.

```
reg = input / 10;  // Divide the input by 10.
int = reg + 0.5;   // floor(x + 0.5)
int = int * 10;    // Multiply by 10 to undo division.
output = int;      // Print the result.
```

## Solution 2

This solution exploits how floating point numbers are represented and handled in
the Comet 64 computer. The computer allows for up to two decimal digits
following the decimal point. If a floating point number cannot fit in the
representation used by the computer, then the third decimal digit is rounded.
The rounding rule is rounding half up. For example, the number 1.123 is rounded
to 1.12 and 1.125 is rounded to 1.13. To round an input number to the nearest
tens, we divide the input by 1000 so the computer would round the result to two
decimal places. Then multiply the rounded number by 1000 to obtain the integer
rounded to the nearest tens. This solution is optimal, according to the game.

```
reg = input / 1000;  // Round to 2 decimal places.
int = reg * 1000;    // Integer rounded to nearest tens.
output = int;        // Print rounded number.
```
