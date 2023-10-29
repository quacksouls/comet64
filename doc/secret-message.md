# Secret Message

## Problem

Read a string from input. Replace each occurrence of `g` with `e`. Print the
modified string.

{% youtube id="_lwYg48HXks", title="33. Secret message, Comet 64" %}{% endyoutube %}

## Solution 1

Iterate over each character of a string. Replace each occurrence of `g` with an
`e`. Start from the first character and work upward to the last character.

```
str = input;                // Read the input string.
reg = str.length - 1;       // Index of last character.
int = 0;                    // Index of i-th character.
loop:                       // Start of "loop".
    check int > reg;        // Is index > last index?
    jump if true: print;    // If so, go to "print".
    char = str[int];        // The i-th character.
    check char = g;         // Is character = g?
    jump if true: replace;  // If so, go to "replace".
    int++;                  // Otherwise, increment index.
    jump to: loop;          // Go to "loop".
replace:                    // The "replace" branch.
    char = e;               // The character "e".
    str[int] = char;        // Replace i-th character with "e".
    int++;                  // Increment the index.
    jump to: loop;          // Go to "loop".
print:                      // The "print" branch.
    output = str;           // Print the possibly new string.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we start from the last character
and work downward to the first character. This solution is optimal, according to
the game.

```
str = input;                // Read the input string.
int = str.length - 1;       // Index of last character.
loop:                       // Start of "loop".
    check int < 0;          // Is index < 0?
    jump if true: print;    // If so, go to "print".
    char = str[int];        // The i-th character.
    check char = g;         // Is character = g?
    jump if true: replace;  // If so, go to "replace".
    int--;                  // Decrement the index.
    jump to: loop;          // Go to "loop".
replace:                    // The "replace" branch.
    char = e;               // The character "e".
    str[int] = char;        // Replace i-th character with "e".
    int--;                  // Decrement the index.
    jump to: loop;          // Go to "loop".
print:                      // The "print" branch.
    output = str;           // Print the possibly new string.
```

## Solution 3

Similar to [Solution 2](#solution-2). However, we remove a jump instruction and
a label. This solution is optimal, according to the game.

```
str = input;              // Read the input string.
int = str.length;         // How many characters in string.
loop:                     // Start of "loop".
    int--;                // Decrement the index.
    check int < 0;        // Is index < 0?
    jump if true: print;  // If so, go to "print".
    char = str[int];      // The i-th character.
    check char = g;       // Is character = g?
    jump if false: loop;  // If not, go to "loop".
    char = e;             // The character "e".
    str[int] = char;      // Replace i-th character with "e".
    jump to: loop;        // Go to "loop".
print:                    // The "print" branch.
    output = str;         // Print the possibly new string.
```
