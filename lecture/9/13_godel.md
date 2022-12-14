# September 13th: Gödel

## Recap

### Propositional Logic

* If we can prove $p$ and $\lnot p$, then you can prove anything $q$ because of the following formula derivable from the axioms $p \implies (\lnot p \implies q)$.
* Therefore if any one thing is *not* provable, then the system is consistent
* Therefore if anything is *not* universally valid, then consistent
* $p \lor q$ is syntactically correct, but is not universally valid
* Therefore the propositional logic system is consisitent

## Gödel

### Gödel Begins

* He opens the paper with a property very similar to Richard's paradox: *Let us assign a number to every property that we can define over the cardinal numbers*
* He also defines a set of symbols he's going to use:

Symbol | Definition | Gödel Number
---        | ---                        | ---
$\lnot$    | not                        | 1
$\lor$     | or                         | 2
$\implies$ | implies                    | 3
$\exists$  | there exists               | 4
$=$        | equals                     | 5
$0$        | zero                       | 6
$s$        | the successor ( $s0 = 1$ ) | 7
$($        |                            | 8
$)$        |                            | 9
$,$        |                            | 10
$+$        | addition                   | 11
$\times$   | multiplication             | 12

 * He uses the substitution and detachment rules from prospective logic

### Gödel Numbers

* Assign each elemntary symbol a number
* Assign numeric variables $x$, $y$, and $z$ a number as follows

Variable | Number
--- | ---
$x$ | $13$
$y$ | $17$
$z$ | $19$

* Formulas get assending prime numbers, squared

Formula | Number
---     | ---
$p$     | $13^2$
$q$     | $17^2$
$r$     | $19^2$

* Predicates get assending prime numbers, cubed

Predicate | Number
---       | ---
$P$       | $13^3$
$Q$       | $17^3$
$R$       | $19^3$

* Now we can calculate the Gödel number of a formula as follows:
  * Find the Gödel number of each element in the formula
  * Raise each prime, starting at 2, ascending, to the power of each number in order.
  * Multiply these powered primes together
* This produces a unique number for every formula
* Furthermore, an entire proof can have a Gödel number, calculated as follows
  * Same trick as before. Proofs are made up of formulas.
  * Calculate the Gödel number of each formula
  * Raise each successive prime, starting at 2, to the power of the associated Gödel number.
  * Multiply these together.
* Using prime factorization, we can deconstruct a Gödel number into a full symbolic proof.

### Applying Gödel Numbers

All of the sudden, we can take abstract statements like

> $(p \lor p)$ is an initial part of $(p \lor p) \implies p$

And write it as an arithmatic statement: 

> The Gödel number of $(p \lor p)$ is a factor of the Gödel number of $(p \lor p) \implies p$

The propositional logic deduction rules have a similar arithmatic meaning in Gödel's system.

### Using Gödel Numbers with Predicates

We can define the predicate $\text{Sub}()$ as the substitution predicate. For example. $\text{Sub}(m, 17, 0)$ means "Substitute the representation for $0$ for the character represented by $17$ in the formula $m$".

So, we have:

* $(\exists x) (x = sy) = m$
* $(\exists x) (x = s0) = n$
* $\text{Sub}(m, 17, 0) = (\exists x) (x = s0) = n$
* $\text{Sub}(m, 17, 1) = (\exists x) (x = ss0)$
* $\text{Sub}(m, 17, m) = (\exists x) (x = sss...s0) = j$
* $f(m, 17) = j$

In essence, Gödel has created a system where he can arithmatize logical deduction.

If we have $2^m \times 3^n = k$, then $k$ is a proof of $n$. 

We can formalize this with the predicate $\text{Dem}(k, n)$ ($\text{Dem}$ for demonstrates)

### Inconsistency

We have the formula $\lnot (\exists x) \text{Dem}(x, y)$, the formula with Gödel number $y$ cannot be demonstrated.

We have the formula $\text{Sub}(y, 17, y)$, so we substitute the representation for $y$ for the character represented by $17$ in the formula $y$.

Then we sub that in to the earlier formula: 

$$\lnot (\exists x)\text{Dem}(x, \text{Sub}(n, 17, n))$$

So we can try to solve for this formula's Gödel number.

Let the Gödel number of $\text{Sub}(n, 17, n)$ be $G$.

If we demonstrate $G$, it assets that $G$ is not demonstrable

If we demonstrate $\lnot G$, we prove that there is a proof of $G$.

So.... 

$$G \implies \lnot G$$

$$\lnot G \implies G$$

We must now choose between consistency and completeness. It is better to choose that 

> If arithmatic is consistent, therefore arithmatic is incomplete

Let's construct that.

**For the first statement:**

$$p \implies (\lnot p \implies q)$$

There is at least one formula that cannot be demonstrated

$$(\exists y) \lnot (\exists x) \text{Dem}(x, y)$$

**For the second statement:**

Some theorem $X$ is true, but is not demonstrable within the system.

$$G$$

$$\lnot (\exists x) \text{Dem}(x, \text{Sub}(n, 17, n))$$

**So putting it together:**

$$(\exists y) \lnot (\exists x) \text{Dem}(x, y) \implies \lnot (\exists x) \text{Dem}(x, \text{Sub}(n, 17, n))$$

If you have $S$ and $S \implies T$, then $T$ must be true. So, if $S$ **must** be false.

So.

> The consistency of arithmetic cannot be proved *within* arithmatic.
