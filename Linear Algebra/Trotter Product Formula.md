#linear-algebra #math

**When $[A,B]\neq 0$ you cannot exponentiate $A+B$ directly, but alternating small steps of each converges to it: $e^{A+B} = \lim_{n\to\infty}(e^{A/n}e^{B/n})^n$ — the basis of quantum simulation and split-step numerics.**

# Reference

$$
e^{A+B} = \lim_{n\to\infty}\left( e^{A/n}\, e^{B/n} \right)^n
$$

Unlike a truncated series, every partial product is a *product of group elements* and therefore in the group — so Trotter is structure-preserving in the same sense as Magnus ([[Propagators, Time Ordering, and the Dyson Series]]).

**First-order error**, from BCH at each slice, $e^{A/n}e^{B/n} = e^{(A+B)/n + [A,B]/2n^2 + \cdots}$, accumulated over $n$ slices:
$$
\left(e^{A/n}e^{B/n}\right)^n = e^{A+B} + \mathcal{O}\!\left(\frac{[A,B]}{2n}\right)
$$

- Error $\sim \lVert[A,B]\rVert/2n$: linear in the commutator, inverse in step count.
- For $e^{-iHt}$ with $H = \sum_j H_j$: slice $t$ into $n$ steps of $\delta t = t/n$; error per step $\sim \delta t^2$, total $\sim t^2/n$.
- **The error budget is set entirely by the commutators among the terms** — commuting pieces cost nothing, so how you group $H$ into $H_j$ matters as much as how finely you slice.

**Second-order (symmetric / Strang) splitting:**
$$
e^{A/2n}\, e^{B/n}\, e^{A/2n} \qquad \Rightarrow \qquad \text{total error } \mathcal{O}(1/n^2)
$$

- The palindromic arrangement cancels the $[A,B]$ term, leaving double commutators $[A,[A,B]]$, $[B,[B,A]]$.
- **Same cost as first order** when steps are chained — adjacent half-steps merge into full ones.
- Higher orders exist (Suzuki recursion) but step counts grow fast; second order is usually the right choice.

| Order | Product | Error per step | Total error |
|---|---|---|---|
| 1 (Lie–Trotter) | $e^{A\delta}e^{B\delta}$ | $O(\delta^2)$ | $O(t^2/n)$ |
| 2 (Strang) | $e^{A\delta/2}e^{B\delta}e^{A\delta/2}$ | $O(\delta^3)$ | $O(t^3/n^2)$ |
| $2k$ (Suzuki) | recursive nesting | $O(\delta^{2k+1})$ | $O(1/n^{2k})$ |

**Trotter–Kato** extends the limit beyond bounded operators: for generators of strongly continuous semigroups (unbounded $H$, as in real Schrödinger operators) the product still converges, on a suitable common domain. This is what licenses the digital↔continuous correspondence — a gate sequence approximating continuous evolution — rather than merely a matrix identity.

**Relation to the neighbors:** [[Baker-Campbell-Hausdorff]] merges a product into one exponential; **Zassenhaus** splits one exponential into a product exactly, and truncating Zassenhaus after two factors *is* first-order Trotter. Trotter is the numerical face of the same algebra ([[Solving Dynamics on Closed Lie Algebras]]).

**Where you meet it:** digital quantum simulation (circuit depth vs. Trotter error), split-operator Schrödinger solvers (kinetic in $k$-space, potential in real space, FFT between), and symplectic integrators — leapfrog *is* Strang splitting, which is why it preserves phase-space area ([[Symplectic Group]]).

> [!question]- Why does the symmetric splitting $e^{A\delta/2}e^{B\delta}e^{A\delta/2}$ kill the first-order error?
> The product is palindromic, so it is invariant under reversing the factor order. Reversal flips the sign of $[A,B]$, so the effective generator can contain no odd-order bracket terms — $\tfrac12[A,B]$ must vanish. The first surviving error is the double commutator at $O(\delta^3)$.

# Connections

- [[Baker-Campbell-Hausdorff]] — supplies the error terms Trotter fights; Zassenhaus is the exact splitting
- [[Magnus Expansion]] — the other structure-preserving option: one exponential rather than many
- [[Trotterization (Atlas)]] — the quantum-simulation deployment: $H = \sum H_j$ compiled into gate sequences
- [[Matrix Exponential]] — the object being approximated by interleaved factors
- [[Symplectic Group]] — why leapfrog/Strang integrators conserve phase-space area
- [[Commutators and Anticommutators]] — the error budget is set entirely by these
- [[Solving ODEs Numerically]] — splitting methods among the structure-preserving integrators

---
Source: Nielsen & Chuang §4.7.2; Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 2 (Lie product formula)
