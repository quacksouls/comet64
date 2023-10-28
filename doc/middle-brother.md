# Middle Brother

## Problem

Read three numbers in a row and print the median.

{% youtube id="f-WLm_SAXLM", title="18. Middle brother, Comet 64" %}{% endyoutube %}

## Solution 1

Let `x`, `y`, `z` be three numbers. We have these cases:

1. `x < y` and `y < z`, so middle is `y`.
1. `x < y`, `z <= y`, `x < z`, so middle is `z`.
1. `x < y`, `z <= y`, `z <= x`, so middle is `x`.
1. `y <= x` and `x < z`, so middle is `x`.
1. `y <= x`, `z <= x`, `y < z`, so middle is `z`.
1. `y <= x`, `z <= x`, `z <= y`, so middle is `y`.

```
int = input;              // Read in x.
reg = input;              // Read in y.
check int < reg;          // Is x < y?
jump if false: yltx;      // If not, then y <= x.
switch int;               // Store x.
int = input;              // Read in z.
check reg < int;          // Is y < z?
jump if false: zlty;      // If not, then z <= y.
output = reg;             // Case (1), y middle.
jump to: end;             // Go to "end".
yltx:                     // y <= x
    switch reg;           // Store y.
    reg = input;          // Read in z.
    check int < reg;      // Is x < z?
    jump if true: xltz;   // If so, then x < z.
    switch int;           // Retrieve y.
    check int < reg;      // Is y < z?
    jump if true: yltz;   // If so, then y < z.
    output = int;         // Case (6), y middle.
    jump to: end;         // Go to "end".
zlty:                     // z <= y
    switch reg;           // Retrieve x.
    check reg < int;      // Is x < z?
    jump if false: zltx;  // If not, then z <= x.
    output = int;         // Case (2), z middle.
    jump to: end;         // Go to "end".
zltx:                     // z <= x
    output = reg;         // Case (3), x middle.
    jump to: end;         // Go to "end".
xltz:                     // x < z
    output = int;         // Case (4), x middle.
    jump to: end;         // Go to "end".
yltz:                     // y < z
    output = reg;         // Case (5), z middle.
end:                      // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1). Notice the symmetry between the cases of
`x < y` and `y <= x`. Let the registers `int` and `reg` hold the values of `x`
and `y`, respectively. If `x < y`, we proceed with cases (1) to (3) as per
[Solution 1](#solution-1). Otherwise `y <= x`, we swap the values of `int` and
`reg`, and proceed as per cases (1) to (3).

```
int = input;                // Read in x.
reg = input;                // Read in y.
check int < reg;            // Is x < y?
jump if true: less;         // If so, go to "less".
switch int;                 // Store x.
int = reg;                  // int := reg
switch reg;                 // Retrieve x.
less:                       // x < y
    switch int;             // Store value of min(x, y).
    int = input;            // Read in z.
    check reg < int;        // Is y < z?
    jump if true: ymiddle;  // If so, go to "ymiddle".
    switch reg;             // Retrieve value of min(x, y).
    check reg < int;        // Is min(x, y) < z?
    jump if true: zmiddle;  // If so, go to "zmiddle".
    output = reg;           // Otherwise, print x.
    jump to: end;           // Go to "end".
ymiddle:                    // The "ymiddle" branch.
    output = reg;           // Print y.
    jump to: end;           // Go to "end".
zmiddle:                    // The "zmiddle" branch.
    output = int;           // Print z.
end:                        // End of program.
```

## Solution 3

Similar to [Solution 2](#solution-2). However, we remove a few unnecessary
lines. Try to always have `reg` store the middle value. This solution is
optimal, according to the game.

```
int = input;              // Read in x.
reg = input;              // Read in y.
check int < reg;          // Is x < y?
jump if true: less;       // If so, go to "less".
switch int;               // Store x.
int = reg;                // int := reg
switch reg;               // Retrieve x.
less:                     // x < y
    switch int;           // Store value of min(x, y).
    int = input;          // Read in z.
    check reg < int;      // Is y < z?
    jump if true: print;  // If so, go to "print".
    switch reg;           // Retrieve value of min(x, y).
    check reg > int;      // Is min(x, y) > z?
    jump if true: print;  // If so, go to "print".
    reg = int;            // z := x
print:                    // The "print" branch.
    output = reg;         // Print the middle value.
```
