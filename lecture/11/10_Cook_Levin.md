---
geometry: margin=1.5in
header-includes:
  - \pagenumbering{gobble}
---

# The Cook-Levin Theorem

We are going to be reducing Sudoku to SAT, to 3SAT, to a Hamiltonian Cycle, to the Travelling Salesman Problem

## NP-Hard and NP-Complete

A new class of problems that are **at least** as hard as hardest NP problems.

If something is in both NP-Hard and NP, then it is NP-Complete. These are the hardest problems in NP. If we can prove a NP-Complete problem is also in P, then we collapse all of NP into P and we are a millionaire and never have to work again.

## More Reduction

For an NP-Hard problem, H, every problem in NP can be reduced to H _in polynomial time_. We express this as:

$$\text{Every NP Problem } {\leq}_\text{P} \text{ NP-Hard Problem}$$

We're going to be using the same trick as with the Languages from the beginning of the course. Where we would use $\text{A}_\text{TM}$ or $\text{Everprint}_\text{TM}$ for Languages, we're going to use SAT for these Problems.

## Reduction of Everything in NP to SAT

We are going to prove the following:

$$\text{Every NP Problem } {\leq}_\text{P} \text{ SAT}$$

uwu let's read the textbook

## Reduction of 3SAT to SAT

### Proof Structure

1. Prove that the thing is in NP (prove a poly-time verifier or NP decider)

   - Case analysis

2. Show that it is in NP-Hard (prove that it is poly-time reducable)

   - Case analysis

### Proof

3SAT looks something like:

$$(x_1 \lor x_2 \lor x_3) \land (x_4 \lor x_5 \lor x_6) \land ...$$

#### Part 1

Is pretty straightforward. SAT is NP, and 3SAT is just a special case of SAT.

#### Part 2

We can expand any SAT expression into a 3SAT by following some simple constant-time rules. See the textbook to find them hehe ngl sussy baka.
