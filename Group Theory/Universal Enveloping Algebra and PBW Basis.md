#group-theory #math

**A Lie algebra only has brackets, but physics needs products — $J^2$, $H = \chi (a^\dagger a)^2$, any Casimir — and the universal enveloping algebra $U(\mathfrak g)$ is the smallest associative algebra where those products live.**

# Reference

$$U(\mathfrak g) = \frac{\text{free associative algebra on } \mathfrak g}{\big(XY - YX - [X,Y]\big)}$$

Read the quotient as an instruction: *you may multiply generators freely, and the only rule for reordering them is the bracket.* Everything else follows. The numerator — the free associative algebra, all words over the generators with no relations imposed — is defined in [[Free Algebras, Words, and Gradings]].

**Why you need it.** $\mathfrak g$ is a vector space with a bracket; $J_z^2$ is not an element of $\mathfrak{su}(2)$. Any of the following forces you out of $\mathfrak g$ and into $U(\mathfrak g)$:

- Casimirs — $J^2 = J_x^2 + J_y^2 + J_z^2$ is quadratic.
- Nonlinear Hamiltonians — Kerr terms $(a^\dagger a)^2$, anharmonicities, $\chi^{(3)}$ couplings.
- Escalating products from repeated commutation in a non-closing algebra.
- Representation theory itself: a representation of $\mathfrak g$ is the same thing as a module over $U(\mathfrak g)$.

## Poincaré–Birkhoff–Witt

Fix an ordered basis $X_1, \dots, X_d$ of $\mathfrak g$. **PBW:** the ordered monomials
$$X_1^{k_1} X_2^{k_2}\cdots X_d^{k_d}, \qquad k_i \geq 0$$
form a vector-space basis of $U(\mathfrak g)$. So $U(\mathfrak g)$ is "polynomials in the generators, with one fixed ordering convention," and every expression has a unique normal form reached by pushing generators past each other using $XY = YX + [X,Y]$.

- **Normal ordering is PBW in practice.** $\{(a^\dagger)^m a^n\}$ is the PBW basis of $U(\mathfrak h_3)$ with the ordering $a^\dagger \prec a$; reducing to normally ordered form is applying the theorem.
- **PBW is a graded statement.** Filter $U(\mathfrak g)$ by degree in the generators; then $[F_m, F_n] \subseteq F_{m+n-1}$ — the bracket lowers degree — so the associated graded loses the bracket entirely:
$$\mathrm{gr}\,U(\mathfrak g) \cong \mathrm{Sym}(\mathfrak g),$$
the commutative polynomial ring on $\mathfrak g$ ([[Graded and Filtered Lie Algebras]]). PBW is exactly the claim that this graded ring is as large as it could be, i.e. no unexpected collapses. The same mechanism as the Weyl algebra, which is the special case $A_1 = U(\mathfrak h_3)/(z-1)$ ([[Weyl Algebra and Degree Filtration]]).

## The distinction that actually matters

| Claim | Means | Consequence |
|---|---|---|
| "The **Lie algebra** closes" | brackets stay in a finite-dimensional span $\mathfrak g$ | Wei–Norman applies; $\dim\mathfrak g$ scalar ODEs; exact solution |
| "The **operators** close under multiplication" | products stay in $U(\mathfrak g)$ | true always, and nearly vacuous — $U(\mathfrak g)$ is infinite-dimensional |

Saying "my operators form an algebra" is almost always the second, weaker statement. Exact solvability needs the first ([[Dynamical Lie Algebras and Closure]]). State which one you have.

## The center: Casimirs

$$Z\big(U(\mathfrak g)\big) = \{\text{elements commuting with all of } \mathfrak g\} = \text{the Casimir operators}$$

Casimirs are *not* elements of $\mathfrak g$ — they live in its enveloping algebra, which is the precise reason $J^2$ is a legitimate operator while not being an angular momentum component.

- **Schur's lemma** ⇒ a Casimir acts as a scalar on each irreducible representation, so its value **labels** the irrep: $J^2 = j(j+1)$ names the spin-$j$ multiplet.
- **Harish-Chandra:** for semisimple $\mathfrak g$, $Z(U(\mathfrak g))$ is a polynomial ring on $\mathrm{rank}\,\mathfrak g$ independent generators. Hence the count on [[Lie Algebras (Atlas)]]: number of independent Casimirs = rank. $\mathfrak{su}(2)$ (rank 1) has $J^2$ alone; $\mathfrak{su}(3)$ (rank 2) has two.
- **Practical use:** Casimirs are the conserved quantities that survive *any* Hamiltonian built from $\mathfrak g$. Finding them tells you which quantum numbers can never be changed by the drives available, before writing a single equation of motion.

| Algebra | Casimir | Labels |
|---|---|---|
| $\mathfrak{su}(2)$ | $J^2 = J_z^2 + \tfrac12(J_+J_- + J_-J_+)$ | $j(j+1)$ — the spin multiplet |
| $\mathfrak{su}(1,1)$ | $K^2 = K_0^2 - \tfrac12(K_+K_- + K_-K_+)$ | the discrete series; fixes the squeezing sector |
| $\mathfrak h_3$ | the central $\mathbb 1$ itself | $\hbar$; the value set to 1 in $A_1$ |
| Poincaré | $P^2$, $W^2$ | mass and spin — the classification of particles |

That last row is the general pattern worth internalizing: **the Casimirs of a symmetry algebra are the labels of its irreducible representations, so they are the quantum numbers your theory is allowed to have.** Mass and spin are Casimirs of the Poincaré algebra, which is what makes them the complete labels of a free relativistic particle.

> [!question]- $H = \chi(a^\dagger a)^2$ is quartic in $a, a^\dagger$. Where does it live, and does anything close?
> In $U(\mathfrak h_3)$ (equivalently $A_1$), not in any finite-dimensional Lie algebra containing $a, a^\dagger$. But $a^\dagger a$ commutes with $H$, so evolution is diagonal in the Fock basis and solvable that way — closure fails while a *conserved quantity* rescues it. Two different routes to exactness.

# Connections

- [[Weyl Algebra and Degree Filtration]] — $A_1 = U(\mathfrak h_3)/(z-1)$; the same filtration story
- [[Graded and Filtered Lie Algebras]] — $\mathrm{gr}\,U(\mathfrak g) = \mathrm{Sym}(\mathfrak g)$
- [[Dynamical Lie Algebras and Closure]] — Lie-closure vs. product-closure, and why only the first is exact
- [[Subalgebras, Ideals, and Quotients]] — $U(\mathfrak g)$ as a quotient of the free algebra
- [[Cartan Subalgebras, Roots, and Weights]] — highest-weight modules as $U(\mathfrak g)$-modules
- [[Lie Algebras (Atlas)]] — Casimirs and rank, at intro level
- [[Group Representations]] — representations as modules; Schur's lemma
- [[Commutators and Anticommutators]] — the reordering rule PBW runs on

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 9; Humphreys, *Introduction to Lie Algebras and Representation Theory*, §17 (PBW), §23 (center)
