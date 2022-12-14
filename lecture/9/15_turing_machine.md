# September 15th: The Turing Machine

## Context
Alan Turing reformulates the "decidability" problem as a computation problem:

> Was it computed?

Then we have to ask

> What can we compute?

Leading us finally to

> What does it mean to compute?

In Turing's time, "computers" were women in a room who performed computations on paper.

Turing is going to abstract this paper and these women into a Turing Machine. Any computation can be represented as a Turing Machine.

## What is a Turing Machine?

### English Specification

* The page is divided into a "tape" of cells that can each contain exactly one symbol.
* The machine can see one cell at a time, and it starts at position 0, the very beginning of the paper.
* The machine has a notion of state
  * It begins at $q_0$
  * Based on what appears on the tape, the machine can move into a different state.
* The machine can traverse the tape in either direction
* The machine can replace symbols on the tape.

### Formal Specification

* $Q$ is a finite set of states $\{q_0, q_1, q_2, ..., q_n\}$
  * $q_0$ is the inital state
  * $q_{halt}$ stops the machine, for convenience
* $\Gamma$ is a finite set of symbols ( $\{0,1\}$ or $\{a, b, c,...\}$)
* $\delta$ is the transition function ( $Q \times \Gamma \mapsto \Gamma \times \{L, R\} \times Q$)
  * Symbol and state maps to symbol and movememnt and state
  * The function must be exhaustive for every state/symbol combination

If we specify $Q$, $\Gamma$, and $\delta$, we have specified the Turing Machine.

### Street Cred

Alonzo Church invents Lambda Calculus, which is another way to specify computations in a more "mathy" way. Turing Machines and Lambda Calculus are proved to be of equivalent power.

## Performing Computations

### Let's try to compute a rational number to infinite precision

For example, $\frac{1}{2} = 0.5$ in decimal $= 0.1$ in binary

### A bad machine will...

* move off the left end of the tape
* try to enter a nonexistant state
* halt
* loop without printing numbers

### Examples of this Machine

* Printing $\frac{1}{2}$
  
$Q$ | $\Gamma$ | Operation
--- | ---      | ---
$q_0$ | - | P1, R, $q_1$
$q_1$ | - | P0, R, $q_1$

* Printing $\frac{1}{64}$

$Q$ | $\Gamma$ | Operation
--- | ---      | ---
$q_0$ | - | P0, R, $q_1$
$q_1$ | - | P0, R, $q_2$
$q_2$ | - | P0, R, $q_3$
$q_3$ | - | P0, R, $q_4$
$q_4$ | - | P0, R, $q_5$
$q_5$ | - | P1, R, $q_6$
$q_6$ | - | P0, R, $q_6$

* Printing $\frac{1}{3}$

$Q$ | $\Gamma$ | Operation
--- | ---      | ---
$q_0$ | - | P0, R, $q_1$
$q_1$ | - | P1, R, $q_0$

* Printing 001011011101111
  * We are going to make some convenient changes to our notation, so we can move more than one cell at a time.
  * It is helpful to add a marker at the left end of the tape so we don't accidentially fall of the end.
  * We are also going to print the number on every other cell, and use the interleaving space as "scractch" paper.
  * We can send a second turing machine along the tape afterwards to get everything to be contiguous again.
    * The following turing machine does that smushing operation:

$Q$ | $\Gamma$ | Operation
--- | ---      | ---    
$q_0$ | 0, 1 | R, $q_1$
$q_1$ | -    | R, $q_1$
$q_1$ | 0    | P_, L, $q_2$
$q_1$ | 1    | P_, L, $q_3$
$q_2$ | -    | L, $q_2$
$q_2$ | 0, 1 | R, P0, $q_1$
$q_3$ | -    | L, $q_3$
$q_3$ | 0, 1 | R, P1, $q_1$

  * Now we specify the turing machine that will generate $\pi$ in every other cell
    * $q_0$ conveniently puts the marker on the left side of the tape, and prints the two leading 0s
    * $q_1$ puts an $x$ next to every 1 on the tape, moving left
    * $q_2$ moves to the right end of the tape
    * $q_3$ prints a 1 on the right end of the tape for every $x$, then moves back to the very left side
    * $q_4$ prints a 0 on the left end of the tape

$Q$   | $\Gamma$    | Operation      | Final
---   | ---         | ---            | ---
$q_0$ | -           | P $\text{\o}$, R, P $\text{\o}$, R, P0, R, R, P0, L, L | $q_1$ 
$q_1$ | 1           | R, P$x$, L, L, L | $q_1$
$q_1$ | 0           |                | $q_2$
$q_2$ | 0, 1        | R, R           | $q_2$
$q_2$ | -           | Pq, L          | $q_3$
$q_3$ | x           | P_, R          | $q_2$
$q_3$ | $\text{\o}$ | R              | $q_4$
$q_3$ | -           | L, L           | $q_3$
$q_4$ | 0, 1        | R, R           | $q_4$
$q_4$ | -           | P0, L, L       | $q_1$

## What can this machine compute?

* Anything in First Order Logic.
* Anything in C
* Anything in anything really. That's our definition of computable.
