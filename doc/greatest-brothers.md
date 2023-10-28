# Greatest of Brothers

## Problem

Determine the maximum of a bunch of numbers.

{% youtube id="Rr5B2i9_Sg8", title="19. Greatest of brothers, Comet 64" %}{% endyoutube %}

## Solution 1

Read in the first value because all the integers might be negative. Cannot
assume that all numbers are positive, hence cannot use the initial value of
`int` as zero. Compare the running maximum to the current input. If the running
maximum is less than the current input, then we have found a new running
maximum. Otherwise read the next input.

```
int = input;               // The current maximum.
loop:                      // Start of loop.
    check input = null;    // No more numbers?
    jump if true: print;   // If so, go to "print".
    reg = input;           // Read the next number
    check int < reg;       // Is current max < input?
    jump if true: newMax;  // If so, go to "newMax".
    jump to: loop;         // Otherwise, go to "loop".
print:                     // The "print" branch.
    output = int;          // Print the running maximum.
newMax:                    // The "newMax" branch.
    int = reg;             // The new maximum value.
    jump to: loop;         // Go to "loop".
```

## Solution 2

Similar to [Solution 1](#solution-1), but we remove a jump instruction.

```
int = input;              // The running maximum.
loop:                     // Start of "loop".
    check input = null;   // No more numbers?
    jump if true: print;  // If so, go to "print".
    reg = input;          // Read the next number.
    check int < reg;      // Is current max < input?
    jump if false: loop;  // If not, go to "loop".
    int = reg;            // The new maximum value.
    jump to: loop;        // Go to "loop".
print:                    // The "print" branch.
    output = int;         // Print the running maximum.
```

## Solution 3

Similar to [Solution 2](#solution-2), but we remove a jump instruction. Only
peek at the next input value after we have updated the current maximum. This
solution is optimal, according to the game.

```
int = input;              // Current maximum.
loop:                     // Start of "loop".
    reg = input;          // Read the next number.
    check int < reg;      // Is current max < input?
    jump if false: peek;  // If not, go to "peek".
    int = reg;            // Otherwise, update the maximum.
peek:                     // The "peek" branch.
    check input = null;   // No more numbers?
    jump if false: loop;  // If still more, go to "loop".
output = int;             // Print the running maximum.
```
