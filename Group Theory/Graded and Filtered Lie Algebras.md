#group-theory #math

**You often organize operators by an index — photon number, order in a small parameter, operator degree — and drop everything above a cutoff; whether that is exact or an uncontrolled approximation depends on one property: does the commutator of two pieces land exactly at the sum of their indices (a grading), or only somewhere at or below it (a filtration)?** **In practice:** check what the commutator does to your index. If it adds (with non-negative indices), everything above the cutoff forms an ideal and truncation is an exact quotient; if it can drop, truncation needs a separate physical argument.

# Reference

**Formally:** grading means the bracket *adds* the index, $[\mathfrak g_m, \mathfrak g_n] \subseteq \mathfrak g_{m+n}$; filtration means only that it does not exceed it — and the difference decides whether cutting off at some index is an exact quotient or an uncontrolled approximation.

**Picture:** a ladder of operator classes: a commutator lands exactly on the rung given by the sum (grading) or possibly lower (filtration), and only in the first case can you cut off the top of the ladder without anything falling back down.

| | Definition | Bracket rule |
|---|---|---|
| **Graded** | $\mathfrak g = \bigoplus_n \mathfrak g_n$, a direct sum of independent pieces | $[\mathfrak g_m, \mathfrak g_n] \subseteq \mathfrak g_{m+n}$ |
| **Filtered** | $F_0 \subseteq F_1 \subseteq F_2 \subseteq \cdots$, nested and exhausting $\mathfrak g$ | $[F_m, F_n] \subseteq F_{m+n}$ |

A grading always induces a filtration, $F_n = \bigoplus_{m \leq n}\mathfrak g_m$. The converse fails: a filtration remembers only "degree at most $n$," with no canonical way to name the piece of degree *exactly* $n$.

**Grading is the stronger statement, and it is the one that licenses truncation.** For a grading by non-negative integers, let $\mathfrak g_{\geq N} = \bigoplus_{n \geq N}\mathfrak g_n$. Then
$$[\mathfrak g_m,\; \mathfrak g_{\geq N}] \subseteq \mathfrak g_{\geq N+m} \subseteq \mathfrak g_{\geq N} \qquad (m \geq 0),$$
so **$\mathfrak g_{\geq N}$ is an ideal**: brackets push you *up* the grading, never back down into what you kept. Truncating at degree $N$ is then literally passing to the quotient $\mathfrak g/\mathfrak g_{\geq N}$, and the result is exact in the sense that quotients are exact ([[Subalgebras, Ideals, and Quotients]]).

**When the bracket can lower the index, the high part is not an ideal and truncation fails.** If $[F_m, F_n] \subseteq F_{m+n-2}$ — the Weyl-algebra case — then bracketing a low-degree element with a high-degree one produces something of *lower* degree, which lands back inside the sector you retained. The discarded terms feed the kept terms, and the error is uncontrolled at every subsequent order ([[Weyl Algebra and Degree Filtration]]).

**The test, stated once:** ask whether the bracket **adds** your bookkeeping index.

- **Adds** → genuine grading → cutoff is an ideal → truncation is a quotient, exact at that order.
- **Can subtract** → filtration only → cutoff is not an ideal → truncation is not justified by algebra, and needs a separate physical argument (scale separation, averaging, a convergence bound).

This is why grading by a physically conserved increment works where grading by operator degree does not. Choose the index to be a quantity the bracket *accumulates* — a detuning, an excitation-number difference, a power of a small parameter — rather than a size measure like polynomial degree.

## The associated graded algebra

Given a filtration, the **associated graded** algebra is
$$\mathrm{gr}(\mathfrak g) = \bigoplus_n F_n / F_{n-1},$$
each piece being "degree exactly $n$, modulo everything below." This is the standard device for turning a filtered object into a graded one you can compute in. The induced bracket on $\mathrm{gr}$ keeps only the part of $[X,Y]$ that sits at the top filtration level and discards the rest.

**A commonly missed consequence:** if the bracket *strictly lowers* the index, then the top-level part is zero, so **the induced bracket on $\mathrm{gr}(\mathfrak g)$ vanishes and $\mathrm{gr}$ is commutative.** A commutative associated graded is a precise signal that your filtration is not a Lie grading — the graded object has thrown the bracket away entirely. Two instances:

| Filtered object | Filtration | $\mathrm{gr}$ | Reading |
|---|---|---|---|
| Weyl algebra $A_1$ | Bernstein (degree in $a, a^\dagger$) | $\mathbb C[x,\xi]$, commutative | the classical phase-space limit |
| $U(\mathfrak g)$ | degree in the generators | $\mathrm{Sym}(\mathfrak g)$, commutative | the PBW theorem ([[Universal Enveloping Algebra and PBW Basis]]) |

In both cases $\mathrm{gr}$ is where the *classical* content lives: commutators become Poisson brackets at the next filtration level down, and that is the classical limit.

## Gradings that appear in physics

| Grading index | $\mathfrak g_n$ | Bracket adds it? | Use |
|---|---|---|---|
| Root lattice | root spaces $\mathfrak g_\alpha$, with $[\mathfrak g_\alpha, \mathfrak g_\beta] \subseteq \mathfrak g_{\alpha+\beta}$ | yes | the root-space decomposition *is* a grading ([[Cartan Subalgebras, Roots, and Weights]]) |
| Weight / excitation-number change | operators shifting $n$ by a fixed amount | yes | selection rules; which terms can connect which states |
| Detuning or frequency offset | terms oscillating as $e^{i n \delta t}$ | yes | [[Rotating Wave Approximation (Atlas)]] as a grading truncation, discarding $\lvert n\rvert \geq 1$ |
| Order in a small parameter $\lambda$ | $\lambda^n$ coefficients | yes | perturbation theory; each order is a quotient |
| Polynomial degree in $(a, a^\dagger)$ | monomials of degree $n$ | **no** — drops by 2 | filtration only; truncation not licensed |

The rotating-wave row is worth stating plainly: RWA is legitimate *as algebra* when the discarded terms are graded by a nonzero frequency index, because that index adds under bracketing and the fast sector is an ideal. Its error is then controlled by scale separation rather than by algebraic exactness.

> [!question]- Your bookkeeping index drops by 2 under every bracket. What breaks, and what do you do instead?
> "Degree $\geq N$" stops being an ideal, so brackets of retained terms regenerate discarded ones and truncation has no algebraic justification. Re-grade by a quantity the bracket adds — a detuning, an excitation-number change, a power of the small parameter — and cut on that index instead.

# Connections

- [[Subalgebras, Ideals, and Quotients]] — the ideal condition used here; why quotients need it
- [[Weyl Algebra and Degree Filtration]] — the worked failure case, in full
- [[Universal Enveloping Algebra and PBW Basis]] — $\mathrm{gr}(U(\mathfrak g)) = \mathrm{Sym}(\mathfrak g)$ as a graded statement
- [[Cartan Subalgebras, Roots, and Weights]] — the root-space decomposition as a grading
- [[Dynamical Lie Algebras and Closure]] — closure and truncation as the two ways an algebra stays finite
- [[Rotating Wave Approximation (Atlas)]] — frequency grading, and what controls its error
- [[Magnus Expansion]] — order-by-order truncation as a grading in the small parameter
- [[Lie Algebras (Atlas)]] — structure constants and the bracket being graded

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 3; Björk, *Rings of Differential Operators*, Ch. 1 (filtrations and associated graded)
