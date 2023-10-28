# Sum'bich

## Problem

A stream of integers is partitioned into packages. The end of a package is
marked by the integer zero. Print the sum of each package.

{% youtube id="j7to2ZCeFO0", title="8. Sum bich, Comet 64" %}{% endyoutube %}

## Solution 1

Assume that the register `reg` is initially zero so no need to set it to zero.
Use an if-else structure. This solution is optimal, according to the game.

```
int = input;          // Read the input number.
reg = reg + int;      // Update the cumulative sum.
check int = 0;        // Is the current input = 0?
jump if true: print;  // If so, go to "print".
jump if false: end;   // Otherwise, go to "end".
print:                // The "print" branch.
    output = reg;     // Print the cumulative sum.
    reg = 0;          // Set cumulative sum to zero.
end:                  // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1). We remove an explicit jump if the
conditional is true. This solution is optimal, according to the game.

```
int = input;         // Read the input number.
reg = reg + int;     // Update the cumulative sum.
check int = 0;       // Is the current input = 0?
jump if false: end;  // If not, go to "end".
output = reg;        // Print the cumulative sum.
reg = 0;             // Set "reg" to zero.
end:                 // End of program.
```
