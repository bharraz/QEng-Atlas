#linear-algebra #math

**The directions a matrix merely stretches: $Av = \lambda v$ — find them and the matrix decouples into scalars.** Eigen-analysis is the universal solvent: coupled ODEs, stationary states, normal modes, stability — all become "find the special directions, treat each one separately."

# Reference

$\lambda$ is an eigenvalue iff $(A - \lambda\mathbb{1})$ is singular:

$$
\det(A - \lambda\mathbb{1}) = 0
$$

— the **characteristic polynomial**, degree $n$, so $n$ eigenvalues in $\mathbb{C}$ counted with multiplicity. (Fine for theory; numerically you never form it — use QR-based `eig`.)

**Free invariants** (no diagonalization needed):

$$
\mathrm{Tr}\,A = \sum_i \lambda_i, \qquad \det A = \prod_i \lambda_i
$$

Great sanity checks: for a 2×2, trace and det pin down both eigenvalues via $\lambda = \tfrac{1}{2}\left(\mathrm{Tr} \pm \sqrt{\mathrm{Tr}^2 - 4\det}\right)$.

**Two multiplicities:** *algebraic* (root order in the characteristic polynomial) vs *geometric* (dimension of the eigenspace). Always geometric ≤ algebraic. When they differ, the matrix is **defective** — not enough eigenvectors to diagonalize, e.g. $\begin{pmatrix} 0 & 1 \\ 0 & 0\end{pmatrix}$. Never happens for normal matrices, which is why QM rarely reminds you of the distinction.

**Physical dictionary:** Hamiltonian eigenvalues = energies; evolution matrix eigenvalues $\mathrm{Re}\,\lambda < 0$ = stability; eigenvectors of coupled-mode matrices = normal modes.

> [!question]- A 2×2 matrix has $\mathrm{Tr} = 0$ and $\det = -1$. What are its eigenvalues, and what familiar matrices have this signature?
> $\lambda = \pm 1$ (solve $\lambda^2 - 0\cdot\lambda - 1 = 0$). This is every Pauli matrix — traceless, involutory, eigenvalues $\pm 1$: the "measurement outcomes" of any Pauli observable.

# Connections

- [[Diagonalization]] — what eigenvectors buy you when there are enough of them
- [[Spectral Theorem]] — the guarantee of a full orthonormal eigenbasis for normal matrices
- [[Linear ODE Systems]] — eigenvalues as decay/oscillation rates of $\dot{x} = Ax$
- [[Rayleigh Quotient and Variational Principle]] — estimating extreme eigenvalues without solving the polynomial

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 1.
