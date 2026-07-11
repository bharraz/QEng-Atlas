#linear-algebra #math

**Same vector, same operator, new coordinates: components transform with $P^{-1}$, operators get sandwiched $P^{-1}AP$.** The physics never changes under a basis change — only your description does. Choosing the basis where the problem looks trivial *is* most of solving it.

# Reference

Let $P$'s columns be the new basis vectors written in the old basis. Then components and operators transform oppositely:

$$
v' = P^{-1} v, \qquad A' = P^{-1} A P
$$

(so that $A'v' = P^{-1}Av$ — the *action* is basis-independent). Quantities that survive any basis change: eigenvalues, trace, determinant, rank — anything you'd call physical.

**Unitary case:** when both bases are orthonormal, $P = U$ is unitary and

$$
A' = U^\dagger A U
$$

— inner products, Hermiticity, and norms all survive. This is the only kind of basis change QM uses: $z$-basis ↔ $x$-basis, lab frame ↔ rotating frame, bare ↔ dressed states.

**Active vs passive** — the perennial sign trap. *Passive*: state fixed, axes rotate ($v' = U^\dagger v$). *Active*: axes fixed, state rotates ($v' = Uv$). Same math, opposite sense; a rotating-frame transformation is passive, a gate is active. When a phase sign comes out wrong mid-derivation, check this first.

**Diagonalization is just basis change** to the eigenbasis: $P$ = eigenvector matrix makes $A' = D$ diagonal.

> [!question]- Why do operators transform as $P^{-1}AP$ and not $P^{-1}A$ or $PAP^{-1}$?
> $A'$ must eat new-basis components and return new-basis components: translate back to old ($P$), act ($A$), translate forward ($P^{-1}$). Composition order reads right-to-left: $A' = P^{-1}AP$.

# Connections

- [[Unitary Matrices]] — basis changes between orthonormal bases; the only kind that preserves quantum structure
- [[Diagonalization]] — the payoff basis change: to the eigenbasis, where $A$ is diagonal
- [[Spectral Theorem]] — guarantees the orthonormal eigenbasis exists for normal operators
- [[Bloch Sphere]] — qubit basis changes as literal rotations of the sphere

---
Source: Axler, *Linear Algebra Done Right*, Ch. 3 & 10.
