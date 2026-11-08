#linear-algebra #group-theory #math

**The dot product, the Minkowski interval, the phase-space area $q_1p_2 - p_1q_2$, and a covariance matrix are all rules that take two vectors and return a number — bilinear forms — and the transformations that leave such a rule unchanged are the classical groups: keep lengths and you get rotations $O(n)$, keep the interval and you get the Lorentz group, keep phase-space area and you get the symplectic group.** **In practice:** to know which group your dynamics lives in, and which quantities it can never change, ask which pairing it preserves.

# Reference

**Formally:** a bilinear form is a matrix $B$ read as a pairing $\langle u,v\rangle_B = u^{\mathsf T}Bv$ — and demanding that transformations preserve it, $A^{\mathsf T}BA = B$, is the construction that manufactures every classical group.

**Change of basis acts by congruence,** not conjugation:
$$B \to S^{\mathsf T} B S \qquad \text{(transpose, not inverse)}$$

**Picture:** a bilinear form takes two arrows and returns a number; its group is every linear rearrangement of space that leaves all those numbers unchanged.

| Transform | Form | Invariant |
|---|---|---|
| **Congruence** $S^{\mathsf T}BS$ | acts on bilinear forms | signature (Sylvester's law of inertia) |
| **Conjugation** $SXS^{-1}$ | acts on operators | spectrum ([[Conjugation]]) |

Confusing the two is the standard error: a covariance matrix transforms by congruence, a Hamiltonian by conjugation, and they have different invariants.

**Classification by symmetry:**

- **Symmetric** ($B^{\mathsf T} = B$) — generalizes the dot product. The diagonal $\langle v,v\rangle_B$ is a **quadratic form**: energies, metrics, covariances ([[Positive Semidefinite Matrices]]). Signature (counts of $+,-,0$ eigenvalues) is the congruence invariant — all positive = Euclidean, mixed = Minkowski.
- **Antisymmetric** ($B^{\mathsf T} = -B$) — $\langle v,v\rangle_B = 0$ for every $v$, so no notion of length, only of *oriented area* between pairs. Nondegenerate only in even dimension; canonical form is $J$.
- **Hermitian / sesquilinear** (complex, conjugate-linear in one slot) — the quantum inner product; preservers are the unitaries.

## Preserving a form defines a group

Fix $B$ and collect every $A$ with $A^{\mathsf T}BA = B$. Closure and inverses are immediate, so it is a group — and each classical group is exactly this:

| Preserved form $B$                                                                | Condition                            | Group                | Preserved geometry              |
| --------------------------------------------------------------------------------- | ------------------------------------ | -------------------- | ------------------------------- |
| $\mathbb 1$ (real)                                                                | $A^{\mathsf T}A = \mathbb 1$         | $O(n)$               | lengths and angles              |
| $\mathbb 1$ (complex, Hermitian)                                                  | $A^\dagger A = \mathbb 1$            | $U(n)$               | quantum inner product           |
| $\eta = \mathrm{diag}(-1,1,1,1)$                                                  | $A^{\mathsf T}\eta A = \eta$         | $O(3,1)$             | spacetime interval (Lorentz)    |
| $\eta = \mathrm{diag}(1,-1)$ (Hermitian)                                           | $A^\dagger \eta A = \eta$            | $U(1,1)$             | indefinite Hermitian form; squeezing |
| $J = \begin{pmatrix}0 & \mathbb 1\\ -\mathbb 1 & 0\end{pmatrix}$                  | $A^{\mathsf T}JA = J$                | $Sp(2n,\mathbb R)$   | phase-space area                |

"Generalized orthogonal" is the right reading throughout: orthogonality with respect to a non-Euclidean $B$. Every statement about rotations has an analog in each row with the preserved quantity swapped. Full catalogue with dimensions: [[The Classical Groups Reference]].

**The Lie-algebra version** — differentiate $e^{tX^{\mathsf T}} B\, e^{tX} = B$ at $t=0$:
$$X^{\mathsf T}B + BX = 0$$

The generators are the matrices "antisymmetric with respect to $B$":

| Group | Generator condition | Generators are |
|---|---|---|
| $O(n)$ | $X^{\mathsf T} = -X$ | antisymmetric |
| $U(n)$ | $X^\dagger = -X$ | anti-Hermitian |
| $Sp(2n,\mathbb R)$ | $X^{\mathsf T}J + JX = 0$ | $X = JS$, $S$ symmetric |

The $Sp$ row is why **symmetric matrices — i.e. quadratic Hamiltonians — generate symplectic flow**: Hamilton's equations read $\dot z = J\nabla_z H = JSz$. This algebra is closed under the bracket and stable under $\mathrm{Ad}$ by its group, as any such algebra must be.

**Why the antisymmetric case dominates physics.** Phase space $(q_1,\dots,q_n,p_1,\dots,p_n)$ carries $\omega(u,v) = u^{\mathsf T}Jv$ = sum of signed areas of the $(q_i,p_i)$-plane projections. Two facts make it unavoidable:

- **Hamiltonian flow preserves it automatically** — canonical transformations *are* the symplectic group. Liouville's theorem is a corollary, and a weak one: symplecticity conserves every projected area sum, not only total volume.
- **The canonical commutation relations are this form, operator-valued:** $[z_i, z_j] = i\hbar J_{ij}$. A linear transformation of mode operators is physical iff it preserves the commutators, iff it is symplectic — hence Gaussian evolution = symplectic matrices.

Block conditions, the symplectic spectrum, Bloch–Messiah, Williamson, covariance propagation and the uncertainty condition are all in [[Symplectic Group]].

> [!question]- Squeezing reduces $\Delta X$ below vacuum. Which preserved structure forces the conjugate quadrature to pay?
> The symplectic form. $M = \mathrm{diag}(e^{-r}, e^{+r})$ satisfies $M^{\mathsf T}JM = J$, which forces $\det M = 1$: phase-space area, hence the uncertainty product, is untouchable and only its *shape* can be redistributed. Same constraint bounds a classical degenerate parametric amplifier at gain $G$ / deamplification $1/G$.

# Connections

- [[Conjugation]] — the contrasting transform: spectrum-preserving rather than signature-preserving
- [[Multilinear Maps and Polarization]] — the $k$-slot generalization, and recovering a form from its diagonal
- [[Index Notation and Tensors]] — $B_{ij}$ as a rank-2 tensor; the symmetric/antisymmetric split in indices
- [[Symplectic Group]] — the antisymmetric case in full
- [[The Classical Groups Reference]] — the catalogue this construction generates
- [[Inner Products and Orthogonality]] — the positive-definite symmetric case
- [[Unitary Matrices]] — preservers of the Hermitian form
- [[Lie Groups]] / [[Lie Algebras (Atlas)]] — generators via $X^{\mathsf T}B + BX = 0$
- [[Positive Semidefinite Matrices]] — quadratic forms and covariance matrices
- [[Solving ODEs Numerically]] — symplectic integrators as form-preserving update maps

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 1; Arnold, *Mathematical Methods of Classical Mechanics*, Ch. 8
