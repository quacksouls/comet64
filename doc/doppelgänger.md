# The Doppelgänger

## Problem

Read the years, one at a time. A year can occur twice in a row. Print the
duplicate years.

{% youtube id="VVGZdgfGPNY", title="7. The doppelgänger, Comet 64" %}{% endyoutube %}

## Solution 1

The register `int` is initially zero. Assume this to be the case and read input
into the register `reg` only. We print only if two consecutive values from input
are the same. This solution does not use a loop.

```
reg = input;          // Read the year from input.
check int = reg;      // Are both values the same?
jump if true: print;  // If so, go to "print".
jump to: end;         // Go to "end".
print:                // The "print" branch.
    output = int;     // Print the duplicate year.
end:                  // The "end" branch.
    int = reg;        // Set current year to latest year.
```

## Solution 2

Similar to [Solution 1](#solution-1), but we use a loop. This solution is
optimal, according to the game.

```
loop:                     // Start of "loop".
    int = reg;            // Set current year to latest year.
    reg = input;          // Read a year from input.
    check int = reg;      // Are two year values the same?
    jump if false: loop;  // If not, go to "loop".
output = int;             // Print the duplicate year.
```

## Solution 3

Similar to [Solution 2](#solution-2), but we do not use an explicit loop. This
solution is optimal, according to the game.

```
reg = input;         // Read the year from input.
check int = reg;     // Are both values the same?
jump if false: end;  // If not, go to "end".
output = int;        // Print the duplicate year.
end:                 // The "end" branch.
    int = reg;       // Set current year to latest year.
```
