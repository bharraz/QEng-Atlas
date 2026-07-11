#linear-algebra #math

**Hermitian matrices with $\langle x|A|x\rangle \ge 0$ for every $x$ — the operators that behave like probabilities and variances.** Density matrices are PSD because expectation values of $|x\rangle\langle x|$-type projectors are probabilities, and probabilities don't go negative.

# Reference

Equivalent characterizations (use whichever is cheapest to check):

$$
\langle x|A|x\rangle \ge 0 \;\;\forall x
\;\Longleftrightarrow\;
\text{all } \lambda_i \ge 0
\;\Longleftrightarrow\;
A = B^\dagger B \text{ for some } B
$$

Positive *definite* = strict versions ($>0$, $\lambda_i > 0$, $B$ full rank; then $A$ is invertible).

- **$A = B^\dagger B$ view:** every PSD matrix is a "square" — covariance matrices ($C = \langle \delta x\, \delta x^T\rangle$), Gram matrices, and $A^\dagger A$ in the SVD are PSD for free.
- **Square roots:** unique PSD $\sqrt{A} = \sum_i \sqrt{\lambda_i}\,|v_i\rangle\langle v_i|$. **Cholesky** is the numerically cheap alternative factorization $A = LL^\dagger$ with $L$ lower-triangular — the standard way to sample correlated Gaussians and to test PSD-ness in code (Cholesky fails ⇔ not positive definite).
- **Density matrices:** $\rho \ge 0$, $\mathrm{Tr}\rho = 1$. Eigenvalues are the probabilities of the eigenstate mixture. A reconstructed $\rho$ from tomography with a small negative eigenvalue is unphysical — noise artifact, fix with MLE.
- **Ordering:** $A \ge B$ means $A - B$ PSD; this is the partial order behind "POVM elements $E_m \ge 0$".

> [!question]- Tomography hands you a Hermitian, trace-1 matrix with eigenvalue $-0.02$. What went wrong and why does it matter?
> Nothing "went wrong" numerically — linear inversion of noisy data doesn't enforce positivity. But $\lambda<0$ means some measurement would have negative probability, so the matrix isn't a state. Enforce $\rho\ge 0$ (MLE or eigenvalue truncation) before computing entropies or fidelities, which choke on negative eigenvalues.

# Connections

- [[Density Matrix]] — the canonical physical PSD object: PSD + unit trace = quantum state
- [[Hermitian Matrices]] — PSD is Hermitian plus nonnegative spectrum
- [[Singular Value Decomposition]] — singular values are $\sqrt{\text{eigenvalues of } A^\dagger A}$, PSD by construction
- [[Projective Measurement and POVMs]] — POVM elements are exactly PSD matrices summing to identity

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 7.
