#linear-algebra #math

**The operator alphabet of a two-level system: three traceless Hermitian-and-unitary matrices that, with $\mathbb{1}$, span all 2×2 operators.** Everything qubit — Hamiltonians, gates, measurements, noise — is written in Paulis.

# Reference

$$
\sigma_x = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad
\sigma_y = \begin{pmatrix} 0 & -i \\ i & 0 \end{pmatrix}, \quad
\sigma_z = \begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}, \quad
\mathbb{1} = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}
$$

**The algebra** — one identity to rule them all:

$$
\sigma_i \sigma_j = \delta_{ij}\mathbb{1} + i\,\varepsilon_{ijk}\,\sigma_k
$$

Unpack: $\sigma_i^2 = \mathbb{1}$; commutator $[\sigma_i,\sigma_j] = 2i\varepsilon_{ijk}\sigma_k$ (angular momentum algebra — spin-½ is $S_i = \tfrac{\hbar}{2}\sigma_i$); anticommutator $\{\sigma_i,\sigma_j\} = 2\delta_{ij}\mathbb{1}$ (distinct Paulis *anticommute*). Each is Hermitian AND unitary, eigenvalues $\pm 1$, traceless.

**Basis for 2×2 Hermitian matrices:** any $H = a_0\mathbb{1} + \vec{a}\cdot\vec\sigma$ with real coefficients $a_\mu = \tfrac{1}{2}\mathrm{Tr}(H\sigma_\mu)$ (orthogonality $\mathrm{Tr}(\sigma_i\sigma_j) = 2\delta_{ij}$). Eigenvalues: $a_0 \pm |\vec a|$. This is why every two-level Hamiltonian is "a field $\vec{a}$ on the Bloch sphere."

**Rotation formula** — since $(\hat n\cdot\vec\sigma)^2 = \mathbb{1}$, the exponential series splits into cos/sin:

$$
e^{-i\theta\, \hat n\cdot\vec\sigma/2} = \cos\frac{\theta}{2}\,\mathbb{1} - i\sin\frac{\theta}{2}\; \hat n\cdot\vec\sigma
$$

Rotates the Bloch vector by $\theta$ about $\hat n$. Note the half-angle: $\theta = 2\pi$ gives $-\mathbb{1}$, the spin-½ sign, invisible alone but measurable in interference.

> [!question]- Why does the Bloch vector rotate by $\theta$ when the state picks up only half-angle factors $\cos\theta/2$, $\sin\theta/2$?
> The Bloch vector is bilinear in the state, $r_i = \langle\psi|\sigma_i|\psi\rangle$ — the two half-angles combine to full angle (SU(2) double-covers SO(3)). Same reason $2\pi$ rotation flips the state's sign but returns the Bloch vector home.

# Connections

- [[Spin-1-2]] — the physics the algebra was built for: $\vec S = \hbar\vec\sigma/2$
- [[Bloch Sphere]] — $\vec a\cdot\vec\sigma$ Hamiltonians precess the Bloch vector about $\vec a$
- [[Single-Qubit Gates]] — every gate is $e^{-i\theta\hat n\cdot\vec\sigma/2}$ up to phase
- [[Pauli Group]] — the $n$-qubit extension: tensor products of Paulis as the error basis
- [[Generators and the Exponential Map]] — $\sigma/2$ as the generators of SU(2)

---
Source: Nielsen & Chuang §2.1.3 & §4.2.
