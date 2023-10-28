# Must Come Down

## Problem

Print all integers starting from 100 and count down to 0. The count should
include both 100 and 0.

{% youtube id="FAprn3pgWYg", title="5. Must come down, Comet 64" %}{% endyoutube %}

## Solution 1

This solution is straightforward. We start at 100. Use a loop to print the
current integer, then decrement the integer. Exit the loop when the integer is
negative.

```
int = 100;                // Start at 100.
loop:                     // Start of "loop".
    output = int;         // Print the integer.
    int--;                // Decrement the integer by 1.
    check int < 0;        // Is integer < 0?
    jump if true: end;    // If so, go to "end".
    jump if false: loop;  // Otherwise, go to "loop".
end:                      // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we keep on printing integers to
output. The program stops as soon as the game detects we have printed the
required number of integers. This solution is optimal, according to the game.

```
int = 100;          // Start at 100.
loop:               // Start of "loop".
    output = int;   // Print the integer.
    int--;          // Decrement the integer by 1.
    jump to: loop;  // Go to "loop".
```

## Solution 3

The register `int` is initially zero. Subtract the content of `int` from 100,
which yields the next integer to be printed. Increment the content of `int`. We
do not need an explicit loop because the game loops back to the start of the
program once it has read the last line of code. This solution is optimal,
according to the game.

```
reg = 100 - int;  // Subtract content of int from 100.
output = reg;     // Print the result of the subtraction.
int++;            // Increment int.
```
