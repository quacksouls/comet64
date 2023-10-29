# Give me a Ballpark

## Problem

Calculate the arithmetic mean of a bunch of numbers.

{% youtube id="U9g_07uBVss", title="23. Give me a ballpark, Comet 64" %}{% endyoutube %}

## Solution 1

We assume that each of the registers `int` and `reg` is initially set to zero.
Read a number from input and keep track of the cumulative sum. We also keep
track of how many numbers we have read so far. If there are no more input
values, calculate and print the average.

```
int++;                // How many numbers read so far.
reg = reg + input;    // The cumulative sum.
check input = null;   // Any more numbers?
jump if true: print;  // If not, go to "print".
jump to: end;         // Otherwise, go to "end".
print:                // The "print" branch.
    reg = reg / int;  // The arithmetic mean.
    output = reg;     // Print the average.
end:                  // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1), but we use an explicit loop. We remove a
jump instruction and a label. This solution is optimal, according to the game.

```
loop:                     // Start of "loop".
    int++;                // How many numbers read so far.
    reg = reg + input;    // The cumulative sum.
    check input = null;   // Any more numbers?
    jump if false: loop;  // If yes, go to "loop".
reg = reg / int;          // The arithmetic mean.
output = reg;             // Print the average.
```
