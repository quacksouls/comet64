# Launch Discount

## Problem

Read an integer from input, apply a 20% discount, and print the result.

{% youtube id="stlfldVMigw", title="1. Launch discount, Comet 64" %}{% endyoutube %}

## Solution 1

Calculate 20% of the original value. Subtract the 20% value from the original
value. The result should be 80% of the original value.

```
reg = input;      // Read the original value.
int = reg * 0.2;  // Calculate 20% of original value.
reg = reg - int;  // Subtract 20% value from original value.
output = reg;     // Print the result.
```

## Solution 2

A 20% discount is the same as 80% of the original value. We must multiply the
original value by 0.8.

```
reg = 0.8;        // Percentage of original value.
int = input;      // Read original value.
int = int * reg;  // Value after discount.
output = int;     // Print the result.
```

## Solution 3

A 20% discount is the same as 80% of the original value. We must multiply the
original value by 0.8. No need for using the register `reg` to store the
fraction 0.8. Simply multiply the input value by 0.8, store the result to a
register, and print the content of the register. This solution is optimal,
according to the game.

```
reg = input * 0.8;  // Multiply original value by 0.8.
output = reg;       // Print the result.
```
