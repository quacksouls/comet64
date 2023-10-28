# Differentiator

## Problem

Calculate the absolute difference between two input values. If the difference is
greater than 5, print `true`, otherwise print `false`.

{% youtube id="nnGmhv6Strw", title="13. Differentiator, Comet 64" %}{% endyoutube %}

## Solution 1

If `a` and `b` are given numbers, we want to calculate the number

```
c := abs(a - b)
```

where `abs(x)` is the absolute value function. Print `true` if `c > 5`; print
`false` otherwise.

```
int = input;           // Read the first input.
int = input - int;     // Difference between two input values.
check int < 0;         // Is the difference negative?
jump if false: print;  // If non-negative, go to "print".
int = int * -1;        // Otherwise, convert to positive.
print:                 // The "print" branch.
    check int > 5;     // Is difference > 5?
    output = bool;     // Print the boolean result.
```

## Solution 2

If `a` and `b` are given numbers, we have the difference

```
d := a - b
```

The difference is greater than 5 provided that either of the following
conditions is true:

-   `d > 5`; or
-   `d < -5`

This solution is optimal, according to the game.

```
int = input - input;  // Difference between 2 input values.
check int > 5;        // Is difference > 5?
jump if true: print;  // If so, go to "print".
check int < -5;       // Is difference < -5?
print:                // The "print" branch.
    output = bool;    // Print the boolean result.
```

## Solution 3

If `a` and `b` are given numbers, we want to calculate the difference

```
d := a - b
```

We have three cases:

1. If the difference is `d := 5` or `d := -5`, then the square is `d^2 := 25`.
1. If `0 <= d < 5` or `-5 < d <= 0`, then `0 <= d^2 < 25`.
1. If `d > 5` or `d < -5`, then `d^2 > 25`.

We only need to test whether `d^2 > 25`. If true, then the difference is more
than 5 units. Otherwise, the difference is at most 5 units. This solution is
optimal, according to the game.

```
int = input - input;  // d := a - b
int = int * int;      // d^2
check int > 25;       // Is d^2 > 25?
output = bool;        // Print the boolean result.
```
