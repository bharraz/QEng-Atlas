#linear-algebra #math

**Every normal matrix is a weighted sum of orthogonal projectors onto its eigenspaces — the license to think of an operator as "its eigenvalues, sitting on its eigenvectors."** This is why diagonalizing the Hamiltonian solves the problem: the operator falls apart into independent 1D pieces.

# Reference

For $A$ normal ($[A, A^\dagger] = 0$), there is an orthonormal eigenbasis $\{|v_i\rangle\}$:

$$
A = \sum_i \lambda_i\, |v_i\rangle\langle v_i| = U D U^\dagger
$$

where the $|v_i\rangle\langle v_i|$ are orthogonal [[Projectors]] resolving the identity, $\sum_i |v_i\rangle\langle v_i| = \mathbb{1}$. With degeneracy, group terms into $A = \sum_k \lambda_k P_k$ with $P_k$ projecting onto each eigenspace.

**Functions of operators** — the theorem's killer app. Define $f(A)$ by acting on eigenvalues only:

$$
f(A) = \sum_i f(\lambda_i)\, |v_i\rangle\langle v_i|
$$

This is how $e^{-iHt/\hbar}$, $\sqrt{\rho}$, $\log\rho$, and $H^{-1}$ actually get computed: diagonalize once, apply $f$ to the diagonal, transform back. Consistency check: $f(A)$ commutes with $A$ and shares its eigenbasis.

**Scope:** Hermitian, unitary, anti-Hermitian — all normal, all covered. Non-normal matrices get the weaker [[Diagonalization]] story (skewed eigenbasis, or Jordan blocks). Infinite dimensions add continuous spectrum: sums become integrals, $x$ and $p$ live there.

> [!question]- Why does $f(A) = \sum_i f(\lambda_i)|v_i\rangle\langle v_i|$ reproduce the power series definition of $e^A$?
> Projector orthogonality gives $A^n = \sum_i \lambda_i^n |v_i\rangle\langle v_i|$ (cross terms vanish). Sum the series term by term and it collects into $\sum_i e^{\lambda_i}|v_i\rangle\langle v_i|$ — the series acts on each eigenvalue independently.

# Connections

- [[Normal Matrices]] — the exact class the theorem covers, no more, no less
- [[Projectors]] — the building blocks; spectral decomposition = eigenvalues weighting a projector resolution of identity
- [[Matrix Exponential]] — $f(A)$ with $f = \exp$: the diagonal-case shortcut lives here
- [[Hermitian Matrices]] — observables: outcomes are the $\lambda_i$, Born-rule probabilities come from the $P_i$
- [[Simultaneous Diagonalization]] — extending to two operators at once, when they commute

---
Source: Axler, *Linear Algebra Done Right*, Ch. 7; Nielsen & Chuang §2.1.6.
