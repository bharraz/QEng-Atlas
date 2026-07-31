#group-theory #math

**A Lie algebra is the linearization of a Lie group at the identity: the flat vector space of infinitesimal generators, whose only structural data is how those generators fail to commute.** You trade a curved continuous group for a flat space where the multiplication rule becomes the commutator — and in quantum mechanics the generators are the physical observables.

# Reference

Write a group element just off the identity as

$$g = \mathbb{1} + i\epsilon X + O(\epsilon^2),$$

where $X$ is a generator — an element of the Lie algebra. The algebra is the vector space of all such $X$, closed under the **commutator**, which is its product:

$$[X, Y] = XY - YX.$$

The commutator measures how much the group fails to commute; for an abelian group it vanishes and the algebra is trivial. The algebra is fixed by its **structure constants** $f_{abc}$:

$$[X_a, X_b] = i f_{abc}\, X_c.$$

Everything about the connected group near the identity is encoded in these numbers.

**Exponentiate to return to the group**: a finite transformation is built by accumulating infinitesimal ones,

$$g = e^{i\theta X}.$$

This is the bridge — see [[Generators and the Exponential Map]]. Composing two such exponentials is governed by [[Baker-Campbell-Hausdorff]], where the commutator reappears as the leading correction.

**Examples:**
- $\mathfrak{u}(1)$: one generator, $[X,X]=0$ — abelian, just phases.
- $\mathfrak{su}(2)$: three generators $J_i = \sigma_i/2$ with $[J_i, J_j] = i\,\epsilon_{ijk} J_k$ — the angular-momentum algebra.
- $\mathfrak{su}(N)$: traceless Hermitian $N\times N$ matrices, dimension $N^2 - 1$. For $N=2$ the Paulis; for general $N$ the generalized Gell-Mann matrices, normalized $\mathrm{Tr}(T_a T_b) = \tfrac12 \delta_{ab}$. An $n$-qubit Hamiltonian is an element of $\mathfrak{u}(2^n)$; the Pauli strings are its standard basis.
- $\mathfrak{so}(3) \cong \mathfrak{su}(2)$: same structure constants, different groups upstairs (see [[SU(2) and SO(3)]]).

## Casimirs and the adjoint representation

A **Casimir operator** is a polynomial in the generators commuting with *all* of them. For $\mathfrak{su}(2)$: $J^2 = J_x^2 + J_y^2 + J_z^2$, with $[J^2, J_i] = 0$. By Schur's lemma a Casimir is a constant on each irrep — that constant *labels* the irrep: $J^2 = j(j+1)$ names the spin-$j$ multiplet. The number of independent Casimirs equals the **rank** of the algebra (see below); rank-1 $\mathfrak{su}(2)$ has just $J^2$, rank-2 $\mathfrak{su}(3)$ has two.

The algebra also acts on *itself*: the **adjoint representation** $(\mathrm{ad}_X)Y = [X, Y]$, with matrix elements given by the structure constants, $(\mathrm{ad}_{X_a})_{cb} = i f_{abc}$. Its dimension is the dimension of the algebra ($3$ for $\mathfrak{su}(2)$ — the spin-1 irrep; $8$ for $\mathfrak{su}(3)$ — the gluon octet). Conjugation in the group, $g X g^{-1}$, exponentiates the adjoint action: $e^{A} B e^{-A} = e^{\mathrm{ad}_A} B = B + [A,B] + \tfrac{1}{2!}[A,[A,B]] + \dots$ — the workhorse identity for moving to rotating/interaction frames.

## Cartan subalgebra, weights, ladder operators

The **rank** is the dimension of the largest set of mutually commuting generators (the **Cartan subalgebra**) — the maximal set of simultaneously assignable quantum numbers. The rest of the algebra reorganizes into **ladder (root) operators** that shift those quantum numbers by fixed amounts. For $\mathfrak{su}(2)$: Cartan $= \{J_z\}$, ladders $J_\pm = J_x \pm i J_y$ with $[J_z, J_\pm] = \pm J_\pm$. States within an irrep are labeled by their Cartan eigenvalues (**weights** — the $m$ values), and the ladder operators walk between them:

$$J_\pm |j, m\rangle = \sqrt{j(j+1) - m(m \pm 1)}\, |j, m \pm 1\rangle.$$

Every irrep of every semisimple Lie algebra is built this same way — pick a highest weight, apply lowering operators until the state annihilates. The $\mathfrak{su}(2)$ ladder construction is the template for all of them.

**Why the generators carry the physics**: in quantum mechanics the generator of a continuous symmetry is the conserved observable that produces it. Angular momentum generates rotations, momentum generates translations, and the Hamiltonian generates time evolution ($U = e^{-iHt/\hbar}$). Reading "$\hat{p}$ generates translations" as a Lie-algebra statement is exactly the shift in language this note is for.

> [!question]- Why work with the algebra instead of the group directly?
> The group is a curved manifold; the algebra is a vector space, so linear-algebra tools apply — you can add generators, take commutators, and classify representations with matrices. The commutation relations capture the entire local structure of the group, and exponentiation recovers the group elements, so almost nothing is lost by linearizing.

# Connections

- [[Lie Groups]] — the curved object this is the tangent space of
- [[Generators and the Exponential Map]] — $e^{i\theta X}$, the algebra-to-group bridge
- [[Commutators and Anticommutators]] — the algebra's product and its identities
- [[Baker-Campbell-Hausdorff]] — how generators combine when you multiply exponentials
- [[Reference Atlas/Math/Magnus Expansion]] — time-dependent evolution generated within the algebra
- [[Angular Momentum in QM]] — $\mathfrak{su}(2)$ realized as the physical angular-momentum operators
- [[Reference Atlas/Linear Algebra/Pauli Matrices]] — the $\mathfrak{su}(2)$ basis; Pauli strings as the $\mathfrak{u}(2^n)$ basis

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 2–3; Wiersema et al., "Lie algebras for quantum computing" (arXiv:2308.01306) for the QC framing
