# Negative Initiative

## Problem

A sequence of numbers is organized as packages, where the end of a package is
delimited by 0. Print the first negative number in each package. If a package
does not have negative numbers, print 0.

{% youtube id="n8_Y9TwufVk", title="35. Negative initiative, Comet 64" %}{% endyoutube %}

## Solution 1

Given a number `n`, we have these cases:

1. If `n < 0`, then we print `n`. Read all remaining numbers in the package,
   including the zero that delimits the end of the package, and ignore those
   numbers.
1. If `n = 0`, we have reached the end of a package without finding a negative
   number in the package. Print 0.

```
reg = input;              // Read a number n.
check reg < 0;            // Is n < 0?
jump if true: print;      // If so, go to "print".
check reg = 0;            // Is n = 0?
jump if true: zero;       // If so, go to "zero".
jump to: end;             // Go to "end" branch.
zero:                     // The "zero" branch.
    output = 0;           // Print zero.
    jump to: end;         // Go to "end" branch.
print:                    // The "print" branch.
    output = reg;         // Print the first negative number.
loop:                     // Start of "loop".
    reg = input;          // Read input number.
    check reg = 0;        // Is number = 0?
    jump if false: loop;  // If not, go to "loop".
end:                      // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we removed a jump instruction and
removed a label. This solution is optimal, according to the game.

```
reg = input;              // Read a number n.
check reg < 0;            // Is n < 0?
jump if true: print;      // If so, go to "print".
check reg = 0;            // Is number = 0?
jump if false: end;       // If not, go to "end".
output = 0;               // Print zero.
jump to: end;             // Go to "end".
print:                    // The "print" branch.
    output = reg;         // Print the first negative number.
loop:                     // Start of "loop".
    reg = input;          // Read input number.
    check reg = 0;        // Is number = 0?
    jump if false: loop;  // If not, go to "loop".
end:                      // End of program.
```
