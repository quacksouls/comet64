# Compare the Pair

## Problem

Read two numbers from input, compare them, and print the greater number.

{% youtube id="3g9enxsaZh0", title="6. Compare the pair, Comet 64" %}{% endyoutube %}

## Solution 1

We read two numbers `x` and `y` from input and compare them. If `x > y`, then
the left operand is larger and we print `x`. Otherwise, `x <= y` and we print
the right operand `y`.

```
int = input;           // Read x from input.
reg = input;           // Read y from input.
check int > reg;       // Is x > y?
jump if true: left;    // If true, x is larger.
jump if false: right;  // Otherwise, x <= y.
left:                  // The "left" branch.
    output = int;      // Print x.
    jump to: end;      // Go to "end".
right:                 // The "right" branch.
    output = reg;      // Print y.
end:                   // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1). We can eliminate some lines from the
previous solution by noticing that we do not need a jump instruction when the
conditional `x > y` is false. If the conditional `x > y` is true, we jump to the
branch that prints `x`. Otherwise, we print `y` without having to jump to a
different branch. This solution is optimal, according to the game.

```
int = input;          // Read x from input.
reg = input;          // Read y from input.
check int > reg;      // Is x > y?
jump if true: print;  // If so, go to "print".
int = reg;            // Otherwise, set int to value of reg.
print:                // The "print" branch.
    output = int;     // Print the larger number.
```
