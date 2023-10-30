# No Duplicates!

## Problem

Read 5 random one-digit numbers. Exactly one of the numbers appears twice. Find
and print the duplicate number.

{% youtube id="D5eTnyPvcX8", title="39. No duplicates!, Comet 64" %}{% endyoutube %}

## Solution

Reuse the array solution to the problem [No Duplicates!](./no-duplicates-1.md).

```
str = oooooooooo;         // Array of 10 elements.
loop:                     // Start of "loop".
    int = input;          // Read a one-digit integer i.
    char = str[int];      // Character at index i of string.
    check char = x;       // Is character = x?
    jump if true: print;  // If so, go to "print".
    char = x;             // Otherwise, have not seen i yet.
    str[int] = char;      // Set character to x.
    jump to: loop;        // Go to "loop".
print:                    // The "print" branch.
    output = int;         // Print the duplicate integer.
```
