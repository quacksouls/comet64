# Big Brother

## Problem

Read three numbers in a row and determine the maximum.

{% youtube id="Ui2op5uZt4g", title="17. Big brother, Comet 64" %}{% endyoutube %}

## Solution 1

Let `x`, `y`, `z` be three numbers read in a row. We have these cases:

1. `x < y` and `y < z`, so `max = z`
1. `x < y` and `z <= y`, so `max = y`
1. `y <= x` and `x < z`, so `max = z`
1. `y <= x` and `z <= x`, so `max = x`

```
int = input;             // Read in x.
reg = input;             // Read in y.
check int < reg;         // Is x < y?
jump if false: ylessx;   // If not, go to "ylessx".
int = input;             // Read in z.
check reg < int;         // Is y < z?
jump if true: zmax;      // If so, go to "zmax".
output = reg;            // Otherwise, y is maximum.
jump to: end;            // Go to "end".
ylessx:                  // y <= x
    reg = int;           // Set x := y.
    int = input;         // Read in z.
    check reg < int;     // Is x < z?
    jump if true: zmax;  // If so, go to "zmax".
    output = reg;        // Otherwise, print x.
    jump to: end;        // Go to "end".
zmax:                    // Maximum is z.
    output = int;        // Print z.
end:                     // End of program.
```

## Solution 2

Let `x`, `y`, `z` be three numbers read in a row. Let the registers `int` and
`reg` hold the values of `x` and `y`, respectively. Note the symmetry between
`x < y` and `y <= x`. In the cases from [Solution 1](#solution-1), consider the
symmetry between cases (1) and (2), and cases (3) and (4). If `x < y`, use `int`
to store the value of `z`. If `y <= x`, we set `reg := int` and use `int` to
store the value of `z`. In both cases, `reg := max(x, y)`. This solution is
optimal, according to the game.

```
int = input;              // Read in x.
reg = input;              // Read in y.
check int < reg;          // Is x < y?
jump if true: less;       // If so, go to "less".
reg = int;                // Otherwise, set reg := int.
less:                     // The "less" branch.
    int = input;          // Read in z.
    check int < reg;      // Is z < max(x, y)?
    jump if true: print;  // If so, go to "print".
    reg = int;            // The max of all 3 numbers.
print:                    // The "print" branch.
    output = reg;         // Print the maximum.
```
