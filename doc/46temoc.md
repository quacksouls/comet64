# 46temoc

## Problem

Reverse each input string.

{% youtube id="m6yUICS6nl8", title="28. 46temoc, Comet 64" %}{% endyoutube %}

## Solution 1

Let `n` be the number of characters in the input string. We reverse the string
in-place because we have only one string variable. Let `l` be the index of the
left character and let `r` be the index of the right character. Initially,
`l := 0` and the left character is the first character of the string.
Furthermore, `r := n - 1` and the right character is initially the last
character of the string. Interchange the left and right characters. Then
increment `l` by one and decrement `r` by one. Repeat the above process until
`l >= r`, at which point we print the reversed string.

```
str = input;               // Read the input string.
int = 0;                   // The left index.
reg = str.length - 1;      // The right index.
loop:                      // Start of "loop".
    check int < reg;       // Is left < right?
    jump if false: print;  // If left >= right, go to "print".
    char = str[int];       // The left character.
    switch char;           // Store the character in memory.
    char = str[reg];       // The right character.
    str[int] = char;       // Left index has right character.
    switch char;           // Retrieve the left character.
    str[reg] = char;       // Right index has left character.
    int++;                 // Increment left index.
    reg--;                 // Decrement right index.
    jump to: loop;         // Go to "loop".
print:                     // The "print" branch.
    output = str;          // Print the reversed string.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we remove a jump instruction and
move the index check to the end of the loop.

```
str = input;             // Read the input string.
int = 0;                 // The left index.
reg = str.length - 1;    // The right index.
loop:                    // Start of "loop".
    char = str[int];     // The left character.
    switch char;         // Store the character in memory.
    char = str[reg];     // The right character.
    str[int] = char;     // Left index has right character.
    switch char;         // Retrieve the left character.
    str[reg] = char;     // Right index has left character.
    int++;               // Increment left index.
    reg--;               // Decrement right index.
    check int < reg;     // Is left < right?
    jump if true: loop;  // If so, go to "loop".
output = str;            // Print the reversed string.
```

## Solution 3

Use the command `switch` to interchange the contents of the register `str` and
the switch box. If the switch box has a non-empty string and the register `str`
also contains a non-empty string, then the command `switch str` would move the
content of `str` to the switch box and the previous content of the switch box
would now be in `str`. Use the switch box as a temporary string variable.
Traverse the input string from the last character down to the first character.
Use the switch box to build the string backward. This solution is optimal,
according to the game.

```
str = input;              // Read the input string.
int = str.length - 1;     // Index of last character.
loop:                     // Start of "loop".
    char = str[int];      // Character at index i.
    switch str;           // Interchange str and box.
    str = str + char;     // Append character to new string.
    switch str;           // Interchange str and box.
    int--;                // Decrement the index i.
    check int = -1;       // Is index = -1?
    jump if false: loop;  // If not, go to "loop".
switch str;               // Get the reversed string.
switch null;              // Clear the switch box.
output = str;             // Print the reversed string.
```
