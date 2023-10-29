# Lasting Impression

## Problem

Read an input string and print its last character.

{% youtube id="POg49CyyNSg", title="26. Lasting impression, Comet 64" %}{% endyoutube %}

## Solution 1

Characters in a string are indexed starting from 0. If `n` is the number of
characters in a string, the last character has index `n - 1`. We read a string,
determine the number of characters `n`, calculate the index

```
k := n - 1
```

of the last character, and print the last character.

```
str = input;       // Read the input string.
int = str.length;  // Number of characters in string.
int--;             // Index of the last character.
char = str[int];   // The last character.
output = char;     // Print the last character.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, the index of the last character
can be calculated in one instruction, instead of two. This solution is optimal,
according to the game.

```
str = input;           // Read the input string.
int = str.length - 1;  // Index of the last character.
char = str[int];       // The last character.
output = char;         // Print the last character.
```
