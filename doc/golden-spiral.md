# Golden Spiral

## Problem

Read a number from input and print the Fibonacci sequence up to, but not
exceeding, the number.

{% youtube id="XUpd2AmY1m4", title="20. Golden spiral, Comet 64" %}{% endyoutube %}

## Solution 1

Let `F_n` be the `n`-th Fibonacci number and let `phi` be the golden ratio:

```
phi := 1.618033988749...
```

Then the Fibonacci sequence follows the recurrence relation

```
F_{n+1} := floor(phi*F_n + 0.5)
```

where `floor(x)` is the floor function. See

https://mathworld.wolfram.com/FibonacciNumber.html

Essentially, we are rounding `phi*F_n` to the nearest integer, where the
rounding rule is "round half up", also known as "round half toward positive
infinity". This solution is optimal, according to the game.

```
int = input;              // Read the max value.
reg = 1;                  // First Fibonacci number F_0.
output = reg;             // Print F_0.
loop:                     // Start of "loop".
    output = reg;         // Print F_n.
    reg = reg * 1.618;    // phi * F_n
    switch int;           // Store max value.
    int = reg + 0.5;      // F_{n+1} := floor(phi*F_n + 0.5)
    reg = int;            // Copy result to register "reg".
    switch int;           // Retrieve max value.
    check reg > int;      // Is F_{n+1} > max value?
    jump if false: loop;  // If not, go to "loop".
```

## Solution 2

Similar to [Solution 1](#solution-1). However, instead of using the `floor(x)`
function for rounding, we exploit how floating point numbers are rounded by the
game. Given a number having at least 3 decimal places, the game rounds the
floating point number to 2 decimal places. The rounding rule is "round half up"
or "round half toward positive infinity". To exploit this behaviour, we multiply
`F_n` by `phi/100`, then multiply the result by 100 to obtain `F_{n+1}`. This
solution is optimal, according to the game.

```
int = input;              // Read the max value.
reg = 1;                  // First Fibonacci number F_0.
output = reg;             // Print F_0.
loop:                     // Start of "loop".
    output = reg;         // Print F_n.
    reg = reg * 0.0162;   // f := (phi/100) * F_n
    reg = reg * 100;      // F_{n+1} := 100*f
    check reg > int;      // Is F_{n+1} > max value?
    jump if false: loop;  // If not, go to "loop".
```
