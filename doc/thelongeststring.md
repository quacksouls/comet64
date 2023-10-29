# thelongeststring

## Problem

Find the longest string.

{% youtube id="msnVeASEY2g", title="27. thelongeststring, Comet 64" %}{% endyoutube %}

## Solution 1

Read a string from input and determine its length. If the length of the new
string is less than the length of the longest string so far, then read the next
string. Otherwise, the length of the new string is at least the length of the
longest string so far. Set the longest string (so far) to the newly read string
and read the next string. If there are no more strings from input, print the
longest string. Use the register `reg` to hold the length of the longest string
so far.

```
check input = null;      // Any more strings?
jump if true: print;     // If no more, go to "print".
jump if false: compare;  // Otherwise, go to "compare".
compare:                 // The "compare" branch.
    str = input;         // Read an input string.
    int = str.length;    // How many characters in the string.
    check reg < int;     // New string has more characters?
    jump if false: end;  // If not, go to "end".
    reg = int;           // Otherwise, note the larger length.
    switch str;          // Store the new string.
    jump to: end;        // Go to "end".
print:                   // The "print" branch.
    switch str;          // Retrieve the longest string.
    output = str;        // Print the longest string.
end:                     // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we remove a jump instruction and
a label. We also add an explicit loop. This solution is optimal, according to
the game.

```
loop:
    check input = null;   // Any more strings?
    jump if true: print;  // If not, go to "print".
    str = input;          // Read the input string.
    int = str.length;     // How many characters in the string.
    check reg < int;      // New string has more characters?
    jump if false: loop;  // If not, go to "end".
    reg = int;            // Otherwise, note larger length.
    switch str;           // Store the new string.
    jump to: loop;        // Go to "loop".
print:                    // The "print" branch.
    switch str;           // Retrieve the longest string.
    output = str;         // Print the longest string.
```
