# Binary Transition

## Problem

Convert a binary number to its decimal representation.

{% youtube id="Wj_qQLCGnq8", title="37. Binary transition, Comet 64" %}{% endyoutube %}

## Solution 1

This is a brute force solution. We check every possible binary representation
and print the corresponding decimal representation.

```
start:
    int = input;
    check int = 1111;
    jump if true: fifteen;
    check int = 1110;
    jump if true: fourteen;
    check int = 1101;
    jump if true: thirteen;
    check int = 1100;
    jump if true: twelve;
    check int = 1011;
    jump if true: eleven;
    check int = 1010;
    jump if true: ten;
    check int = 1001;
    jump if true: nine;
    check int = 1000;
    jump if true: eight;
    check int = 0111;
    jump if true: seven;
    check int = 0110;
    jump if true: six;
    check int = 0101;
    jump if true: five;
    check int = 0100;
    jump if true: four;
    check int = 0011;
    jump if true: three;
    check int = 0010;
    jump if true: two;
    check int = 0001;
    jump if true: one;
    output = 0;
    jump to: start;
fifteen:
    output = 15;
    jump to: start;
fourteen:
    output = 14;
    jump to: start;
thirteen:
    output = 13;
    jump to: start;
twelve:
    output = 12;
    jump to: start;
eleven:
    output = 11;
    jump to: start;
ten:
    output = 10;
    jump to: start;
nine:
    output = 9;
    jump to: start;
eight:
    output = 8;
    jump to: start;
seven:
    output = 7;
    jump to: start;
six:
    output = 6;
    jump to: start;
five:
    output = 5;
    jump to: start;
four:
    output = 4;
    jump to: start;
three:
    output = 3;
    jump to: start;
two:
    output = 2;
    jump to: start;
one:
    output = 1;
```

## Solution 2

We use the method of double dabble to convert from binary to decimal
representation:

https://en.wikipedia.org/wiki/Double_dabble

Let `S` be a string of binary digits. We want to obtain the decimal equivalent
of `S`. Set `d := 0`. Consider `S_0`, the left-most digit. Set
`d := (2 * d) + S_0`. Consider the next digit `S_1` and set
`d := (2 * d) + S_1`. Continue the process until we have considered all binary
digits in `S`. The final value of `d` is the decimal representation of `S`. The
algorithm essentially is to double our current value of `d` and add the current
binary digit under consideration. Use the register `int` to store the decimal
representation. Initially `int` holds 0, hence no need to perform the first
doubling operation.

```
reg = input;
check reg < 1000;
jump if true: four;
reg = reg - 1000;
int++;
four:
    int = 2 * int;
    check reg < 100;
    jump if true: two;
    reg = reg - 100;
    int++;
two:
    int = 2 * int;
    check reg < 10;
    jump if true: one;
    reg = reg - 10;
    int++;
one:
    int = 2 * int;
    check reg < 1;
    jump if true: zero;
    int++;
zero:
    output = int;
    int = 0;
```

## Solution 3

This solution is due to

-   https://steamcommunity.com/id/werg0n
-   https://steamcommunity.com/id/hanni16
-   https://steamcommunity.com/id/giraffe94

from the guide

https://steamcommunity.com/sharedfiles/filedetails/?id=2385965404

The solution is optimal, according to the game. Here is an explanation of the
solution given by WeRGoN, one of the above guide's writers:

```
The main idea of this solution was: using simple mathematical operations on
4-digit binary numbers (which are perceived as decimal), distribute the
results evenly enough to reduce them later to 0, 1, 2, ..., 15.  It seems
that I even managed to do this, but with too many lines, so I modernized the
solution a bit: I tried to do the same thing, but with pairs of binary
digits.

If we go back to my code:
Line 1: add a magic constant (I'll explain it later).
Lines 2-6: we separate the 4-digit number into 2 pairs.
Lines 7-8: transform the first pair.
Lines 9-11: transform the second pair and add to the result from the first
one.

I will begin the explanation with the transformation of pairs.  Each pair of
binary numbers can have 4 states: 00, 01, 10, 11 (i.e. 0, 1, 10, 11).  Our
task is to convert this series into 0, 1, 2, 3 using simple mathematical
operations.  Using only multiplication/division operations, this is
impossible, because the series numbers 0, 1, 10, 11 are distributed very
unevenly (the difference between 1 and 10 is tenfold, and between 10 and 11
is only x1.1).  Ideally, you need to add some value to the numbers of the
series in order to at least slightly smooth this series, and then try to
find a divisor that will reduce it to 0, 1, 2, 3.  If this could not be done
right away, then you would have to repeat these operations several times,
each time slightly smoothing the row. But in this case, one cycle was
enough.

If we add 4 to the series 0, 1, 10, 11, then we get the series 4, 5, 14, 15.
By what number should it be divided to get 0, 1, 2, 3?  It is important not
to forget that the INT register doesn't round off real numbers, but cuts off
the fractional part.  Well, the necessary divisor is the number 5.

Now we can convert two-digit binary numbers to decimal.  It remains only to
multiply the result of top bits pair by 4 and add it to the result of the
second pair.

As for the magic number 404, we simply immediately add the number 4 to each
pair of binary digits so as not to waste two lines of code on this.
```

```
reg = input + 404;
reg = reg / 100;
int = reg;
reg = reg - int;
reg = reg * 100;
switch reg;
int = int / 5;
int = int * 4;
switch reg;
reg = reg / 5;
int = int + reg;
output = int;
```
