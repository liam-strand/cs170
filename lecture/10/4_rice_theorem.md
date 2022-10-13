# October 4th: Rice's Theorem

## More Undecidable Languages

### $\text{E}_{\text{TM}}$

Defined to be the following language:

$$\text{E}_{\text{TM}} = \{\langle M \rangle \mid M \text{ is a TM and } L(M) \text{ is } \emptyset\}$$

The language of turing machine specifications for a decider that will never accept.

**Proof by reduction** from $A_{\text{TM}}$ to $\text{E}_{\text{TM}}$

$D_A$ does the following on input $\langle M, w \rangle$:

1. Construct $M'$
   1. If $x \neq w$, REJECT
   2. If $x = w$, Run $M$ on $w$
   3. DWID ("do what it does")
2. Run $D_E \langle M' \rangle$ and DTO ("do the opposite)

**Cases:**

$\langle M, w \rangle \in A_{\text{TM}}$: Well, $M$ accepts $w$, which means that $M'$ accepts an input. So $D_E$ rejects $M'$ and $D_A$ accepts.

$\langle M, w \rangle \notin A_{\text{TM}}$: Well, $M$ does not accept $w$, which means that $M'$ rejects on all inputs. So $D_E$ accepts $M'$ and $D_A$ rejects.

Okay so we add $\text{E}_{\text{TM}}$ to the zoo of undecidable languages.

### $\text{EQ}_{\text{TM}}$

$$\text{EQ}_{\text{TM}} = \{\langle M_1, M_2 \rangle \mid M_1 \text{ and } M_2 \text{ are TMs and } L(M_1) = L(M_2)\}$$

The language of turing machines that accept/reject the same set of languages.

**Proof by reduction** from $\text{E}_{\text{TM}}$ to $\text{EQ}_{\text{TM}}$

$\text{D}_{\text{E}}$ on input $\langle M \rangle$:

1. Construct a machine $M'$ that rejects everything
2. Run $\text{D}_{\text{EQ}}$ on $\langle M, M' \rangle$ and DWID

yay

$$\pagebreak$$

### $\text{101}_{\text{TM}}$

$$\text{101}_{\text{TM}} = \{\langle M \rangle \mid M \text{ is a TM that accepts input } 101\}$$

**Proof by reduction** from $\text{A}_{\text{TM}}$ to $\text{101}_{\text{TM}}$

1. Construct the following machine $M'$
   - On input $x$:
     - If $x = 101$, run $M$ on $w$
       - If $M$ accepts $w$, ACCPET
       - If $M$ rejects $w$, loop infinitely
     - Else REJECT
   - Run $\text{D}_{\text{101}} \langle M \rangle$ and DWID.

sure...?

## Rice's Theorem:

> Any nontrivial property about the language recognized by a Turing machine is undecidable.

- Nontrivial = TBD
- About the language = TBD
