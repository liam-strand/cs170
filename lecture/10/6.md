---
geometry: margin=1.5in
header-includes:
  - \pagenumbering{gobble}
---

# October 6th: More Rice's Theorem

## Review

> Any nontrivial property about the language recognized by a Turing machine is undecidable.

The *nontrivial* and the *about the language* and the *recognized by a Turing machine* are doing a lot of the heavy lifting here.

## Linear Bound Automata

Like a Turing Machine, but with some limitations:

* $q$ states in $Q$
* $g$ symbols in $\Gamma$
* $n$ squares on the tape

The same as a Turing Machine but we cannot use any more space on the tape than was provided in the input.

Thus there are a finite number of tape configurations: $qng^n$

So, with the following language:

$$\text{A}_{\text{LBA}} = \{\langle M, w \rangle \mid M \text{ is a linear bound automaton that accepts } w\}$$

This is decidable because there are a finite number of tape configurations!!

Let's try something a bit harder:

### $\text{E}_{\text{LBA}}$

$$\text{E}_{\text{LBA}} = \{\langle M \rangle \mid M \text{ is a LBA where } L(M) \text{ is } \emptyset\}$$

**Proof by reduction:** $\text{A}_{\text{TM}}$ to $\text{E}_{\text{LBA}}$

$$\text{A}_{\text{TM}} = \{\langle N, w \rangle \mid N \text{ is a TM and } N \text{ accepts } w\}$$

We have to use $\langle N w \rangle$ to build LBA B, as follows...

1. Check for a valid start configuration
2. Check for a valid accept configuration
3. Check that adjacent configurations are valid
4. If any of the above checks fail, **reject**. Otherwise, **accept**.

To construct $\text{D}_{\text{A}}$:

1. Run $\text{D}_{\text{ELBA}} \langle B \rangle$ and 
2. Do the opposite of what it does. hello
