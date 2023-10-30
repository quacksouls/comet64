# Let's Settle This

## Problem

Read two strings from input. Each string is a strategy, i.e. either "rock",
"paper", or "scissors". Compare the two strategies and determine the winner.
Output "draw" in case of no winner.

{% youtube id="CDtNRNx6jtM", title="40. Let's settle this, Comet 64" %}{% endyoutube %}

## Solution 1

Use the following abbreviations and integer values:

```
p := paper, 16
r := rock, 18
s := scissors, 19
```

The integer value corresponding to each strategy is the integer equivalent of
the first character in the strategy's name. The game represents `a` as 1, `b` as
2, `c` as 3, and so on. The winners are:

```
paper := (p - r)^2 = 4
rock := (r - s)^2 = 1
scissors := (s - p)^2 = 9
draw := (p - p)^2 = (r - r)^2 = (s - s)^2 = 0
```

```
loop:                        // Start of "loop".
    str = input;             // Read first strategy.
    char = str[0];           // Abbreviation of strategy.
    reg = char;              // Integer value of strategy.
    str = input;             // Read second strategy.
    char = str[0];           // Abbreviation of strategy.
    int = char;              // Integer value of strategy.
    int = reg - int;         // Difference between integers.
    int = int * int;         // Squared of difference.
    check int = 4;           // Is paper the winner?
    jump if true: paper;     // If so, go to "paper".
    check int = 1;           // Is rock the winner?
    jump if true: rock;      // If so, go to "rock".
    check int = 9;           // Is scissors the winner?
    jump if true: scissors;  // If so, go to "scissors".
    output = draw;           // A draw.
    jump to: loop;           // Go to "loop".
paper:                       // The "paper" branch.
    output = paper;          // Paper wins.
    jump to: loop;           // Go to "loop".
rock:                        // The "rock" branch.
    output = rock;           // Rock wins.
    jump to: loop;           // Go to "loop".
scissors:                    // The "scissors" branch.
    output = scissors;       // Scissors wins.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, instead of calculating the
difference, we calculate the addition of the integer values of both strategies.
Use the following abbreviations and integer values:

```
p := paper, 16
r := rock, 18
s := scissors, 19
```

The winners are:

```
paper := 16 + 18 = 34
rock := 18 + 19 = 37
scissors := 16 + 19 = 35
draw := both strategies are the same
```

We also first check to see whether both strategies are the same. This solution
is optimal, according to the game.

```
loop:                        // Start of "loop".
    str = input;             // Read first strategy.
    char = str[0];           // Abbreviation of strategy.
    reg = char;              // Integer value of strategy.
    str = input;             // Read second strategy.
    char = str[0];           // Abbreviation of strategy.
    int = char;              // Integer value of strategy.
    check int = reg;         // Both strategies the same?
    jump if true: draw;      // If so, go to "draw".
    int = reg + int;         // Addition of strategy codes.
    check int = 34;          // Is paper the winner?
    jump if true: paper;     // If so, go to "paper".
    check int = 37;          // Is rock the winner?
    jump if true: rock;      // If so, go to "rock".
    output = scissors;       // Scissors is the winner.
    jump to: loop;           // Go to "loop".
paper:                       // The "paper" branch.
    output = paper;          // Paper wins.
    jump to: loop;           // Go to "loop".
rock:                        // The "rock" branch.
    output = rock;           // Rock wins.
    jump to: loop;           // Go to "loop".
draw:                        // The "draw" branch.
    output = draw;           // A draw.
```
