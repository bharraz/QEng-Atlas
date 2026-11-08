#linear-algebra #math

**A vector and an operator exist independently of any coordinates; choosing a basis writes them as a column and a matrix, and choosing a different basis rewrites them without changing what they do.** Components transform with $P^{-1}$, operators are sandwiched as $P^{-1}AP$, and quantities that survive every basis change — eigenvalues, trace, determinant, rank — are the ones that can be physical. Choosing the basis in which a problem looks simple is most of solving it.

# Reference

Let the columns of $P$ be the new basis vectors written in the old basis. Components and operators then transform oppositely:

$$
v' = P^{-1} v, \qquad A' = P^{-1} A P
$$

- $v$, $v'$ — components of one vector in the old and new basis
- $A$, $A'$ — matrices of one operator in the old and new basis
- $P$ — columns are the new basis vectors, in old components

so that $A'v' = P^{-1}Av$: the action of the operator is the same in either description.

**Picture:** a basis change is a dictionary between two languages; the operator in the new basis is "translate into the old language, act, translate back".

**Unitary case.** When both bases are orthonormal, $P = U$ is unitary and

$$
A' = U^\dagger A U
$$

Inner products, Hermiticity, and norms all survive. This is the only kind of basis change quantum mechanics uses ([[Unitary Matrices]]).

**Basis changes that appear in quantum physics:**

| From → to | Matrix | What it reveals |
|---|---|---|
| $z$ basis → $x$ basis of a qubit | Hadamard | $X$ becomes diagonal; phases become populations ([[Bloch Sphere]]) |
| bare states → dressed states | rotation by the mixing angle | the eigenstates of a driven system ([[Dressed States]]) |
| sites → normal modes | eigenvectors of the coupling matrix | independent oscillations ([[Normal Modes of Ion Chains]]) |
| position → momentum | Fourier transform | the plane-wave content of a wavefunction ([[Dirac Notation]]) |
| computational → Bell basis | Hadamard on one qubit, then CNOT; the reverse order to measure in the Bell basis | entangled pairs as single labels |
| lab frame → rotating frame | time-dependent $U(t)$ | a static Hamiltonian, at the cost of an extra term ([[Rotating Frame Transformation]]) |

A time-dependent basis change adds a term $i\hbar\dot U U^\dagger$ to the Hamiltonian; a static one does not.

**Active vs passive.** *Passive*: the state stays fixed and the axes rotate, $v' = U^\dagger v$. *Active*: the axes stay fixed and the state rotates, $v' = Uv$. The mathematics is the same with the opposite sense; a rotating-frame transformation is passive, a gate is active. When a phase sign comes out wrong mid-derivation, check this first ([[Conventions and Factor-of-Two Traps]]).

**Diagonalization is a basis change** to the eigenbasis: with $P$ the matrix of eigenvectors, $A' = D$ is diagonal ([[Diagonalization]]).

> [!question]- Why do operators transform as $P^{-1}AP$ and not $P^{-1}A$ or $PAP^{-1}$?
> $A'$ must take new-basis components in and return new-basis components. Translate back to the old basis ($P$), act ($A$), translate forward ($P^{-1}$). Composition reads right to left: $A' = P^{-1}AP$.

# Connections

- [[Unitary Matrices]] — changes between orthonormal bases; the only kind that preserves quantum structure
- [[Diagonalization]] — the most useful basis change: to the eigenbasis, where $A$ is diagonal
- [[Spectral Theorem]] — guarantees the orthonormal eigenbasis exists for normal operators
- [[Bloch Sphere]] — qubit basis changes as rotations of the sphere
- [[Reading Matrices and Hamiltonians]] — why "off-diagonal" is a statement about the basis
- [[Rotating Frame Transformation]] — the time-dependent case

---
Source: Axler, *Linear Algebra Done Right*, Ch. 3 & 10
