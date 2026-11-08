#linear-algebra #math

**Feed a matrix most vectors and it changes their direction; a few special inputs come out pointing the same way, only rescaled: $Av = \lambda v$.** Those directions are the eigenvectors and the scale factors are the eigenvalues. Once you have them, a coupled problem splits into independent scalar ones — coupled differential equations, stationary states, normal modes, and stability all reduce to finding these directions and treating each separately.

# Reference

$\lambda$ is an eigenvalue exactly when $A - \lambda\mathbb{1}$ is singular:

$$
\det(A - \lambda\mathbb{1}) = 0
$$

- $\lambda$ — eigenvalue: the factor by which its eigenvector is scaled
- $\det(A - \lambda\mathbb{1})$ — the **characteristic polynomial**, of degree $n$

So there are $n$ eigenvalues in $\mathbb{C}$, counted with multiplicity. The polynomial is for theory; numerically, eigenvalues come from QR-based `eig` routines, never from the polynomial's roots ([[Matrix Decompositions in Practice]]).

**Picture:** spin a globe and every point on its surface moves except the two poles; the axis through them is the eigenvector of the rotation.

**Invariants available without diagonalizing:**

$$
\mathrm{Tr}\,A = \sum_i \lambda_i, \qquad \det A = \prod_i \lambda_i, \qquad \lambda_\pm = \tfrac12\left(\mathrm{Tr}\,A \pm \sqrt{(\mathrm{Tr}\,A)^2 - 4\det A}\right) \ \ (2\times2)
$$

These are quick checks on any hand calculation. For a $2\times 2$ matrix, trace and determinant fix both eigenvalues.

**Two multiplicities.** *Algebraic*: the order of the root in the characteristic polynomial. *Geometric*: the dimension of the eigenspace. Always geometric ≤ algebraic; when they differ the matrix is **defective**, without enough eigenvectors to diagonalize, e.g. $\begin{pmatrix} 0 & 1 \\ 0 & 0\end{pmatrix}$. This never happens for normal matrices, which is why quantum mechanics rarely mentions the distinction ([[Normal Matrices]]).

**What eigenvalues mean in physics:**

| Matrix | Eigenvalues | Eigenvectors |
|---|---|---|
| Hamiltonian $H$ | energies | stationary states |
| observable $O$ | possible measurement outcomes | states with a definite outcome |
| evolution operator $e^{-iHt/\hbar}$ | phases $e^{-iE_nt/\hbar}$ | the same stationary states |
| density matrix $\rho$ | probabilities of an orthogonal mixture | the states being mixed |
| coupling matrix of oscillators | squared normal-mode frequencies | normal modes |
| generator of $\dot x = Ax$ | growth or decay rates ($\mathrm{Re}\,\lambda$; all negative means stable) and oscillation frequencies ($\mathrm{Im}\,\lambda$) | modes of the linear system |

Only eigenvalue *differences* of a Hamiltonian are observed as frequencies: every oscillation in a measured signal is at some $(E_m - E_n)/\hbar$ ([[Reading Matrices and Hamiltonians]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| spectroscopy line positions | differences of Hamiltonian eigenvalues |
| frequencies in a time trace (Rabi, Ramsey, beating) | eigenvalue differences of the Hamiltonian in the frame used |
| decay rates of a linear system's response | real parts of the generator's eigenvalues |
| outcomes of a projective measurement | eigenvalues of the measured observable |

> [!question]- A $2\times2$ matrix has $\mathrm{Tr} = 0$ and $\det = -1$. What are its eigenvalues, and which familiar matrices have this signature?
> $\lambda = \pm 1$, from $\lambda^2 - 0\cdot\lambda - 1 = 0$. Every Pauli matrix has it: traceless, squaring to the identity, with eigenvalues $\pm 1$ — the two measurement outcomes of any Pauli observable.

# Connections

- [[Diagonalization]] — what eigenvectors give you when there are enough of them
- [[Spectral Theorem]] — the guarantee of a full orthonormal eigenbasis for normal matrices
- [[Linear ODE Systems]] — eigenvalues as decay and oscillation rates of $\dot{x} = Ax$
- [[Rayleigh Quotient and Variational Principle]] — estimating extreme eigenvalues without the polynomial
- [[Reading Matrices and Hamiltonians]] — eigenvectors as the inputs a matrix only rescales
- [[Degeneracy and Level Crossings]] — repeated eigenvalues and what they imply

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 1
