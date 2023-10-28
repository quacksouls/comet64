# Reverse Integeering

## Problem

Reverse the digits of a two-digit integer.

{% youtube id="sS7BR4tpfIc", title="14. Reverse integeering, Comet 64" %}{% endyoutube %}

## Solution 1

Switch the digits of a 2-digit integer. Isolate the tens and units digits. Let
`a` be the tens digit and let `b` be the units digit. If we are given a 2-digit
integer as `x := 10*a + b`, then we output `10*b + a`. The tens digit is defined
as `a := floor(x / 10)`. The units digit is defined as `b := x mod 10`, where
`mod` is the remainder operator. We also have the definition `b := x - 10a`.

```
reg = input;      // Read in x.
int = reg / 10;   // The tens digit.
switch int;       // Store the tens digit.
int = reg / 10;   // The quotient a := x / 10.
int = 10 * int;   // The multiple 10a.
int = reg - int;  // The remainder b := x mod 10.
reg = int * 10;   // The remainder is now the tens digit.
switch int;       // Retrieve the tens digit from memory.
reg = reg + int;  // The tens digit is now the units digit.
output = reg;     // Print the reversed number.
```

## Solution 2

Similar to [Solution 1](#solution-1). Let `x` be the input integer and define
the subtraction `x := x - 10`. Repeatedly apply the subtraction until the result
is less than 10, at which point we would be left with the units digit. The tens
digit is `floor(x / 10)`.

```
reg = input;                  // Read in x.
int = reg / 10;               // The tens digit.
subtract:                     // The "subtract" branch.
    reg = reg - 10;           // Subtract 10.
    check reg < 10;           // Is the result < 10?
    jump if false: subtract;  // If not, subtract again.
reg = reg * 10;               // The tens digit of new number.
reg = reg + int;              // The reversed number.
output = reg;                 // Print the reversed number.
```

## Solution 3

Let `n := 10a + b` be a 2-digit integer, where `a` and `b` are decimal digits.
For brevity, we write the 2-digit number as `ab`. Using digit-wise
multiplication, we have

```
(1) 10.1 * ab = aba.b
```

If we can remove the right-most and left-most digits from expression (1), we
should have the reverse of the original 2-digit integer. The left-most digit is
a. It can be extracted by the digit-wise expression `floor(aba.b / 100)`. The
expression `floor(aba.b / 100)` can be problematic because given
`floor(999.9 / 100)` the game rounds the result to 10. Instead, use
`floor(aba.b / 100.1)`. To remove the left-most digit, perform the digit-wise
subtraction

```
(2) aba.b - a00.0 = ba.b
```

Now to remove the right-most digit b from expression (2), use `floor(ba.b)`.
This solution is optimal.

```
reg = input * 10.1;  // 10.1 * ab = aba.b
int = reg / 100.1;   // a := floor(aba.b / 100.1)
int = int * 100;     // a00
int = reg - int;     // ba := floor(aba.b - a00.0)
output = int;        // Print the reversed integer.
```
