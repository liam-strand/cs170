# September 8th: Paradoxes and Consistency

## Early, important paradoxes
* Lewis Carroll fucking around with logic
* Georg Cantor fucking around with the set of all sets
  * There's another diagonalization proof hiding in here
  * You get a proof of two different infinities, just like the normal b10 proof. This is just b2
* Bertram Russel started fucking with the core of set theory's consistency
  * Take the set of all sets that do not contain themselves
  * Does that set contain itself?
  * Everyone's getting all worried
* Jules Richard kinda goes off the deep end 
  * Consider a language in which the properties of cardinal numbers can be formulated and defined...like English
  * Just go and list all of these properties
  * Then sort them by the character length of the property
  * Now add the property that a number has the property described by its associated definition
  * Now add the inverse property
    * Ok just call that inverse property Richardian for convenience
  * When we do that the number that is associated with the Richardian property can't be Richardian or not Richardian

## Principia Mathematica
### We need an **absolute** proof of consistency
* Throw away first-order logic and go to weaker, simpler propositional logic
  * We don't have $\exists$ or $\forall$
  * Formulas instead of relations
  * Two deduction rules: substitution adn detachment
  * 4 axioms:
    * $(p \lor p) \implies p$
    * $p \implies (p \lor p)$
    * $(p \lor q) \implies (q \lor p)$
    * $(p \implies q) \implies ((r \lor p) \implies (r \lor q))$
  * The 4 axioms can deduce the following, very dangerous, forumula: $p \implies (\lnot p \implies q)$
    * If we ever prove that anything is equivelant to its negation, you can prove that anything is true.

### Abreviated Proof of Propositional Logic's Consistency
* We want to prove that propositional logic is consistent *using only propositional logic*
* Here's the big thing: *If you can find a formula that is not provable, then the system is consistent*.
* Propositional logic generates universally valid statements.
  * So, we can replace the "provable" in the above claim with "universally valid"
  * So we have: **If you can find a formula that is not provable, then the system is consistent**
* Let's see where we can go:
  1. $p \implies (\lnot p \implies q)$
  2. If the system is inconsistent: anythign is provable
  3. If something is not provable, the system is consistent
  4. If somethign is not universally valid, the system is consistent
  5. $p \lor q$ is not universally valid
  6. The axioms are consistent

### Extensions
* These were easy:
  * Tarski's Plane Geometry
  * Presburger (6-year-old) Arithmetic
  * Skolem Arithmetic
* Peano Arithmetic was trickier
  * All we want is to prove that addition and multiplication are consistent
  * You'd think that wouldn't be a big problem
* We're going to add another metric of good axioms: Decidability: the ability to trace a statement back to the axioms
