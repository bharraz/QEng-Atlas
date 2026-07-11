#group-theory #quantum #AMO #math

**$SO(3)$ rotates ordinary 3D vectors; $SU(2)$ acts on two-component spinors; they share one Lie algebra but differ globally — $SU(2)$ is a double cover, so two of its elements map to each rotation.** This is the concrete group behind spin, the Bloch sphere, and every rotation you apply to a qubit, and it is where the $2\pi \to -1$ sign of spin-1/2 comes from.

# Reference

Both groups are three-dimensional Lie groups with the *same* algebra $\mathfrak{su}(2) \cong \mathfrak{so}(3)$:

$$[J_i, J_j] = i\,\epsilon_{ijk}\,J_k.$$

They differ in their global structure — the map $SU(2) \to SO(3)$ is two-to-one:

$$\pm U \in SU(2) \;\longmapsto\; \text{the same rotation } R \in SO(3).$$

$SU(2)$ is the **double cover** of $SO(3)$. A rotation by $2\pi$ is the identity in $SO(3)$, but the corresponding $SU(2)$ element is $-\mathbb{1}$; you need $4\pi$ to return $SU(2)$ to the identity.

**The spinor sign**: a spin-1/2 state transforms under $SU(2)$, so a full $2\pi$ rotation multiplies it by $-1$,

$$R_{\hat{n}}(\theta) = e^{-i\theta\,\hat{n}\cdot\vec{\sigma}/2}, \qquad R_{\hat{n}}(2\pi) = -\mathbb{1}.$$

This is not a bookkeeping artifact — it is the observable statement that spin-1/2 lives in the covering group, not in the rotation group. A spin-1 (vector) state lives in $SO(3)$ and returns after $2\pi$.

**Representations split by which group sees them:**
- **Integer $j$** ($0, 1, 2, \dots$): genuine representations of $SO(3)$ — orbital angular momentum, vectors, tensors.
- **Half-integer $j$** ($\tfrac12, \tfrac32, \dots$): representations of $SU(2)$ only — spinors. They pick up the minus sign under $2\pi$.

Each spin-$j$ irrep has dimension $2j+1$. This is the concrete face of [[Group Representations]] and the reason [[Angular Momentum in QM]] and the [[Bloch Sphere]] look the way they do: a single-qubit gate $e^{-i\theta\,\hat n\cdot\vec\sigma/2}$ is literally an element of $SU(2)$.

**The explicit covering map** — the rotation $R$ corresponding to $U \in SU(2)$:

$$R_{ij}(U) = \tfrac{1}{2}\,\mathrm{Tr}\!\left(\sigma_i\, U\, \sigma_j\, U^\dagger\right),$$

i.e. conjugation of the Paulis by $U$ rotates the Bloch vector: $U(\hat n \cdot \vec\sigma)U^\dagger = (R\hat n)\cdot\vec\sigma$. Manifestly $U$ and $-U$ give the same $R$ — the double cover in one line. This is also the practical dictionary between a unitary and its Bloch-sphere rotation (axis and angle: $U = \cos\tfrac\theta2\,\mathbb{1} - i \sin\tfrac\theta2\, \hat n\cdot\vec\sigma$, so $\mathrm{Tr}\,U = 2\cos\tfrac\theta2$ fixes the angle).

**Characters and tensor products.** The spin-$j$ character for rotation angle $\theta$ is

$$\chi_j(\theta) = \sum_{m=-j}^{j} e^{im\theta} = \frac{\sin\!\big((2j+1)\,\theta/2\big)}{\sin(\theta/2)},$$

and multiplying characters decomposes composite systems:

$$j_1 \otimes j_2 = |j_1 - j_2| \oplus \cdots \oplus (j_1 + j_2),$$

each irrep appearing exactly once ($SU(2)$ is multiplicity-free — one reason angular momentum bookkeeping is as easy as it is). Basis change between $|j_1 m_1; j_2 m_2\rangle$ and $|J M\rangle$ is the [[Clebsch-Gordan Coefficients]] table. Standard checks: $\tfrac12 \otimes \tfrac12 = 0 \oplus 1$ (singlet + triplet), $\tfrac12 \otimes 1 = \tfrac12 \oplus \tfrac32$ (spin-orbit in a $p$ level).

**Casimir**: $J^2$ commutes with all three generators and equals $j(j+1)$ on the spin-$j$ irrep — the irrep label is the Casimir eigenvalue (see [[Lie Algebras]]).

> [!question]- Where do you physically "see" that spin-1/2 belongs to $SU(2)$ rather than $SO(3)$?
> In interference: rotate one arm of a spin-1/2 (e.g. neutron) interferometer by $2\pi$ and the pattern shifts as if the amplitude were multiplied by $-1$; only a $4\pi$ rotation restores it. A vector quantity would return after $2\pi$. The measurable $4\pi$ periodicity is the double cover made visible.

# Connections

- [[Group Representations]] — spin-$j$ multiplets are the irreps; $2j+1$ is their dimension
- [[Lie Algebras]] — the shared $\mathfrak{su}(2)$ algebra both groups exponentiate from
- [[Pauli Matrices]] — $\sigma_i/2$ are the generators; $e^{-i\theta\hat n\cdot\vec\sigma/2}$ is the group element
- [[Bloch Sphere]] — $SU(2)$ acting on a qubit, drawn as rotations of a sphere
- [[Angular Momentum in QM]] — the ladder structure and the integer/half-integer split
- [[Clebsch-Gordan Coefficients]] — the tensor-product change of basis

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, Ch. 3; Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 4
