#group-theory #quantum #math

**Bracket every Hamiltonian you can apply with every other, repeatedly, until nothing new appears: the resulting algebra $\mathfrak g$ is the complete set of evolutions the system can undergo, and its size decides both what you can reach and whether you can solve it in closed form.**

# Reference

## Construction and controllability

Given available generators $\{-iH_1, \dots, -iH_k\}$ (drives you can turn on, plus the drift), the **dynamical Lie algebra** is their closure under linear combination and bracketing:
$$\mathfrak g = \mathrm{span}\big\{H_j,\ [H_i,H_j],\ [H_i,[H_j,H_k]],\ \dots\big\}.$$

Why brackets enter — alternating two evolutions generates motion along neither:
$$e^{-iH_1\epsilon}e^{-iH_2\epsilon}e^{iH_1\epsilon}e^{iH_2\epsilon} = e^{-[H_1,H_2]\epsilon^2 + O(\epsilon^3)}$$
so each commutator is a *reachable direction*, and by induction so is every nested bracket. The reachable set of propagators is exactly $e^{\mathfrak g}$.

**Controllability is a dimension count:** a system of Hilbert dimension $n$ is universally controllable iff $\mathfrak g = \mathfrak{su}(n)$ (or $\mathfrak u(n)$), i.e. $\dim \mathfrak g = n^2-1$. One qubit: $\sigma_x$ and $\sigma_z$ suffice, since $[\sigma_x,\sigma_z]\propto\sigma_y$ closes $\mathfrak{su}(2)$. The same criterion on two-qubit drives plus a coupling is the algebraic content of [[Universal Gate Sets]].

**Controllability and solvability trade off against each other.** $\mathfrak g = \mathfrak{su}(2^N)$ gives universality but no closed form (exponentially many coefficients); a small $\mathfrak g$ gives closed form but restricted reach.

## Subalgebra vs. ideal — the distinction to be solid on

| | Condition | What it gives you |
|---|---|---|
| **Subalgebra** $\mathfrak h \subseteq \mathfrak g$ | $[\mathfrak h, \mathfrak h] \subseteq \mathfrak h$ | closed under its *own* brackets — a self-contained sub-dynamics you can restrict to |
| **Ideal** $\mathfrak h \subseteq \mathfrak g$ | $[\mathfrak g, \mathfrak h] \subseteq \mathfrak h$ | closed under bracketing with **everything** — the quotient $\mathfrak g/\mathfrak h$ exists |

Only ideals give quotients. **This is the whole reason a truncation is or is not legitimate:** discarding a set of operators is consistent only if what you discard is an ideal, so that brackets can never feed it back into what you kept. Truncating by degree in $(\hat a, \hat a^\dagger)$ fails precisely because the high-degree terms are *not* an ideal — brackets of low-degree operators regenerate them. Grading by a quantity that the bracket adds does work; see [[Graded and Filtered Lie Algebras]] and [[Weyl Algebra and Degree Filtration]].

"Exact at a given order" is a statement about a quotient: you have computed in $\mathfrak g/\mathfrak h$ and the neglected $\mathfrak h$ is an ideal whose contribution is controlled.

## Nilpotent vs. solvable — the two termination conditions

Both are defined by a chain that must reach zero, and they are *not* the same chain:

| | Series | Nilpotent / solvable if | Consequence |
|---|---|---|---|
| **Nilpotent** | lower central: $\mathfrak g^{0} = \mathfrak g$, $\;\mathfrak g^{k+1} = [\mathfrak g, \mathfrak g^{k}]$ | $\mathfrak g^{k} = 0$ for some $k$ | BCH **terminates**; Magnus terminates; $\mathrm{ad}$-nilpotent, so $e^{\mathrm{ad}}$ is a finite sum |
| **Solvable** | derived: $\mathfrak g^{(0)} = \mathfrak g$, $\;\mathfrak g^{(k+1)} = [\mathfrak g^{(k)}, \mathfrak g^{(k)}]$ | $\mathfrak g^{(k)} = 0$ for some $k$ | Wei–Norman system is triangular: **quadratures only**, no nonlinear step |

Nilpotent $\Rightarrow$ solvable, not conversely. Nilpotent is the one you want: it buys exact, non-perturbative results at *any* drive strength.

## The closure table — what each case buys

| $\mathfrak g$ is | Test | Method available |
|---|---|---|
| abelian | all $[H_i,H_j] = 0$ | $U = \exp\!\int A\,dt$ exactly ([[Propagators, Time Ordering, and the Dyson Series]]) |
| nilpotent | lower central series dies | BCH/Magnus terminate; explicit integrals of the drive |
| solvable | derived series dies | Wei–Norman by quadrature alone |
| $\mathfrak{su}(2)$ or $\mathfrak{su}(1,1)$ | 3-dimensional, closes | Wei–Norman: one Riccati + quadratures; or solve $2\times2$ |
| quadratic ($\mathfrak{sp}(2n,\mathbb R)$) | closes, finite | symplectic moment propagation ([[Symplectic Group]]) |
| finite but large | closes, $\dim \mathfrak g = d$ | $d$ coupled scalar ODEs, independent of Hilbert dimension |
| unbounded | never closes | truncated [[Magnus Expansion]], or numerics |

Methods for each: [[Solving Dynamics on Closed Lie Algebras]].

## The small algebras that actually appear

| Algebra | Basis | Type | Why it matters |
|---|---|---|---|
| $\mathfrak h_3$ (Heisenberg) | $\{a, a^\dagger, \mathbb 1\}$ | nilpotent, depth 2 | $[a,a^\dagger]=\mathbb 1$ is central, so brackets die immediately — displacements compose cleanly ([[Displacement Operator]]) |
| $\mathrm{osc}$ | $\mathfrak h_3 \rtimes \{a^\dagger a\}$ | solvable | free oscillator plus any linear drive |
| $\mathfrak{sp}(2,\mathbb R) \cong \mathfrak{su}(1,1)$ | $\{a^2, a^{\dagger 2}, a^\dagger a\}$ | simple, non-compact | the quadratic/squeezing sector; where anomalous $a^2, a^{\dagger 2}$ terms live |
| quadratic + linear | $\{1, a, a^\dagger, a^2, a^{\dagger 2}, a^\dagger a\}$ | 6-dimensional, closes | *all* Gaussian evolution — squeezers, beamsplitters, [[Ray Transfer Matrices\|ABCD optics]]. One cubic term destroys it |
| $\mathfrak{su}(2)$ | $\{S_x, S_y, S_z\}$ | simple, compact | every driven spin is three scalar ODEs; the [[Bloch Sphere]] |
| spin $\rtimes$ displacement | $\sigma_\phi \otimes \{a, a^\dagger, \mathbb 1\}$ | nilpotent (semidirect) | the [[Molmer-Sorensen Gate]] at $\delta_c = 0$ — the exactly-solvable point to expand around |

Note the **semidirect product** $\rtimes$: one factor acts on the other rather than commuting with it. The MS structure is spin acting on displacement, which is why the result is a *spin-dependent* displacement.

**Caveat on where your operators live.** Escalating products of $a, a^\dagger$ do not sit in a finite-dimensional Lie algebra at all — they live in the [[Universal Enveloping Algebra and PBW Basis|universal enveloping algebra]] (concretely, the Weyl algebra). Saying "the algebra closes" is a claim about a finite-dimensional Lie algebra; saying "the operators close under multiplication" is a different and weaker claim.

**The practical test, in order:** write $H(t) = \sum_j f_j(t) H_j$; bracket the $H_j$ pairwise; if new operators appear, bracket again. Terminates quickly → exact by Wei–Norman or Magnus. Grows without bound → perturbation theory, numerics, or a frame chosen to shrink the effective algebra ([[Rotating Wave Approximation (Atlas)]] is an algebra truncation in disguise).

> [!question]- A force gate has $H(t) = f(t)\,\sigma_\phi\,(a e^{-i\delta t} + a^\dagger e^{i\delta t})$. Bracket it with itself at two times — what is guaranteed before any calculation?
> $[H(t_1), H(t_2)]$ is a c-number times $\sigma_\phi^2 = \mathbb 1$, which is central: the algebra is $\mathfrak h_3$-like, nilpotent at depth two. So Magnus terminates exactly at $\Omega_2$ — a spin-dependent displacement plus a spin-dependent phase, for *any* envelope $f(t)$ and any drive strength.

# Connections

- [[Solving Dynamics on Closed Lie Algebras]] — the solution methods once closure is established
- [[Subalgebras, Ideals, and Quotients]] — the ideal condition and what quotients mean
- [[Graded and Filtered Lie Algebras]] — when a degree truncation is legitimate
- [[Lie Algebras (Atlas)]] — structure constants, $\mathrm{ad}$, the general framework
- [[Magnus Expansion]] — termination under nilpotency as the exactness mechanism
- [[Baker-Campbell-Hausdorff]] — the bracket as a reachable direction
- [[Conjugation]] — $\mathrm{ad}$-nilpotency; the adjoint action the closure respects
- [[Displacement Operator]] / [[Molmer-Sorensen Gate]] — $\mathfrak h_3$ cashed in
- [[Universal Gate Sets]] — controllability as $\mathfrak g = \mathfrak{su}(2^N)$
- [[The Classical Groups Reference]] — which group each closed algebra generates

---
Source: d'Alessandro, *Introduction to Quantum Control and Dynamics*, Ch. 3; Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 3 (nilpotent and solvable)
