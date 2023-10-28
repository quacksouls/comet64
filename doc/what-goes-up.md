# What Goes Up

## Problem

Print all integers from 1 to 100, inclusive.

{% youtube id="CvHgKJV3Jw0", title="4. What goes up, Comet 64" %}{% endyoutube %}

## Solution 1

We need to output all integers from 1 to 100, inclusive. In a high-level
programming language, we would typically use a loop as follows.

```
int = 1;                 // Start at 1.
loop:                    // Start of "loop".
    output = int;        // Print the integer.
    int++;               // Increment the current integer.
    check int < 101;     // Is integer < 101?
    jump if true: loop;  // If so, go to "loop".
    jump if false: end;  // Otherwise, go to "end".
end:                     // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1). We can shave off a few lines by noticing
that, from the previous solution, the last two lines are not necessary. If the
loop conditional is false, then we automatically exit the loop and reach the end
of the program. Also note that we do not need a loop conditional. Use a loop to
print as many integers as necessary. Once the game detects we have output the
required number of integers, the program ends.

```
int = 1;            // Start at 1.
loop:               // Start of "loop".
    output = int;   // Print the integer.
    int++;          // Increment the integer.
    jump to: loop;  // Go to "loop".
```

## Solution 3

Suppose we want to use 2 lines to output all integers from 1 to 100, inclusive.
The register `int` is initially zero. Incrementing that register would give us 1
and we can output that value. Continue incrementing and outputting until we have
output all required integers. This solution is optimal, according to the game.

```
int++;         // Increment the integer.
output = int;  // Print the integer.
```
