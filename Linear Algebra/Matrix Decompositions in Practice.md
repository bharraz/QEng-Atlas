#linear-algebra #quantum #math

**Every decomposition answers one question — what basis makes this operator simple, and what does "simple" cost — and each row below gains generality by giving up structure.**

# Reference

| Decomposition   | Form                                    | Exists for                     | Preserved                                    | Sacrificed                                           |
| --------------- | --------------------------------------- | ------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------ |
| Spectral        | $A = U\Lambda U^\dagger$                | normal $A$ ($[A,A^\dagger]=0$) | one orthonormal basis, diagonal                      | requires normality                                           |
| Eigen (general) | $A = S\Lambda S^{-1}$                   | diagonalizable $A$             | diagonal                                             | $S$ non-orthogonal, ill-conditioned; fails for defective $A$ |
| **Schur**       | $A = QTQ^\dagger$, $T$ upper triangular | **every** square $A$           | orthonormal basis; eigenvalues on $\mathrm{diag}\,T$ | only triangular, not diagonal                                |
| **SVD**         | $A = U\Sigma V^\dagger$                 | **every** matrix, any shape    | two orthonormal bases, nonneg. diagonal              | input and output bases differ                                |
| Polar           | $A = (UV^\dagger)(V\Sigma V^\dagger)$   | every square $A$               | rotation × positive stretch                          | — (a regrouping of SVD)                                      |

**Picture:** each decomposition rewrites one matrix as a sequence of simple moves (rotate, stretch, shear, permute); the more general the matrix, the less simple the moves you are allowed.

The two that always exist — Schur and SVD — are the two that get used numerically.

**Schur vs. SVD is a one-line distinction with large consequences.** Both sandwich $A$ between unitaries, but:

| | Schur $Q \cdots Q^\dagger$ | SVD $U \cdots V^\dagger$ |
|---|---|---|
| Transform type | similarity ([[Conjugation]]) | equivalence |
| Survives | the spectrum | the singular values |
| Answers questions about | **dynamics** — $A^n$, $e^{At}$, stability | **magnitude** — gain, rank, conditioning, best approximation |

For normal $A$ the two collapse and $\sigma_i = |\lambda_i|$. The gap between them *is* the non-normality.

**Schur's triangle measures non-normality.** In $A = QTQ^\dagger$ the eigenvalues sit on $\mathrm{diag}\,T$; the strictly upper-triangular part vanishes exactly when $A$ is normal (recovering the spectral theorem). Its size quantifies non-orthogonality of the eigenvectors — which is what produces transient growth in a nominally stable system, and what makes eigenvalues an unreliable guide for non-normal operators.

**Why numerics prefers it:** eigenvector matrices $S$ can be arbitrarily ill-conditioned, so $A = S\Lambda S^{-1}$ is a numerically dangerous route to a matrix function; $Q$ is unitary and perfectly conditioned. Library eigensolvers for non-Hermitian matrices compute a Schur form internally (QR algorithm), and `expm` works from Schur or Padé rather than eigenvectors ([[Floating Point and Numerical Error]]).

**Spectral decomposition $A = \sum_a a P_a$ is one theorem doing several jobs:**

| Object | What the eigendata means |
|---|---|
| Observable | eigenvalues are outcomes, projectors give probabilities ([[Operators and Observables]]) |
| Hamiltonian | eigenbasis is stationary; $e^{-iHt/\hbar} = \sum_n e^{-iE_nt/\hbar}\|n\rangle\langle n\|$ — diagonalizing *is* solving the dynamics |
| Density matrix | eigenvalues are populations; positivity ⇔ all $\lambda \geq 0$, the physicality check on [[Quantum State Tomography (Atlas)]] |
| Liouvillian / channel | non-Hermitian, so Schur territory: eigenvalues are decay rates, zero-eigenvector is the steady state ([[Lindblad Master Equation]]) |
| Symmetry sector | commuting operators share an eigenbasis — a symmetry block-diagonalizes $H$ before you diagonalize it ([[Simultaneous Diagonalization]]) |

**Schmidt decomposition** — the SVD of a bipartite amplitude matrix $c_{ij}$:
$$|\psi\rangle = \sum_{ij} c_{ij}|i\rangle_A|j\rangle_B = \sum_{k=1}^{r} \sigma_k\, |u_k\rangle_A |v_k\rangle_B, \qquad \sum_k \sigma_k^2 = 1$$

- $r = 1$ ⇔ product state; any $r>1$ is entangled, no measure needed.
- $\rho_A = \sum_k \sigma_k^2 |u_k\rangle\langle u_k|$, and $\rho_B$ has the *same* eigenvalues — which is why entanglement entropy is symmetric between the halves ([[Entanglement Measures]]).
- Dropping small $\sigma_k$ is the optimal approximation (Eckart–Young) — the compression step of [[Tensor Networks and MPS]], where bond dimension = retained Schmidt rank.
- Pure bipartite states only. No analogous canonical form for three parties or mixed states.

Geometry, Eckart–Young, and the engineering uses of the SVD (MIMO gain, POD/PCA, ill-determined fit parameters, regularized inversion) are in [[Singular Value Decomposition]] and [[Pseudo-Inverse]].

> [!question]- A control loop has all eigenvalues in the left half-plane, yet produces a large transient excursion before settling. Which decomposition explains it?
> Eigenvalues govern asymptotic decay only, and correctly say "stable." For non-normal $A$ the eigenvectors are strongly non-orthogonal, so the state grows before the exponentials take over. $\sigma_{\max}(e^{At})$ bounds the actual excursion; Schur's upper-triangular part measures the non-normality causing it.

# Connections

- [[Singular Value Decomposition]] — the always-exists decomposition; geometry and Eckart–Young
- [[Spectral Theorem]] / [[Hermitian Matrices]] — the normal-matrix case in full
- [[Simultaneous Diagonalization]] — when two operators share the basis
- [[Condition Number]] — $\sigma_{\max}/\sigma_{\min}$, and why $S$ vs $Q$ matters numerically
- [[Pseudo-Inverse]] — SVD-based inversion and regularization
- [[Entanglement Measures]] / [[Tensor Networks and MPS]] — Schmidt coefficients as the compression currency
- [[Matrix Exponential]] — computed via Schur/Padé, not via eigenvectors
- [[Conjugation]] — similarity as the spectrum-preserving transform

---
Source: Trefethen & Bau, *Numerical Linear Algebra*, Lec. 4–5, 24–26; Nielsen & Chuang §2.5 (Schmidt)
