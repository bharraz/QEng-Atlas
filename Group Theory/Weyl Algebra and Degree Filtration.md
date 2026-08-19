#group-theory #math

**The Weyl algebra $A_1$ is the algebra of all polynomials in $a$ and $a^\dagger$ — the correct name for "escalating products of ladder operators" — and its degree filtration is not a Lie grading, which is exactly why truncating in operator degree fails.**

# Reference

$$A_1 = \mathbb C\langle a, a^\dagger\rangle \big/ \big([a, a^\dagger] = 1\big)$$

Equivalently $\mathbb C\langle x, \partial_x\rangle$ with $[\partial_x, x] = 1$: the algebra of differential operators with polynomial coefficients. Basic facts:

- **Associative, not a finite-dimensional Lie algebra.** Infinite-dimensional as a vector space. This is the distinction that matters when you ask whether something "closes" ([[Dynamical Lie Algebras and Closure]]).
- **Simple** — no nontrivial two-sided ideals — and has no zero divisors.
- **Normal ordering gives a basis:** $\{(a^\dagger)^m a^n\}_{m,n \geq 0}$. Every expression reduces to a unique normally ordered form by repeated use of $aa^\dagger = a^\dagger a + 1$.
- **It contains the Heisenberg Lie algebra** $\mathfrak h_3 = \{a, a^\dagger, \mathbb 1\}$ as the degree-$\leq 1$ part, and $A_1 = U(\mathfrak h_3)/(z - 1)$ — the enveloping algebra of $\mathfrak h_3$ with the central generator set to $1$ ([[Universal Enveloping Algebra and PBW Basis]]).

## The Bernstein filtration

Assign $\deg a = \deg a^\dagger = 1$ and let $F_n$ = operators of total degree $\leq n$, so $\dim F_n = \binom{n+2}{2} = \tfrac12(n+1)(n+2)$. **This is the "degree in $(\hat a, \hat a^\dagger)$" that operator-ordering calculations count.** The filtration is exhaustive and nested, $F_0 \subseteq F_1 \subseteq \cdots$, with $F_m \cdot F_n \subseteq F_{m+n}$ for the *product*.

**But the bracket lowers degree by two:**
$$[F_m, F_n] \subseteq F_{m+n-2}$$
because each contraction $[a, a^\dagger] = 1$ removes one $a$ and one $a^\dagger$. The cheapest instance: $a$ and $a^\dagger$ both have degree 1, and $[a, a^\dagger] = 1$ has degree 0.

Two consequences, and they are the point of the page:

**1. "Degree $\geq N$" is not an ideal, so degree truncation is not a quotient.** Take $X$ of degree 1 and $Y$ of degree $N$: $[X, Y]$ has degree $N-1$, which sits in the sector you *kept*. Discarded high-degree operators therefore feed back into the retained low-degree ones under bracketing, and the error is uncontrolled at every subsequent order. Contrast a genuine grading, where brackets only push you further up and the tail *is* an ideal ([[Graded and Filtered Lie Algebras]], [[Subalgebras, Ideals, and Quotients]]).

**2. The associated graded is a commutative polynomial ring.** Because the bracket strictly lowers the filtration index, the induced bracket on $\mathrm{gr}(A_1) = \bigoplus_n F_n/F_{n-1}$ vanishes identically:
$$\mathrm{gr}(A_1) \;\cong\; \mathbb C[x, \xi], \qquad \text{commutative}$$
Passing to the associated graded throws the commutator away entirely — which is a clean statement that the degree filtration is *not* a Lie grading. It is also the classical limit: $\mathbb C[x,\xi]$ is the ring of polynomial functions on phase space, and the commutator reappears one filtration level down as the Poisson bracket,
$$\tfrac{1}{i\hbar}[\hat A, \hat B] \;\longrightarrow\; \{A, B\}_{\text{PB}}.$$
This is the algebraic skeleton of the Wigner–Weyl symbol calculus: $A_1$ with its Moyal product deforms $\mathbb C[x,\xi]$, and $\hbar$ is the deformation parameter that reinstates the bracket the grading discarded.

## What to do instead

| Situation | Move |
|---|---|
| Want a legitimate cutoff | re-grade by a quantity the bracket **adds** — detuning index, excitation-number change, power of a small parameter |
| Want the algebra to close | restrict to a finite-dimensional Lie subalgebra of $A_1$: $\mathfrak h_3$ (degree $\leq 1$), $\mathfrak{su}(1,1)$ (the quadratic part), or the 6-dimensional quadratic-plus-linear algebra |
| Want exact time evolution | check closure first, then Wei–Norman or Magnus ([[Solving Dynamics on Closed Lie Algebras]]) |
| Want a controlled approximation anyway | justify it physically — scale separation, a convergence bound, or an averaging argument — not algebraically |

**The finite-dimensional Lie subalgebras of $A_1$ worth knowing:**

| Subalgebra | Span | Degree | Type |
|---|---|---|---|
| $\mathfrak h_3$ | $\{a, a^\dagger, \mathbb 1\}$ | $\leq 1$ | nilpotent — brackets die at depth 2 |
| $\mathrm{osc}$ | $\mathfrak h_3 \rtimes \{a^\dagger a\}$ | $\leq 2$ | solvable |
| $\mathfrak{su}(1,1)$ | $\{a^2, a^{\dagger 2}, a^\dagger a\}$ | $2$ | simple, non-compact ([[Symplectic Group]]) |
| quadratic + linear | all of $F_2$ | $\leq 2$ | 6-dimensional, closes — *all* Gaussian evolution |

**$F_2$ closes under the bracket and $F_3$ does not.** Since $[F_2, F_2] \subseteq F_2$, degree-$\leq 2$ is a genuine Lie subalgebra — the reason every quadratic Hamiltonian is exactly solvable. Adding one cubic term breaks it: $[F_3, F_3] \subseteq F_4$, which is strictly larger, and iterating generates all of $A_1$. That single step is the boundary between Gaussian and non-Gaussian, integrable and not.

> [!question]- Why does an exact result exist for any quadratic Hamiltonian but not after adding one cubic term?
> $[F_2, F_2] \subseteq F_2$, so degree $\leq 2$ is a closed 6-dimensional Lie algebra and Wei–Norman applies. Cubic terms give $[F_3, F_3] \subseteq F_4$; bracketing repeatedly never terminates and generates all of $A_1$, so no finite-dimensional closure and no closed form.

# Connections

- [[Graded and Filtered Lie Algebras]] — the grading-vs-filtration distinction this instantiates
- [[Subalgebras, Ideals, and Quotients]] — why a non-ideal cutoff cannot be quotiented
- [[Universal Enveloping Algebra and PBW Basis]] — $A_1 = U(\mathfrak h_3)/(z-1)$; PBW as the ordering theorem
- [[Dynamical Lie Algebras and Closure]] — closure inside $A_1$; $F_2$ as the solvable ceiling
- [[Solving Dynamics on Closed Lie Algebras]] — methods once you have restricted to a closed subalgebra
- [[Symplectic Group]] — the quadratic sector as $\mathfrak{sp}(2,\mathbb R) \cong \mathfrak{su}(1,1)$
- [[Displacement Operator]] / [[Squeezed States]] — degree 1 and degree 2 exponentiated
- [[Commutators and Anticommutators]] — $[a, (a^\dagger)^n] = n(a^\dagger)^{n-1}$, the degree-lowering rule in action

---
Source: Björk, *Rings of Differential Operators*, Ch. 1; Coutinho, *A Primer of Algebraic D-modules*, Ch. 1–3
