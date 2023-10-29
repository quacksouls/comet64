# Paired Coordinates

## Problem

Read in the numbers `x_1`, `x_2`, `y_1`, `y_2` and output the points
`(x_1, y_1)` and `(x_2, y_2)`.

{% youtube id="2ImFwXR48ig", title="32. Paired coordinates, Comet 64" %}{% endyoutube %}

## Solution

We are given `x_1`, `x_2`, `y_1`, `y_2`. We must output `(x_1, y_1)` and
`(x_2, y_2)`. This solution is optimal, according to the game.

```
int = input;        // x_1
reg = input;        // x_2
switch reg;         // Store x_2 in memory.
reg = input;        // y_1
output = int, reg;  // Print (x_1, y_1).
switch int;         // Retrieve x_2 from memory.
reg = input;        // y_2
output = int, reg;  // Print (x_2, y_2).
```
