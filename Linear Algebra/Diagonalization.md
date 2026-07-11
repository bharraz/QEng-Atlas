#linear-algebra #math

**If a matrix has a full set of eigenvectors, change to that basis and it becomes diagonal — after which powers, exponentials, and dynamics are trivial.** Diagonalization turns matrix problems into $n$ independent scalar problems.

# Reference

$A$ is diagonalizable iff it has $n$ linearly independent eigenvectors. Stack them as columns of $P$:

$$
A = P D P^{-1}, \qquad D = \mathrm{diag}(\lambda_1, \ldots, \lambda_n)
$$

**Why bother** — sandwiched powers telescope:

$$
A^k = P D^k P^{-1}, \qquad f(A) = P\, \mathrm{diag}(f(\lambda_i))\, P^{-1}
$$

so $e^{At}$, $\sqrt{A}$, resolvents, and long-time dynamics cost one diagonalization each.

**When it's guaranteed:** distinct eigenvalues (sufficient), or normal matrix (then $P$ is unitary and you get the [[Spectral Theorem]] — the clean case, and the usual one in QM).

**When it fails:** **defective matrices** — repeated eigenvalue with too few eigenvectors, e.g. $\begin{pmatrix} \lambda & 1 \\ 0 & \lambda \end{pmatrix}$. Geometric < algebraic multiplicity; closest you get is Jordan form, and dynamics pick up secular $t e^{\lambda t}$ terms (critically damped oscillator, exceptional points in non-Hermitian systems). Defectiveness only occurs for non-normal matrices, and it's fragile — numerically, near-defective means an ill-conditioned $P$ and untrustworthy eigenvectors.

**Gotcha:** diagonalizable does *not* mean orthogonal eigenvectors. Non-normal $A$ can diagonalize with a skewed basis; then $\|e^{At}\|$ can transiently grow even when every $\mathrm{Re}\,\lambda < 0$.

> [!question]- All eigenvalues of $A$ have negative real part, yet $\|e^{At}x_0\|$ grows 100× before decaying. How?
> $A$ is non-normal: eigenvectors are nearly parallel, so representing $x_0$ requires huge opposing coefficients that cancel at $t=0$ and de-cancel at different rates. Eigenvalues govern $t\to\infty$; transients are governed by non-normality.

# Connections

- [[Eigenvalues and Eigenvectors]] — the ingredients; diagonalizability = enough of them
- [[Spectral Theorem]] — the orthonormal upgrade for normal matrices
- [[Basis Change]] — diagonalization is a basis change to the eigenbasis
- [[Matrix Exponential]] — the main consumer: $e^{At}$ via $Pe^{Dt}P^{-1}$
- [[Linear ODE Systems]] — coupled modes decouple exactly when you diagonalize

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 1 & 3.
