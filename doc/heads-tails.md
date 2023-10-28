# Heads & Tails

## Problem

Each input value is either "heads" or "tails". Read 100 string values and
determine whether "heads" or "tails" is the winner. If there is no winner, print
"draw".

{% youtube id="lRiJJguCZGw", title="16. Heads or tails, Comet 64" %}{% endyoutube %}

## Solution 1

Use the registers `reg` and `int` to keep track of the number of heads and
tails, respectively. If there are no more input, we print the winner. No need
for an explicit loop. Upon reaching the end of the program, the game would loop
back to the start of the program.

```
check input = null;            // Any more coin results?
jump if true: print;           // No more results, then print.
check input = heads;           // Is it heads?
jump if false: tails;          // If not, go to "tails".
reg++;                         // Increment number of heads.
jump to: end;                  // Go to "end".
print:                         // The "print" branch.
    check reg > int;           // #heads > #tails?
    jump if true: printHeads;  // If true, go to "printHeads".
    check reg = int;           // A draw?
    jump if true: printDraw;   // If true, go to "printDraw".
    output = tails;            // Tails wins.
    jump to: end;              // Go to "end".
printHeads:                    // The "printHeads" branch.
    output = heads;            // Heads wins.
    jump to: end;              // Go to "end".
printDraw:                     // The "printDraw" branch.
    output = draw;             // It's a draw.
tails:                         // The "tails" branch.
    int++;                     // Increment number of tails.
end:                           // End of program.
```

## Solution 2

Similar to [Solution 1](#solution-1). However, we do not need to make an
explicit jump after we print the winner. The game expects only one output. After
receiving an output, the game would terminate the program. This solution is
optimal, according to the game.

```
check input = null;            // Any more coin results?
jump if true: print;           // No more results, then print.
check input = heads;           // Is it heads?
jump if false: tails;          // If not, go to "tails".
reg++;                         // Increment number of heads.
jump to: end;                  // Branch to "end".
print:                         // The "print" branch.
    check reg > int;           // #heads > #tails?
    jump if true: printHeads;  // If true, go to "printHeads".
    check reg = int;           // A draw?
    jump if true: printDraw;   // If true, go to "printDraw".
    output = tails;            // Tails wins.
printHeads:                    // The "printHeads" branch.
    output = heads;            // Heads wins.
printDraw:                     // The "printDraw" branch.
    output = draw;             // It's a draw.
tails:                         // The "tails" branch.
    int++;                     // Increment number of tails.
end:                           // End of program.
```

## Solution 3

In 100 coin flips, we have the following cases:

1. The number of tails is 50, so a draw.
1. The number of tails is at least 51, so tails wins.
1. The number of tails is less than 50, so heads wins.

We only need to keep track of the number of tails. Here we assume that the
register `int` is initially zero. As in [Solution 2](#solution-2), we do not
need to make any jump after printing the winner. This solution is optimal,
according to the game.

```
loop:                      // Start of "loop".
    check input = null;    // Any more coin results?
    jump if true: winner;  // If not, go to "winner".
    check input = tails;   // Is it tails?
    jump if false: loop;   // If not, go to "loop".
    int++;                 // Otherwise, increment #tails.
    jump to: loop;         // Go to "loop".
winner:                    // The "winner" branch.
    check int = 50;        // Is it a draw?
    jump if true: draw;    // If so, go to "draw".
    check int > 50;        // Is tails the winner?
    jump if true: tails;   // If so, go to "tails".
    output = heads;        // Otherwise, heads is the winner.
draw:                      // The "draw" branch.
    output = draw;         // A draw.
tails:                     // The "tails" branch.
    output = tails;        // Tails is the winner.
```
