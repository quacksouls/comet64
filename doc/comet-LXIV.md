# Comet LXIV

## Problem

Given an integer between 1 and 20, inclusive, convert the integer to Roman
numeral.

{% youtube id="EJCavvANBUE", title="30. Comet LXIV, Comet 64" %}{% endyoutube %}

## Solution 1

Let `n` be the input integer, where `1 <= n <= 20`. Let `q` and `r` be the
quotient and remainder, respectively, after dividing `n` by 10. We have these
cases:

1. If `q = 2`, then `n = 20`.
1. If `q = 1`, then `10 <= n < 20`.
1. If `q = 0`, then `n < 10`.

We isolate the quotient `q` and remainder `r`. Convert to Roman numeral on a
case-by-case basis.

```
str = ;                   // S := empty string
reg = input;              // Read the integer n.
int = reg / 10;           // The quotient.
int = int * 10;           // The quotient as tens.
int = reg - int;          // The remainder.
switch int;               // Store the remainder.
int = reg / 10;           // The quotient.
reg = int;                // Quotient q.
switch int;               // Remainder r.
check reg = 2;            // Is q = 2?
jump if true: twenty;     // If so, go to "twenty".
check reg = 1;            // Is q = 1?
jump if true: ten;        // If so, go to "ten".
jump to: units;           // Otherwise, go to "units".
twenty:                   // The "twenty" branch.
    str = XX;             // Append XX to S.
    jump to: units;       // Go to "units".
ten:                      // The "ten" branch.
    str = X;              // Append X to S.
units:                    // The "units" branch.
    check int = 9;        // Is n = 9?
    jump if true: nine;   // If so, go to "nine".
    check int > 4;        // Is n >= 5?
    jump if true: five;   // If so, go to "five".
    check int = 4;        // Is n = 4?
    jump if true: four;   // If so, go to "four".
    check int = 0;        // Is n = 0?
    jump if true: print;  // If so, go to "print".
    str = str + I;        // Append I to S.
    int--;                // n := n - 1
    jump to: units;       // Go to "units".
nine:                     // The "nine" branch.
    str = str + IX;       // Append IX to S.
    jump to: print;       // Go to "print".
five:                     // The "five" branch.
    str = str + V;        // Append V to S.
    int = int - 5;        // n := n - 5
    jump to: units;       // Go to "units".
four:                     // The "four" branch.
    str = str + IV;       // Append IV to S.
print:                    // The "print" branch.
    output = str;         // Print the Roman numeral.
```

## Solution 2

Let `n` be an integer such that `1 <= n <= 20`. Let `S` be a string
representation of the Roman numeral equivalent of `n`. Initially, `S` is the
empty string. We have these cases to consider, in the order given:

1. If `n >= 10`, then the Roman numeral has an `X`. Append `X` to `S` and set
   `n := n - 10`.
1. If `n = 9`, then the Roman numeral has `IX`. Append `IX` to `S` and set
   `n := n - 9`.
1. If `n >= 5`, then the Roman numeral has a `V`. Append `V` to `S` and set
   `n := n - 5`.
1. If `n = 4`, then the Roman numeral has `IV`. Append `IV` to `S` and set
   `n := n - 4`.
1. If `n > 0`, then the Roman numeral has an `I`. Append `I` to `S` and set
   `n := n - 1`.
1. If `n = 0`, then we have finished our conversion from decimal to Roman
   numeral. Print the string `S`.

```
int = input;              // Read the decimal number n.
str = ;                   // S := empty string
loop:                     // Start of "loop".
    check int > 9;        // Is n >= 10?
    jump if true: ten;    // If so, go to "ten".
    check int = 9;        // Is n = 9?
    jump if true: nine;   // If so, go to "nine".
    check int > 4;        // Is n >= 5?
    jump if true: five;   // If so, go to "five".
    check int = 4;        // Is n = 4?
    jump if true: four;   // If so, go to "four".
    check int = 0;        // Is n = 0?
    jump if true: print;  // If so, go to "print".
    str = str + I;        // Append I to S.
    int--;                // n := n - 1
    jump to: loop;        // Go to "loop".
ten:                      // The "ten" branch.
    str = str + X;        // Append X to S.
    int = int - 10;       // n := n - 10
    jump to: loop;        // Go to "loop".
nine:                     // The "nine" branch.
    str = str + IX;       // Append IX to S.
    jump to: print;       // Go to "print".
five:                     // The "five" branch.
    str = str + V;        // Append V to S.
    int = int - 5;        // n := n - 5
    jump to: loop;        // Go to "loop".
four:                     // The "four" branch.
    str = str + IV;       // Append IV to S.
print:                    // The "print" branch.
    output = str;         // Print the Roman numeral.
```

## Solution 3

Similar to [Solution 2](#solution-2). However, we create a label called `units`
to handle the case where `n < 4`. As long as `0 < n <= 3`, we append `I` to the
string `S`. If `n = 0`, then we print the Roman numeral. This solution is
optimal, according to the game.

```
int = input;              // Read the decimal number n.
str = ;                   // S := empty string
loop:                     // Start of "loop".
    check int > 9;        // Is n >= 10?
    jump if true: ten;    // If so, go to "ten".
    check int = 9;        // Is n = 9?
    jump if true: nine;   // If so, go to "nine".
    check int > 4;        // Is n >= 5?
    jump if true: five;   // If so, go to "five".
    check int = 4;        // Is n = 4?
    jump if true: four;   // If so, go to "four".
units:                    // The "units" branch.
    check int = 0;        // Is n = 0?
    jump if true: print;  // If so, go to "print".
    str = str + I;        // Append I to S.
    int--;                // n := n - 1
    jump to: units;       // Go to "units".
ten:                      // The "ten" branch.
    str = str + X;        // Append X to S.
    int = int - 10;       // n := n - 10
    jump to: loop;        // Go to "loop".
nine:                     // The "nine" branch.
    str = str + IX;       // Append IX to S.
    jump to: print;       // Go to "print".
five:                     // The "five" branch.
    str = str + V;        // Append V to S.
    int = int - 5;        // n := n - 5
    jump to: units;       // Go to "units".
four:                     // The "four" branch.
    str = str + IV;       // Append IV to S.
print:                    // The "print" branch.
    output = str;         // Print the Roman numeral.
```
