#group-theory #math

**A representation is a concrete realization of an abstract group as matrices acting on a vector space, chosen so that matrix multiplication reproduces the group's composition rule.** The group is a pattern of how moves combine; a representation is a specific way that pattern acts on states.

# Reference

A representation is a map $\rho: G \to GL(V)$ assigning to each group element a linear operator on a vector space $V$, respecting composition:

$$\rho(g \cdot h) = \rho(g)\,\rho(h).$$

Because states in quantum mechanics live in a vector space, a symmetry group acts on them through a representation — this is the channel by which an abstract group touches physics.

**Irreducible representation (irrep)**: a representation whose space $V$ has no proper subspace left invariant by every $\rho(g)$. You cannot block-diagonalize it into smaller pieces by any choice of basis. Irreps are the indivisible building blocks; any representation decomposes into a direct sum of them.

**Why irreps are the object of interest:**
- The distinct irreps of a symmetry group label the distinct "types" of state: spin-$j$ multiplets, particle species, orbital symmetries. A degenerate energy multiplet *is* an irrep (see [[Symmetry in Quantum Mechanics]]).
- The **dimension** of an irrep is the size of the multiplet it labels — a spin-$j$ irrep of $SU(2)$ has dimension $2j+1$.
- **Character** $\chi(g) = \mathrm{Tr}\,\rho(g)$ is a basis-independent fingerprint of a representation; characters are how you identify which irreps a reducible representation contains.

**Schur's lemma** (the workhorse): any operator commuting with every element of an irrep is a multiple of the identity. This is why a Casimir operator like $J^2$ takes a single fixed value across an entire multiplet — it commutes with all rotations, so on each irrep it must be a scalar.

## Character machinery — how you actually decompose

For finite (and compact) groups the characters of inequivalent irreps are orthonormal under averaging over the group:

$$\frac{1}{|G|} \sum_{g} \chi^{(\mu)}(g)^* \chi^{(\nu)}(g) = \delta_{\mu\nu}.$$

Characters are constant on **conjugacy classes** (conjugate elements are "the same move seen from a rotated frame"), so the full data of a finite group's representation theory is its **character table**: rows = irreps, columns = classes. Two counting rules pin it down: the number of irreps equals the number of conjugacy classes, and $\sum_\mu d_\mu^2 = |G|$.

Given any representation with character $\chi$, the number of times irrep $\mu$ appears is

$$n_\mu = \frac{1}{|G|}\sum_g \chi^{(\mu)}(g)^*\, \chi(g),$$

and the **projection operator** onto the $\mu$-part of the space is $P^{(\mu)} = \frac{d_\mu}{|G|} \sum_g \chi^{(\mu)}(g)^*\, \rho(g)$ — this is how you construct symmetry-adapted states (molecular orbitals, vibrational modes) mechanically. For $SU(2)$ the same orthogonality runs over the group with the Haar measure; the spin-$j$ character is $\chi_j(\theta) = \sin\!\big((2j{+}1)\theta/2\big)/\sin(\theta/2)$ for rotation angle $\theta$.

**Unitarity**: every representation of a finite or compact group is equivalent to a unitary one (average any inner product over the group). This is why symmetries act unitarily on Hilbert space and why complete reducibility — every rep = direct sum of irreps — holds.

## Tensor products of representations

Two systems transforming under the same group: the composite transforms under the **tensor product representation**, $\rho_1 \otimes \rho_2$ acting on $V_1 \otimes V_2$, with character $\chi_{1\otimes 2}(g) = \chi_1(g)\,\chi_2(g)$. The product is generally *reducible*, and decomposing it back into irreps is a central operation:

$$j_1 \otimes j_2 = |j_1 - j_2| \oplus (|j_1 - j_2| + 1) \oplus \dots \oplus (j_1 + j_2)$$

for $SU(2)$ — angular momentum addition *is* tensor-product decomposition, and [[Clebsch-Gordan Coefficients]] are the change of basis from $|m_1 m_2\rangle$ to $|J M\rangle$. Sanity check by dimensions: $2 \otimes 2 = 3 \oplus 1$ (two qubits = triplet + singlet). The same decomposition applied to *operators* (which transform in the adjoint/tensor reps) is what powers the [[Wigner-Eckart Theorem]].

> [!question]- What is the difference between a group and a representation of it, in one sentence?
> The group is the abstract composition structure (how moves combine); a representation is one specific set of matrices that obeys that structure — the same group can act on spin-1/2 states, spin-1 states, or 3-vectors, and each is a different representation of the identical underlying group.

# Connections

- [[(Atlas) Group Theory]] — the abstract structure being represented
- [[Symmetry in Quantum Mechanics]] — degenerate multiplets are irreps; good quantum numbers are irrep labels
- [[SU(2) and SO(3)]] — the concrete irreps you meet first: spin-$j$ multiplets
- [[Point Groups and Character Tables]] — the character machinery applied to finite symmetry groups
- [[Clebsch-Gordan Coefficients]] — how tensor products of irreps decompose back into irreps
- [[Wigner-Eckart Theorem]] — Schur's lemma turned into a computational tool for matrix elements
- [[Tensor Product]] — the linear-algebra substrate of product representations
- [[Angular Momentum in QM]] — the $2j+1$ multiplet is the canonical example

---
Source: Zee, *Group Theory in a Nutshell for Physicists*, Ch. II; Georgi, *Lie Algebras in Particle Physics*, Ch. 1
