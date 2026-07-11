#linear-algebra #math

**Continuous symmetry groups are built by exponentiating their tangent space at the identity: know the generators (a Lie algebra), and $e^{-i\theta G}$ manufactures every group element near $\mathbb{1}$.** In QM this is why every Hermitian operator generates a unitary flow — the Hamiltonian generates time translation, momentum generates spatial translation, $J_z$ generates rotation.

# Reference

$$
U(\theta) = e^{-i\theta G}, \qquad G = G^\dagger \;\Longleftrightarrow\; U^\dagger U = \mathbb{1}
$$
Hermitian generators ↔ unitary groups; the generator is recovered from the flow by $G = i\,\frac{dU}{d\theta}\big|_{\theta=0}$. Infinitesimally, $U \approx \mathbb{1} - i\,d\theta\, G$: the generator is the group element's first-order behavior, and the exponential map rebuilds finite transformations by compounding infinitesimal ones.

**The algebra determines (almost) everything.** Commutators of generators close: $[G_a, G_b] = i f_{abc} G_c$, and the structure constants $f_{abc}$ fix the group's local structure. Noncommuting generators ⇒ the order of transformations matters, with BCH quantifying by how much.

**Worked case — SU(2)/rotations:** generators $J_i = \sigma_i/2$, algebra $[J_i, J_j] = i\epsilon_{ijk}J_k$, and
$$
e^{-i\theta\, \hat{n}\cdot\vec{\sigma}/2} = \cos\tfrac{\theta}{2}\,\mathbb{1} - i\sin\tfrac{\theta}{2}\,\hat{n}\cdot\vec{\sigma}
$$
— every single-qubit gate. The $\theta/2$ is the spin-1/2 double cover: $\theta = 2\pi$ gives $-\mathbb{1}$, not $\mathbb{1}$.

**Caveats worth remembering:** the exponential map is onto for compact connected groups (SU(N), SO(N)) but same algebra ≠ same group globally (SU(2) vs SO(3)). And via Noether/Stone, "conserved quantity" and "symmetry generator" are the same object — $[H, G]=0$ says both.

> [!question]- Why does $G$ Hermitian force $e^{-i\theta G}$ unitary?
> $\left(e^{-i\theta G}\right)^\dagger = e^{+i\theta G^\dagger} = e^{+i\theta G}$, which is exactly the inverse. Anti-Hermitian exponent ⇔ unitary flow, the Lie-theory version of "imaginary exponent ⇔ unit modulus."

# Connections

- [[Unitary Matrices]] — every unitary connected to $\mathbb{1}$ is $e^{iH}$ for some Hermitian $H$
- [[Pauli Matrices]] — the su(2) generators, with the rotation formula in closed form
- [[Matrix Exponential]] — the map itself, and its non-commuting subtleties
- [[Baker-Campbell-Hausdorff]] — how generator noncommutativity shows up in composed exponentials
- [[Euler-Lagrange Equation]] — Noether's side of the story: symmetries ↔ conserved generators

---
Source: Georgi, *Lie Algebras in Particle Physics*, Ch. 1-3
