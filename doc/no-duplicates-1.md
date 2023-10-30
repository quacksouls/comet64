# No Duplicates!

## Problem

Read 11 random one-digit numbers. Exactly one of the digits appears twice. Find
and print the duplicate digit.

{% youtube id="J4FxfK_ZWWA", title="38. No duplicates!, Comet 64" %}{% endyoutube %}

## Solution 1

Use an array of 10 elements, because the one-digit numbers start from 0 and end
at 9, inclusive. The only array we have access to is a string of characters.
Interpret a string as an array of characters. Let `i` be an input one-digit
integer. If the character in `str` at index `i` is lower-case O (i.e. `o`), this
is the first time we see `i`. Set the character in `str` at index `i` to `x`,
meaning we have seen the digit `i`. However, in case the character in `str` at
index `i` is `x`, then we have seen `i` already and this is the second time we
are seeing `i`. Therefore `i` is a duplicate.

```
str = oooooooooo;         // Array of 10 elements.
loop:                     // Start of "loop".
    int = input;          // Read a one-digit integer i.
    char = str[int];      // Peek at character with index i.
    check char = x;       // Is character = x?
    jump if true: print;  // If so, go to "print".
    char = x;             // Otherwise, have not seen i yet.
    str[int] = char;      // Mark the number as seen.
    jump to: loop;        // Go to "loop".
print:                    // The "print" branch.
    output = int;         // Print the duplicate number.
```

## Solution 2

All the one-digit integers are:

```
0, 1, 2, 3, ..., 8, 9
```

The sum of these digits is

```
0 + 1 + 2 + 3 + ... + 8 + 9 = 45
```

Let `x` be a repeating digit. The sum of the 11 random one-digit numbers is
`S := 45 + x`. The value of the repeating digit is therefore `x := S - 45`.

```
loop:                     // Start of "loop".
    check input = null;   // Any more digits to read?
    jump if true: print;  // If not, go to "print".
    int = int + input;    // Update cumulative sum.
    jump to: loop;        // Go to "loop".
print:                    // The "print" branch.
    int = int - 45;       // The duplicate digit.
    output = int;         // Print the duplicate digit.
```

## Solution 3

Similar to [Solution 2](#solution-2). However, after we have updated the
cumulative sum, we check whether there are any more integers to read. This
allows us to remove a jump instruction and a label. The register `int` initially
holds zero. There is no need to explicitly set `int` to zero at the start of the
program. This solution is optimal, according to the game.

```
loop:                     // Start of "loop".
    int = int + input;    // Update cumulative sum.
    check input = null;   // Any more digits to read?
    jump if false: loop;  // If so, go to "loop".
int = int - 45;           // Otherwise, get duplicate digit.
output = int;             // Print the duplicate digit.
```
