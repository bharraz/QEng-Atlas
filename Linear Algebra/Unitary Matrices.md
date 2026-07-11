#linear-algebra #math

**$U^\dagger U = \mathbb{1}$ — the complex rotations: they preserve every inner product, which is why quantum time evolution and basis changes are unitary.** Probability is $|\langle\phi|\psi\rangle|^2$; evolution that conserves probability must preserve inner products.

# Reference

$$
U^\dagger U = U U^\dagger = \mathbb{1} \quad\Longleftrightarrow\quad \langle U\phi | U\psi \rangle = \langle \phi | \psi \rangle \;\;\forall \phi,\psi
$$

**Equivalent statements** (any one implies the rest):
- Columns form an orthonormal basis (rows too)
- $\|Ux\| = \|x\|$ for all $x$ (norm preservation is enough, by polarization)
- Eigenvalues all lie on the unit circle, $\lambda = e^{i\theta}$ — unitaries stretch nothing, they only rotate phases

**The exponential connection:** every unitary is $U = e^{iH}$ with $H$ Hermitian. Generator ↔ group element: $H$ is the Hamiltonian, $U(t) = e^{-iHt/\hbar}$ is the evolution ([[Generators and the Exponential Map]]).

**Two jobs in practice:** (1) *evolution* — Schrödinger dynamics, gates; (2) *basis change* — $A' = U^\dagger A U$ re-expresses the same operator in a rotated orthonormal basis without distorting anything ([[Basis Change]]). Unitaries are also normal, so they diagonalize unitarily; real-field special case is orthogonal matrices.

> [!question]- Why must eigenvalues of a unitary have $|\lambda|=1$?
> $\|Uv\| = \|v\|$, but $\|Uv\| = |\lambda|\|v\|$ for an eigenvector. So $|\lambda| = 1$: unitaries can only impart phases, never grow or shrink a state.

# Connections

- [[Matrix Exponential]] — $U = e^{iH}$: how Hermitian generators produce unitary evolution
- [[Basis Change]] — the $P^\dagger A P$ special case where orthonormality survives the transformation
- [[Hermitian Matrices]] — the generator class; anti-Hermitian exponents give unitaries
- [[Single-Qubit Gates]] — SU(2) unitaries are exactly the qubit operations
- [[Normal Matrices]] — unitaries are normal, hence spectrally decomposable

---
Source: Nielsen & Chuang §2.1.4; Horn & Johnson, *Matrix Analysis*, Ch. 2.
