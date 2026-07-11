#linear-algebra #math

**$A = A^\dagger$ — the matrices whose eigenvalues are real, which is exactly why observables are Hermitian operators.** Measurement outcomes are eigenvalues; nature hands you real numbers, so the operator must be Hermitian.

# Reference

Defining property, equivalent in inner-product language to self-adjointness:

$$
A = A^\dagger \quad\Longleftrightarrow\quad \langle x, Ay\rangle = \langle Ax, y\rangle \;\;\forall x,y
$$

**Guaranteed structure** (this is the payoff):
- All eigenvalues $\lambda_i \in \mathbb{R}$
- Eigenvectors of distinct eigenvalues are orthogonal; a full orthonormal eigenbasis always exists (Hermitian ⊂ normal, so the [[Spectral Theorem]] applies)
- Spectral decomposition: $A = \sum_i \lambda_i |v_i\rangle\langle v_i|$

**Quantum reading:** eigenvalues = possible measurement outcomes, $|v_i\rangle\langle v_i|$ = the projector that fires when you get $\lambda_i$, $\langle\psi|A|\psi\rangle$ = expectation value. Diagonalizing the Hamiltonian *is* solving the system.

**Quick checks:** diagonal entries are real; $\mathrm{Tr}\,A$ and $\det A$ are real; real symmetric matrices are the real-field special case. Any matrix splits as $A = \tfrac{1}{2}(A+A^\dagger) + \tfrac{1}{2}(A-A^\dagger)$, Hermitian + anti-Hermitian — the matrix analogue of real + imaginary parts.

> [!question]- Why are Hermitian eigenvalues real? (2-line proof)
> $\langle v|Av\rangle = \lambda\langle v|v\rangle$, but also $\langle v|Av\rangle = \langle Av|v\rangle = \lambda^*\langle v|v\rangle$. So $\lambda = \lambda^*$.

# Connections

- [[Spectral Theorem]] — the diagonalization guarantee Hermitian matrices inherit as normal matrices
- [[Unitary Matrices]] — the sibling class: $e^{iA}$ of a Hermitian $A$ is unitary (generator ↔ evolution)
- [[Eigenvalues and Eigenvectors]] — the general machinery, before Hermiticity adds reality and orthogonality
- [[Rayleigh Quotient and Variational Principle]] — $\langle x|A|x\rangle/\langle x|x\rangle$ is bounded by the extreme eigenvalues, only meaningful because they're real
- [[Positive Semidefinite Matrices]] — Hermitian with the extra constraint $\lambda_i \ge 0$

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 4; Nielsen & Chuang §2.1.
