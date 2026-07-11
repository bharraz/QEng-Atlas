#linear-algebra #math

**Can't exponentiate $A+B$ when $[A,B]\ne 0$? Alternate small steps of each: $e^{A+B} = \lim_{n\to\infty}(e^{A/n}e^{B/n})^n$.** Slicing time finely enough makes the noncommutativity error vanish — the backbone of quantum simulation and split-step numerics.

# Reference

$$
e^{A+B} = \lim_{n\to\infty}\left( e^{A/n}\, e^{B/n} \right)^n
$$

**First-order error**, from BCH at each slice ($e^{A/n}e^{B/n} = e^{(A+B)/n + [A,B]/2n^2 + \cdots}$), accumulated over $n$ slices:

$$
\left(e^{A/n}e^{B/n}\right)^n = e^{A+B} + \mathcal{O}\!\left(\frac{[A,B]}{2n}\right)
$$

Error $\sim \|[A,B]\|/2n$: linear in the commutator, inverse in step count. For $e^{-iHt}$ with $H = \sum_j H_j$, slice $t$ into $n$ steps of $\delta t = t/n$; error per step $\sim \delta t^2$, total $\sim t^2/n$.

**Second-order (symmetric / Strang) splitting** — nearly free upgrade:

$$
e^{A/2n}\, e^{B/n}\, e^{A/2n} \;\Rightarrow\; \text{total error } \mathcal{O}(1/n^2)
$$

The palindromic arrangement cancels the $[A,B]$ term (leaves double commutators $[A,[A,B]]$, $[B,[B,A]]$). Same cost as first order when steps are chained — adjacent half-steps merge. Higher orders exist (Suzuki recursion) but with rapidly growing step counts; in practice second order is the sweet spot.

**Where you meet it:** digital quantum simulation (circuit depth vs Trotter error tradeoff), split-operator Schrödinger solvers (kinetic in $k$-space, potential in real space, FFT between), and symplectic integrators (leapfrog *is* Strang splitting).

> [!question]- Why does the symmetric splitting $e^{A/2}e^{B}e^{A/2}$ kill the first-order error term?
> It's time-reversal symmetric: swapping $A\leftrightarrow$ its halves and reversing order gives the same product, so the effective exponent's expansion can contain no *even* powers of... rather, no terms antisymmetric under $(A,B)\to(-A,-B)$ reversal — the $\frac{1}{2}[A,B]$ term is odd under reversal and must vanish. First surviving error is third-order per step.

# Connections

- [[Baker-Campbell-Hausdorff]] — supplies the error terms Trotter is fighting; truncate BCH to see the $[A,B]/2n$
- [[Trotterization]] — the quantum-simulation deployment: $H = \sum H_j$ compiled into gate sequences
- [[Matrix Exponential]] — the object being approximated by interleaved factors
- [[Commutators and Anticommutators]] — error budget is set entirely by the commutators among terms

---
Source: Nielsen & Chuang §4.7.2; Hall, *Lie Groups, Lie Algebras*, Ch. 2 (Lie product formula).
