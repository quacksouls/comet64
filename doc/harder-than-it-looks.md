# Harder Than It Looks

## Problem

Read a floating point number `x` from input and print the number `x * (x - 1)`.

{% youtube id="9L16Od1gwOo", title="22. Harder than it looks, Comet 64" %}{% endyoutube %}

## Solution 1

Let `x` be a floating point number with one digit after the decimal point. Write
the expression

```
x * (x - 1)
```

as

```
(x / 10) * [10 * (x - 1)]
```

The expression

```
10 * (x - 1) = 10*x - 10
```

is an integer so it can be stored in the register `int`. We store `x / 10` in
the register `reg`.

```
reg = input;      // Read the number x.
int = 10 * reg;   // 10*x
int = int - 10;   // 10*x - 10
reg = reg / 10;   // x / 10
reg = reg * int;  // (x / 10) * [10 * (x - 1)]
output = reg;     // Print the result.
```

## Solution 2

This solution is similar to the solution in the section
[Easier Than It Looks](./easier-than-it-looks.md). We transform the input number
into an integer and apply the solution in the previous section. Let `x` be a
floating point number with one digit after the decimal point. Write the
expression

```
x * (x - 1)
```

as

```
[10*x * 10*(x - 1)] / 100
```

Store `10*x` in the register `reg`. The expression

```
10 * (x - 1) = 10*x - 10
```

is an integer so it can be stored in the register `int`. Multiply the values of
`reg` and `int` and store the result in `reg`. To recover the original
expression, we must divide by 100 and use the floating point value. This
solution is optimal, according to the game.

```
reg = 10 * input;  // 10*x
int = reg - 10;    // 10*x - 10
reg = reg * int;   // 10*x * 10*(x - 1)
reg = reg / 100;   // [10*x * 10*(x - 1)] / 100
output = reg;      // Print result.
```
