#linear-algebra #math #quantum

**Every decomposition answers one question: what basis makes this operator simple, and what does "simple" cost.** Eigen/spectral asks for a diagonal form and demands normality to get one; Schur gives up diagonal for triangular and always succeeds; SVD gives up a *single* basis — using different ones on input and output — and works on any matrix at all. Choosing correctly is choosing which compromise you can afford.

# Reference

## The hierarchy

| Decomposition   | Form                                    | Exists for                     | What is preserved                                    | What is sacrificed                                           |
| --------------- | --------------------------------------- | ------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------ |
| Spectral        | $A = U\Lambda U^\dagger$                | normal $A$ ($[A,A^\dagger]=0$) | one orthonormal basis, diagonal                      | requires normality                                           |
| Eigen (general) | $A = S\Lambda S^{-1}$                   | diagonalizable $A$             | diagonal                                             | $S$ non-orthogonal, ill-conditioned; fails for defective $A$ |
| **Schur**       | $A = QTQ^\dagger$, $T$ upper triangular | **every** square $A$           | orthonormal basis; eigenvalues on $\mathrm{diag}\,T$ | only triangular, not diagonal                                |
| SVD             | $A = U\Sigma V^\dagger$                 | **every** matrix, any shape    | two orthonormal bases, nonneg. diagonal              | input and output bases differ                                |
| Polar           | $A = (UV^\dagger)(V\Sigma V^\dagger)$   | every square $A$               | rotation × positive stretch                          | — (a regrouping of SVD)                                      |

Reading down the table: each row buys generality by surrendering structure. The two that always exist — Schur and SVD — are the two that get used numerically.

## Schur decomposition

$$A = Q T Q^\dagger, \qquad Q \text{ unitary}, \quad T \text{ upper triangular}, \quad T_{ii} = \lambda_i.$$

Every square matrix has one. The eigenvalues sit on the diagonal; the strictly upper-triangular part measures **how far $A$ is from normal** (it vanishes exactly when $A$ is normal, recovering the spectral theorem). That residual is not a defect of the method — it is the physical content: it quantifies non-orthogonality of the eigenvectors, which is what produces transient growth in a stable system and what makes eigenvalues an unreliable guide for non-normal operators.

Why it matters numerically: eigenvector matrices $S$ can be arbitrarily ill-conditioned, so $A = S\Lambda S^{-1}$ can be a numerically catastrophic route to a matrix function. $Q$ is unitary and therefore perfectly conditioned. This is why library eigensolvers for non-Hermitian matrices compute a Schur form internally (QR algorithm), and why `scipy.linalg.expm` and friends work from Schur or Padé rather than from eigenvectors ([[Floating Point and Numerical Error]]).

**Relation to SVD.** Both use unitaries on both sides, but Schur uses the *same* one ($Q \cdots Q^\dagger$, a similarity transform — the spectrum is preserved, [[Operators and Observables]]) while SVD uses *different* ones ($U \cdots V^\dagger$, an equivalence transform — the spectrum is destroyed, the singular values survive). That single difference explains everything downstream: Schur answers questions about *dynamics* ($A^n$, $e^{At}$, stability — all governed by eigenvalues), SVD answers questions about *magnitude* (gain, rank, conditioning, best approximation — all governed by singular values). For normal matrices the two collapse together and $\sigma_i = |\lambda_i|$; the gap between them is exactly the non-normality that Schur's triangle exposes.

## SVD in engineering — reading a system's response

For a linear system $y = Ax$ (a static input-output map, or a transfer-function matrix $G(j\omega)$ evaluated at one frequency), the SVD says: $\sigma_{\max}$ is the largest gain the system can produce and $v_1$ is the input direction that produces it; $\sigma_{\min}$ and $v_n$ are the least-responsive direction. Concretely:

- **Gain and directionality in MIMO control**: $\sigma_{\max}(G(j\omega))$ vs frequency is the multivariable Bode magnitude; the ratio $\sigma_{\max}/\sigma_{\min}$ at each frequency (the condition number) says how directionally sensitive the plant is — a plant with $\sigma_{\min} \approx 0$ has directions you cannot control at any gain ([[Control Beyond PID]]).
- **Identifying dominant modes from data**: stack measured responses into a matrix and take the SVD; the leading $u_i$ are the dominant spatial patterns, the $\sigma_i$ their weights, and the tail is noise you can truncate (Eckart–Young). This is PCA, POD in fluids, and the first step of dynamic mode decomposition.
- **Which parameters your data can actually constrain**: in fitting, the SVD of the Jacobian names the well- and ill-determined parameter *combinations* — small $\sigma$ directions are the degeneracies that produce absurd error bars ([[Optimization and Curve Fitting]]).
- **Regularized inversion**: truncating or damping small singular values is Tikhonov regularization and the [[Pseudo-Inverse]]; it is the honest way to invert an ill-conditioned response.

## Spectral decomposition in quantum contexts

$A = \sum_a a P_a$ is one theorem doing several jobs, and recognizing which job is which is most of the utility:

- **Observables** — eigenvalues are outcomes, projectors give probabilities ([[Operators and Observables]]).
- **Hamiltonians** — the eigenbasis is the stationary basis, and dynamics become scalar: $e^{-iHt/\hbar} = \sum_n e^{-iE_n t/\hbar}|n\rangle\langle n|$. Diagonalizing *is* solving the dynamics ([[Exact Diagonalization and Sparse Methods]]).
- **Density matrices** — $\rho = \sum_i p_i |i\rangle\langle i|$ gives the eigenensemble; eigenvalues are populations (purity $\mathrm{Tr}\rho^2 = \sum p_i^2$, entropy $-\sum p_i \log p_i$), and positivity is the statement that all eigenvalues are ≥ 0 — the check that a tomographically reconstructed state is physical ([[Quantum State Tomography]]).
- **Liouvillians and channels** — non-Hermitian, so this is Schur/eigen territory rather than spectral: eigenvalues of $\mathcal{L}$ give decay rates, the zero-eigenvalue eigenvector is the steady state ([[Lindblad Master Equation]]).
- **Symmetry sectors** — commuting operators share an eigenbasis, so a symmetry block-diagonalizes $H$ before you ever diagonalize it ([[Simultaneous Diagonalization]]).

## Schmidt decomposition

For a bipartite pure state, reshape amplitudes into a matrix $c_{ij}$ and take its SVD:

$$|\psi\rangle = \sum_{ij} c_{ij}|i\rangle_A|j\rangle_B = \sum_{k=1}^{r} \sigma_k\, |u_k\rangle_A |v_k\rangle_B, \qquad \sum_k \sigma_k^2 = 1.$$

$r$ = Schmidt rank; $\sigma_k$ = Schmidt coefficients. What it buys, in order of usefulness:

- **Entanglement diagnosis is immediate**: $r = 1$ ⇔ product state. Any $r > 1$ is entangled, no measure needed.
- **Reduced states are free**: $\rho_A = \sum_k \sigma_k^2 |u_k\rangle\langle u_k|$ and $\rho_B$ has the *same* eigenvalues — which is why entanglement entropy $S = -\sum_k \sigma_k^2 \log \sigma_k^2$ is symmetric between the halves ([[Entanglement Measures]]).
- **Truncation is controlled**: dropping small $\sigma_k$ is the optimal approximation (Eckart–Young again), which is precisely the compression step of [[Tensor Networks and MPS]] — bond dimension is retained Schmidt rank.
- Caveat: pure bipartite states only. Three parties or mixed states have no analogous canonical form.

> [!question]- A control loop is stable — all eigenvalues in the left half-plane — but the system produces a large transient excursion before settling. Which decomposition explains it, and which one misled you?
> Eigenvalues (spectral/Schur diagonal) govern asymptotic decay and correctly say "stable." They say nothing about the transient when the matrix is non-normal: the eigenvectors are strongly non-orthogonal, so a combination that is small in the eigenbasis can be large in the standard norm, and the state grows before the exponentials win. The right tool is the SVD — $\sigma_{\max}(e^{At})$ versus time bounds the actual excursion — and the Schur form is what shows *why*: a large strictly-upper-triangular part is the quantitative measure of the non-normality producing it.

# Connections

- [[Singular Value Decomposition]] — the always-exists decomposition; geometry and Eckart–Young
- [[Spectral Theorem]] / [[Hermitian Matrices]] — the normal-matrix case in full
- [[Simultaneous Diagonalization]] — when two operators share the basis
- [[Condition Number]] — $\sigma_{\max}/\sigma_{\min}$, and why $S$ vs $Q$ matters numerically
- [[Pseudo-Inverse]] — SVD-based inversion and regularization
- [[Entanglement Measures]] / [[Tensor Networks and MPS]] — Schmidt coefficients as the compression currency
- [[Matrix Exponential]] — computed via Schur/Padé, not via eigenvectors
- [[Polar Decomposition]] — the rotation-times-stretch regrouping

---
Further reading: Trefethen & Bau, *Numerical Linear Algebra*, Lec. 4–5, 24–26 (SVD, Schur, non-normality); Trefethen & Embree, *Spectra and Pseudospectra* (transient growth); Golub & Van Loan, *Matrix Computations*, Ch. 7–8; Skogestad & Postlethwaite, *Multivariable Feedback Control*, Ch. 3 (SVD of plants); Nielsen & Chuang §2.5 (Schmidt)
