# 46cemot

## Problem

Input contains a bunch of strings. Sort each string in alphabetical order and
print the sorted string.

{% youtube id="qhf3ceO3J80", title="29. 46cemot, Comet 64" %}{% endyoutube %}

## Solution 1

We use a variation of bubble sort:

https://en.wikipedia.org/wiki/Bubble_sort

Compare two adjacent characters in a string `S`. If the characters are not in
lexicographic order, then swap the characters. Otherwise, move to the next pair
of characters. Let `i` be the index of the left character in `S`. Initially
`i := 0`. The index of the right character is `i + 1`. Let `j` be the integer
representation of the character at index `i` and `k` the integer representation
of the character at index `i + 1`. If `j <= k`, then set `i := i + 1` and go on
comparing. Otherwise `j > k` so we interchange the two characters at indices `i`
and `i + 1`, set `i := 0`, and compare characters starting from the beginning of
`S`. Note that if two adjacent characters in `S` are not in lexicographic order,
we can find a smallest index `i` such that the characters at indices `i` and
`i + 1` can be swapped with each other. However, if the characters in `S` are in
lexicographic order, then eventually the value of `i` is the same as the maximum
index of `S`. At this point, `i` is the last index of `S`, the index `i + 1` is
out of bound, hence `S` is sorted in lexicographic order.

```
str = input;               // Read a string S.
int = 0;                   // Index i of left character.
loop:                      // Start of "loop".
    reg = str.length - 1;  // Index of last character.
    check int < reg;       // Is i < max index?
    jump if false: print;  // If not, go to "print".
    char = str[int];       // Left character.
    reg = int + 1;         // Index i + 1 of right character.
    switch int;            // Store index i in memory.
    int = char;            // Left character as integer.
    char = str[reg];       // Right character.
    reg = char;            // Right character as integer.
    check int > reg;       // Is left char > right char?
    jump if true: swap;    // If so, go to "swap".
    switch int;            // Retrieve index i.
    int++;                 // Increment index i.
    jump to: loop;         // Go to "loop".
swap:                      // The "swap" branch.
    switch int;            // Get index i; store left char.
    str[int] = char;       // Right char at left index.
    reg = int + 1;         // Index of right char.
    switch int;            // Get left char; store index i.
    char = int;            // Left char as character.
    str[reg] = char;       // Left char at right index.
    int = 0;               // Set i := 0.
    jump to: loop;         // Go to "loop".
print:                     // The "print" branch.
    output = str;          // Print the sorted string.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, instead of going from the first
character up to the last character of the string `S`, we traverse `S` from the
last character down to the first character. This should allow us to remove a few
lines. Let `i` be the index of a character in `S`. Initially we have
`i := n - 1`, where `n` is the number of characters in `S`. The character at
index `i` is the right character, whereas the character at index `i - 1` is the
left character. If `S` is not sorted in lexicographic order, then we can find
the greatest index `i` such that the characters at indices `i` and `i - 1` can
be interchanged. Swap the two adjacent characters, set `i` to the greatest index
of `S`, and repeat the process. Otherwise, `S` is sorted in lexicographic order
and eventually the index `i` is 0. We take the value `i := 0` as the signal to
print the sorted string `S`. This solution is optimal, according to the game.

```
str = input;               // Read a string S.
int = str.length - 1;      // Index i of last character.
loop:                      // Start of "loop".
    char = str[int];       // Right character.
    reg = int - 1;         // Index i - 1 of left character.
    switch int;            // Store index i in memory.
    int = char;            // Right character as integer.
    char = str[reg];       // Left character.
    reg = char;            // Left character as integer.
    check reg > int;       // Is left char > right char?
    jump if true: swap;    // If so, go to "swap".
    switch int;            // Retrieve index i.
    int--;                 // Decrement index i.
    check int < 1;         // Is index i < 1?
    jump if false: loop;   // If not, go to "loop".
    jump to: print;        // Go to "print".
swap:                      // The "swap" branch.
    switch int;            // Get index i; store right char.
    str[int] = char;       // Left char at right index.
    reg = int - 1;         // Index of left character.
    switch int;            // Get right char; store index i.
    char = int;            // Right char as character.
    str[reg] = char;       // Right char at left index.
    int = str.length - 1;  // Set i to last index of S.
    jump to: loop;         // Go to "loop".
print:                     // The "print" branch.
    output = str;          // Print the sorted string.
```
