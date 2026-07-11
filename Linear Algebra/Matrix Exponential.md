#linear-algebra #math

**$e^{At}$ solves $\dot{x} = Ax$ — the exponential turns generators into evolution, exactly as in the scalar case, except order now matters.** Every unitary, every propagator, every Lie group element is a matrix exponential of its generator.

# Reference

$$
e^A = \sum_{k=0}^\infty \frac{A^k}{k!} \qquad (\text{converges for any } A)
$$

**Diagonal/diagonalizable case** — the practical route: $A = PDP^{-1} \Rightarrow e^A = P\,\mathrm{diag}(e^{\lambda_i})\,P^{-1}$. Exponentiate eigenvalues, keep eigenvectors.

**The noncommutativity trap:**

$$
e^A e^B \ne e^{A+B} \quad \text{unless } [A,B]=0
$$

The correction terms are organized by [[Baker-Campbell-Hausdorff]]; splitting approximations by [[Trotter Product Formula]]. Corollary that *does* always hold: $e^A e^{-A} = \mathbb{1}$, and $(e^A)^{-1} = e^{-A}$, $\left(e^A\right)^\dagger = e^{A^\dagger}$.

**Derivative:**

$$
\frac{d}{dt} e^{At} = A\,e^{At} = e^{At} A
$$

— only this clean because $A$ commutes with itself. For time-*dependent* $A(t)$ with $[A(t), A(t')] \ne 0$ you need the time-ordered exponential $\mathcal{T}e^{\int A\,dt}$ (Dyson series) — writing $e^{\int A\,dt}$ is the classic mistake.

**Special structure:** $A$ anti-Hermitian ⇒ $e^A$ unitary ($U = e^{-iHt/\hbar}$); $A$ Hermitian ⇒ $e^A$ positive definite. $\det e^A = e^{\mathrm{Tr}A}$.

**Matrix log one-liner:** $\log$ inverts $\exp$ but is multivalued (eigenvalue phases mod $2\pi$) — extracting an "effective Hamiltonian" $H = i\hbar\log U/t$ from a propagator has branch ambiguities once $|E t/\hbar| > \pi$.

> [!question]- When is $e^{A}e^{B} = e^{A+B}$ exactly, and what's the leading error otherwise?
> Exactly iff $[A,B] = 0$ (sufficient always; necessary for generic parameters). Otherwise $e^Ae^B = e^{A+B+\frac{1}{2}[A,B]+\cdots}$ — the leading correction is half the commutator, which is the seed of both BCH and Trotter error.

# Connections

- [[Baker-Campbell-Hausdorff]] — the full bookkeeping of $e^Ae^B$ when $[A,B]\neq0$
- [[Unitary Matrices]] — $e^{-iHt/\hbar}$: Hermitian generator in, unitary evolution out
- [[Trotter Product Formula]] — approximating $e^{A+B}$ by interleaved small steps
- [[Linear ODE Systems]] — $x(t) = e^{At}x_0$: the entire theory of linear dynamics in one symbol
- [[Diagonalization]] — how $e^A$ is actually computed when $A$ is diagonalizable

---
Source: Horn & Johnson, *Topics in Matrix Analysis*, Ch. 6; Hall, *Lie Groups, Lie Algebras*, Ch. 2.
