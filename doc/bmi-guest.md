# BMI Guest

## Problem

Read two values from input: the weight (kg) followed by the height (m).
Calculate the body mass index (BMI) and print the result.

{% youtube id="DUQFF2_dZ0Q", title="3. BMI guest, Comet 64" %}{% endyoutube %}

## Solution

Let w be the weight in kilograms (kg) and h the height in metres (m). The body
mass index is given by the formula:

```
BMI := w / h^2
```

The solution below is a straightforward implementation of the BMI formula. This
solution is optimal, according to the game.

```
int = input;      // First, read the weight.
reg = input;      // Second, read the height.
reg = reg * reg;  // The square of the height.
reg = int / reg;  // The body mass index (BMI).
output = reg;     // Print the BMI.
```
