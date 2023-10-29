# Black Jack

## Problem

Input contains a sequence of integers that represent values of a deck of cards.
Read an input and add it to the previous input. Print the new sum if it is as
close to 21 as possible, while being at most 21.

{% youtube id="6o9pawhhSxU", title="24. Black jack, Comet 64" %}{% endyoutube %}

## Solution 1

Let the register `int` store the cumulative sum. Assume the register initially
holds zero. We read a value into `reg`, update the cumulative sum

```
int := reg + int
```

and determine whether the updated cumulative sum is greater than 21. If the
value of `int` is at most 21, read in the next value. Otherwise, the value of
`int` is greater than 21 and we know that the newly read input value contributes
to this updated sum. Revert to the previous value of `int` and print the
previous value. Finally, assign the new input value to `int`. Continue the above
process until we have no more values to read, at which point we simply print
whatever value is held in `int`.

```
loop:                     // Start of "loop".
    check input = null;   // Any more numbers?
    jump if true: end;    // If no more, go to "end".
    reg = input;          // Otherwise, read next value.
    int = reg + int;      // Update cumulative sum.
    check int > 21;       // Is sum > 21?
    jump if false: loop;  // If not, go to "loop".
    int = int - reg;      // Otherwise, use previous value.
    output = int;         // Print the previous value.
    int = reg;            // Now start with current input.
    jump to: loop;        // Go to "loop".
end:                      // The "end" branch.
    output = int;         // Print whatever is in "int".
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we remove a jump instruction and
use only one print statement. This solution is optimal, according to the game.

```
loop:                     // Start of "loop".
    check input = null;   // Any more numbers?
    jump if true: print;  // If no more, go to "print".
    reg = input;          // Otherwise, read next value.
    int = reg + int;      // Update cumulative sum.
    check int > 21;       // Is sum > 21?
    jump if false: loop;  // If not, go to "loop".
    int = int - reg;      // Otherwise, use previous value.
print:                    // The "print" branch.
    output = int;         // Print whatever is in "int".
    int = reg;            // Now start with current input.
```
