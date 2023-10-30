# As Easy As 01 10 11

## Problem

Let `n` be an integer between 0 and 15, inclusive. Convert `n` to its binary
representation and print the result.

{% youtube id="m_09ab_AtUM", title="36. As easy as 01 10 11, Comet 64" %}{% endyoutube %}

## Solution 1

This is a brute force solution. It checks every possible value of the input
integer and jumps to the appropriate branch to output the corresponding binary
representation.

```
start:
    int = input;
    check int = 15;
    jump if true: fifteen;
    check int = 14;
    jump if true: fourteen;
    check int = 13;
    jump if true: thirteen;
    check int = 12;
    jump if true: twelve;
    check int = 11;
    jump if true: eleven;
    check int = 10;
    jump if true: ten;
    check int = 9;
    jump if true: nine;
    check int = 8;
    jump if true: eight;
    check int = 7;
    jump if true: seven;
    check int = 6;
    jump if true: six;
    check int = 5;
    jump if true: five;
    check int = 4;
    jump if true: four;
    check int = 3;
    jump if true: three;
    check int = 2;
    jump if true: two;
    check int = 1;
    jump if true: one;
    output = 0000;
    jump to: start;
fifteen:
    output = 1111;
    jump to: start;
fourteen:
    output = 1110;
    jump to: start;
thirteen:
    output = 1101;
    jump to: start;
twelve:
    output = 1100;
    jump to: start;
eleven:
    output = 1011;
    jump to: start;
ten:
    output = 1010;
    jump to: start;
nine:
    output = 1001;
    jump to: start;
eight:
    output = 1000;
    jump to: start;
seven:
    output = 0111;
    jump to: start;
six:
    output = 0110;
    jump to: start;
five:
    output = 0101;
    jump to: start;
four:
    output = 0100;
    jump to: start;
three:
    output = 0011;
    jump to: start;
two:
    output = 0010;
    jump to: start;
one:
    output = 0001;
```

## Solution 2

Consider the following integer to binary conversion table:

```
0: 0000     8: 1000
1: 0001     9: 1001
2: 0010    10: 1010
3: 0011    11: 1011
4: 0100    12: 1100
5: 0101    13: 1101
6: 0110    14: 1110
7: 0111    15: 1111
```

Let `n` be the input integer and let `S` be a string of binary digits. If
`n >= 8`, then the first digit of `S` is 1 and we set `n := n - 8`. Otherwise
the first digit of `S` is 0. If `n >= 4`, the second digit of `S` is 1 and set
`n := n - 4`. Otherwise the second digit of `S` is 0. If `n >= 2`, the third
digit of `S` is 1 and set `n := n - 2`. Otherwise, the third digit of `S` is 0.
If `n = 1`, the fourth digit of `S` is 1 and print the string `S`. Otherwise,
the fourth digit of `S` is 0 and print `S`. This solution is optimal, according
to the game.

```
int = input;              // Read the input integer n.
str = ;                   // S := empty string
check int > 7;            // Is n >= 8?
jump if false: zero8;     // If not, go to "zero8".
str = str + 1;            // Otherwise, 1 as first digit.
int = int - 8;            // n := n - 8
jump to: four;            // Go to "four".
zero8:                    // The "zero8" branch.
    str = str + 0;        // 0 as first digit.
four:                     // The "four" branch.
    check int > 3;        // Is n >= 4?
    jump if false: zero4; // If not, go to "zero4".
    str = str + 1;        // Otherwise, 1 as second digit.
    int = int - 4;        // n := n - 4
    jump to: two;         // Go to "two".
zero4:                    // The "zero4" branch.
    str = str + 0;        // 0 as second digit.
two:                      // The "two" branch.
    check int > 1;        // Is n >= 2?
    jump if false: zero2; // If not, go to "zero2".
    str = str + 1;        // Otherwise, 1 as third digit.
    int = int - 2;        // n := n - 2
    jump to: one;         // Go to "one".
zero2:                    // The "zero2" branch.
    str = str + 0;        // 0 as third digit.
one:                      // The "one" branch.
    check int = 1;        // Is n = 1?
    jump if false: zero;  // If not, go to "zero".
    str = str + 1;        // Otherwise, 1 as fourth digit.
    jump to: print;       // Go to "print".
zero:                     // The "zero" branch.
    str = str + 0;        // 0 as fourth digit.
print:                    // The "print" branch.
    output = str;         // Print the binary representation.
```
