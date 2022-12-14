# September 20th: The Universal Turing Machine

> It is possible to invent a single machine which can be used to compute any computable sequence.

The Universal Turing Machine can run other Turing Machines.

## Standardization of Specification

* We want to simplify this as much as possible so that we can use as few symbols as possible.
  * Instead of having specific symbols, we'll just call them $s$, $s'$, $s''$, etc.
    * We'll just look up the actual symbols after the fact.
  * We can do the same trick with the states: $q$, $q'$, $q''$, etc.
  * We can omit the commas in the operation
  * We specify `:` as the separator between lines.

So.... This Turing Machine:

$Q$   | $\Gamma$ | Operation | Final
---   | ---      | ---       | ---
$q_0$ | 0        | P0, L     | $q_{halt}$ 
$q_0$ | 1        | P0, L     | $q_{halt}$ 
$q_0$ | -        | P0, R     | $q_1$ 
$q_1$ | 0        | P0, L     | $q_{halt}$
$q_1$ | 1        | P0, L     | $q_{halt}$
$q_1$ | -        | P1, R     | $q_0$

Becomes:

$Q$   | $\Gamma$ | Operation | Final | :
---   | ---      | ---       | ---   | ---
$q$  | $s$       | P $s$ L    | $q''$ | :
$q$  | $s'$      | P $s$ L    | $q''$ | :
$q$  | $s''$     | P $s$ R    | $q'$  | :
$q'$ | $s$       | P $s$ L    | $q''$ | :
$q'$ | $s'$      | P $s$ L    | $q''$ | :
$q'$ | $s''$     | P $s'$ R   | $q$   | :

Becomes:

$$qs\text{P}s\text{L}q'':
qs'\text{P}s\text{L}q'':
qs''\text{P}s\text{R}q':
q's\text{P}s\text{L}q'':
q's'\text{P}s\text{L}q'':
q's''\text{P}s'\text{R}q:$$

Now we can assign each symbol a number:

Symbol | Number
---    | ---
$q$    | 1
$s$    | 2
P      | 3
R      | 4
L      | 5
$'$    | 6
:      | 7

And then we can generate a number that identifies a specific Turing Machine.

$$1232517126325.....417$$

So we can just line up all the damn numbers and determine if each number is associated with a syntactically valid Turing Machine. So, there are a ***countably infinite*** number of valid Turing Machines.

This means that we can't write a Machine for every possible real number, since there are an *uncountably infinite* number of those.

## Processing the Program

The Universal Turing Machine takes the program as an input on the left side of the tape.

We don't want to directly print the number, because the execution of the program might overwrite its own program.

So we have to get fancy.

### Notation Break

* We need a compact way to express the tape configuration.
* So we are going to write all the symbols next to each other, with the machine state immediately before the cell that is under the reader head.
* For example, after completing the $q_0$ of the $\pi$ computing Machine, the tape state would look like the following:

$$\text{\o\o} q_1 0 \_ 0$$

Instead of writing out the final output, we are going to write each tape configuration in succession, separated by a separator like `:`.

Given the current state, the machine specification, and the tape configuration (actually all encoded in the tape configuration if you put the specification on the tape); it is a trivial matter to look up the instruction and generate the next tape configuration.

### Optimization

We can optimize this by not copying the entire tape configuration for every machine tick.

1. Copy first part of previous configuration
2. Find the instruction you need in the program segment
3. Update the critical section of the new configuration
4. Copy final part of previous configuration

### Output

In order to actually get the output, we need one final rule.

> Once we write a new digit of the number, we will NOT delete or change it.

So we have the final 5 steps:

1. Copy first part of previous configuration
2. Find the instruction you need in the program segment
3. Update the critical section of the new configuration
4. Copy final part of previous configuration
5. Check for a new digit.
    * If there is a new digit, print it after the tape configuration separator
    * If there is not, print a second separator.


Ok, so in theory, we have generated a Turing Machine that can take any machine specification as input and will compute the result of that Turing Machine.
