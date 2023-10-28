# Some Leftovers

## Problem

Divide an integer by 4. Print the integer if the remainder is 3.

{% youtube id="4_AGDdFKksI", title="12. Some leftovers, Comet 64" %}{% endyoutube %}

## Solution 1

Assume the input number `x` is at least 4. Let `x := x - 4`. If the result is
less than 4, we have the remainder. Otherwise, repeat the subtraction process.
Given the remainder, determine whether it is 3. If so, print the original
integer.

```
reg = input;                  // Read in x.
int = reg;                    // x
subtract:                     // The "subtract" branch.
    int = int - 4;            // x := x - 4
    check int < 4;            // Is x < 4?
    jump if false: subtract;  // If not, go to "subtract".
check int = 3;                // Is remainder = 3?
jump if false: end;           // If not, go to "end".
output = reg;                 // Print the original number.
end:                          // End of program.
```

## Solution 2

Given an input `x`, we print `x` if it has a remainder of 3 after division by 4.
The remainder function is

```
f(x) := x mod 4
```

This can be implemented as follows. Define the quotient by

```
q := floor(x / 4)
```

where the `floor(x)` function is simply the integer part of a floating point
number `x`. Define the number

```
n := 4 * q
```

and the remainder can be calculated as `r := x - n`. This solution is optimal,
according to the game.

```
reg = input;         // Read in x.
int = reg / 4;       // The quotient q := floor(x / 4).
int = 4 * int;       // The number n := 4 * q.
int = reg - int;     // The remainder r := x - n.
check int = 3;       // Is the remainder = 3?
jump if false: end;  // If not, go to "end".
output = reg;        // Print x.
end:                 // End of program.
```
