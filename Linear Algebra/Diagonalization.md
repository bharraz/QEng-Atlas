#linear-algebra #math

**A matrix that couples its components — coupled oscillators, a driven atom, a chain of spins — becomes a set of independent scalar problems once it is written in a basis of its own eigenvectors, where it is diagonal.** In that basis powers, exponentials, and time evolution act on each component separately. Diagonalization is that change of basis, available whenever the matrix has a full set of eigenvectors.

# Reference

$A$ is diagonalizable if and only if it has $n$ linearly independent eigenvectors. Stack them as the columns of $P$:

$$
A = P D P^{-1}, \qquad D = \mathrm{diag}(\lambda_1, \ldots, \lambda_n)
$$

- $P$ — columns are the eigenvectors of $A$
- $D$ — diagonal matrix of the eigenvalues, in the same order

**Picture:** a set of coupled springs untangled into independent normal modes, each ringing at its own frequency.

**Why diagonalize.** Sandwiched powers telescope:

$$
A^k = P D^k P^{-1}, \qquad f(A) = P\, \mathrm{diag}\big(f(\lambda_i)\big)\, P^{-1}
$$

so $e^{At}$, $\sqrt{A}$, resolvents, and long-time dynamics cost one diagonalization each ([[Matrix Exponential]]). For a Hamiltonian, $e^{-iHt/\hbar}$ in the eigenbasis multiplies each component by its own phase $e^{-iE_nt/\hbar}$; all the motion seen in another basis comes from these phases turning at different rates ([[Reading Matrices and Hamiltonians]]).

**Where it appears in physics:** normal modes of coupled oscillators and ion chains ([[Normal Modes of Ion Chains]]); dressed states of a driven atom ([[Dressed States]]); band structures, by diagonalizing in crystal momentum ([[Bloch's Theorem and Band Structure]]); and numerical many-body spectra ([[Exact Diagonalization and Sparse Methods]]).

**When it is guaranteed:** distinct eigenvalues (sufficient), or a normal matrix — then $P$ is unitary and you have the [[Spectral Theorem]], the clean case and the usual one in quantum mechanics.

**When it fails: defective matrices.** A repeated eigenvalue with too few eigenvectors, e.g. $\begin{pmatrix} \lambda & 1 \\ 0 & \lambda \end{pmatrix}$, has geometric multiplicity below algebraic. The closest form is the Jordan form, and dynamics pick up secular $t e^{\lambda t}$ terms: the critically damped oscillator, and exceptional points of non-Hermitian systems. Defectiveness occurs only for non-normal matrices, and it is fragile. Numerically, a nearly defective matrix has an ill-conditioned $P$ and untrustworthy eigenvectors ([[Condition Number]]).

**Non-orthogonal eigenvectors.** Diagonalizable does *not* mean orthogonal eigenvectors. A non-normal $A$ can diagonalize in a skewed basis, and then $\|e^{At}\|$ can grow transiently even when every $\mathrm{Re}\,\lambda < 0$.

> [!question]- All eigenvalues of $A$ have negative real part, yet $\|e^{At}x_0\|$ grows 100× before decaying. How?
> $A$ is non-normal: its eigenvectors are nearly parallel, so representing $x_0$ needs large opposing coefficients that cancel at $t = 0$ and stop cancelling as they decay at different rates. Eigenvalues govern $t \to \infty$; transients are governed by non-normality.

# Connections

- [[Eigenvalues and Eigenvectors]] — the ingredients; diagonalizable means having enough of them
- [[Spectral Theorem]] — the orthonormal upgrade for normal matrices
- [[Basis Change]] — diagonalization is a basis change to the eigenbasis
- [[Matrix Exponential]] — the main use: $e^{At}$ via $Pe^{Dt}P^{-1}$
- [[Linear ODE Systems]] — coupled modes decouple exactly when you diagonalize
- [[Reading Matrices and Hamiltonians]] — what the off-diagonal entries meant before diagonalizing

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 1 & 3
