#linear-algebra #math

**The bookkeeping for multiplying exponentials of noncommuting operators: $e^Ae^B = e^{A+B+\frac{1}{2}[A,B]+\cdots}$ — everything past $A+B$ is built from nested commutators.** The $\tfrac{1}{2}[A,B]$ term is the leading correction and, physically, where geometric phases come from.

# Reference

$$
e^A e^B = \exp\!\Big( A + B + \tfrac{1}{2}[A,B] + \tfrac{1}{12}[A,[A,B]] - \tfrac{1}{12}[B,[A,B]] + \cdots \Big)
$$

**Glauber/disentangling special case** — when $[A,B]$ commutes with both $A$ and $B$ (i.e. $[A,[A,B]] = [B,[A,B]] = 0$), the series terminates:

$$
e^A e^B = e^{A+B}\, e^{\frac{1}{2}[A,B]}
\qquad\Longleftrightarrow\qquad
e^{A+B} = e^A e^B e^{-\frac{1}{2}[A,B]}
$$

This is the ladder-operator case ($[a, a^\dagger] = 1$): normal-ordering displacement operators, composing phase-space displacements. Composing $D(\alpha)D(\beta) = e^{(\alpha\beta^* - \alpha^*\beta)/2} D(\alpha+\beta)$ — the phase is $\tfrac{1}{2}[A,B]$, i.e. the **area enclosed in phase space**, the geometric phase that powers the MS gate.

**Braiding/adjoint identity** (technically the BCH lemma, used even more often):

$$
e^A B e^{-A} = B + [A,B] + \frac{1}{2!}[A,[A,B]] + \frac{1}{3!}[A,[A,[A,B]]] + \cdots
$$

This is how you transform operators into rotating frames, interaction pictures, and dressed bases. If $[A,B] = \lambda B$ (eigenoperator), it sums to $e^{\lambda} B$ — the reason $e^{i\theta n}a e^{-i\theta n} = e^{-i\theta}a$ in one line. Written as $e^{\mathrm{ad}_A}B$, the cases where it collapses are catalogued on [[Conjugation]].

**When does the series terminate?** Not for small $[A,B]$ — for **ad-nilpotency**, i.e. nested brackets dying at finite depth:

| Condition | Result |
|---|---|
| $[A,B] = 0$ | $e^Ae^B = e^{A+B}$ |
| $[A,B]$ central (c-number) | Glauber form above — exact, two terms |
| $\mathrm{ad}^n = 0$ for some $n$ (nilpotent algebra) | finite sum, exact at any strength |
| algebra closes but is not nilpotent | series is infinite; use Wei–Norman instead ([[Solving Dynamics on Closed Lie Algebras]]) |

Convergence in general requires $\lVert A\rVert + \lVert B\rVert$ small enough; the time-dependent analog is the Moan–Niesen bound on the [[Magnus Expansion]].

**Zassenhaus — the dual direction.** BCH merges a product into one exponential; Zassenhaus splits one exponential into a product:
$$e^{t(A+B)} = e^{tA}\, e^{tB}\, e^{-\frac{t^2}{2}[A,B]}\, e^{\frac{t^3}{6}\left(2[B,[A,B]] + [A,[A,B]]\right)} \cdots$$
Truncating after the first two factors is exactly the first-order [[Trotter Product Formula]], so the $-\tfrac{t^2}{2}[A,B]$ factor *is* the Trotter error term made explicit.

> [!question]- Why does composing two displacement operators pick up a phase, and what does the phase equal geometrically?
> $D(\alpha)D(\beta)$: the exponents' commutator $[\alpha a^\dagger - \alpha^* a,\, \beta a^\dagger - \beta^* a] = \alpha\beta^* - \alpha^*\beta$ is a c-number, so Glauber applies and the phase $e^{(\alpha\beta^*-\alpha^*\beta)/2}$ survives. Its argument = twice the signed area of the phase-space triangle swept — enclosed area = geometric phase (the MS-gate mechanism).

# Connections

- [[Matrix Exponential]] — the object being multiplied; BCH is its noncommutative product rule
- [[Displacement Operator]] — the canonical Glauber-case application: phase-space displacements compose with an area phase
- [[Trotter Product Formula]] — BCH truncated at $\frac{1}{2}[A,B]$ gives the Trotter error term
- [[Free Algebras, Words, and Gradings]] — why the coefficients are universal: the series lives in the free Lie algebra
- [[Multilinear Maps and Polarization]] — each bracket-word as a map with slots you can fill separately
- [[Magnus Expansion]] — the time-ordered continuous generalization; $\Omega_2$ in place of $\frac12[A,B]$
- [[Conjugation]] — the adjoint identity as $e^{\mathrm{ad}_A}$, with the cases that collapse
- [[Solving Dynamics on Closed Lie Algebras]] — disentangling identities: BCH resummed exactly on small algebras
- [[Commutators and Anticommutators]] — the algebra all correction terms are made of
- [[Molmer-Sorensen Gate]] — the enclosed-area phase used as an entangling gate

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 5; Gerry & Knight App. D (Glauber form).
