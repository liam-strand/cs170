---
geometry: margin=1.5in
header-includes:
  - \pagenumbering{gobble}
---

# Closure

## Compliment

* If a language is in P, so is its compliment!
* If a language is in NP, we know nothing about its compliment.

## Intersection

* If $L_1$ and $L_2$ are in P, so is $L_1 \cap L_2$
* If $L_1$ and $L_2$ are in NP, so is $L_1 \cap L_2$
* If $L_1$ and $L_2$ are in NP-Complete, $L_1 \cap L_2$ is in NP, but not necesssarilty NP-Complete

## Union

* If $L_1$ and $L_2$ are in P, so is $L_1 \cup L_2$
* If $L_1$ and $L_2$ are in NP, so is $L_1 \cap L_2$
* If $L_1$ and $L_2$ are in NP-Complete, $L_1 \cup L_2$ is in NP, but not necesssarilty NP-Complete

## Concatenation

* If $L_1$ and $L_2$ are in P, so is $L_1 \cdot L_2$
* If $L_1$ and $L_2$ are in NP, so is $L_1 \cdot L_2$ (we can construct a nondeterministic poly-time decider without too much hassle)
* If $L_1$ and $L_2$ are in NP-Complete, $L_1 \cdot L_2$ is in NP, but not necesssarilty NP-Complete


# The big outstanding questions:

* P = NP?
* $L_1$ in NP $\implies$ $\overline{L_1}$ in NP?
* $L_1$ in NP-Complete $\implies$ $\overline{L_1}$ in NP-Complete?
