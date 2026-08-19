#group-theory #reference #math

**A group is the set of transformations leaving some structure unchanged, together with the rule for composing them — the minimal axioms for "reversible moves that stack."**

Entry point and map for this folder: the axioms and the abstract/concrete distinction below, then a routing table for the other seventeen pages.

# Reference

A group is a set $G$ with a binary operation $\cdot$ satisfying four conditions:

- **Closure** — $a \cdot b \in G$. Composing two moves gives a move.
- **Associativity** — $(a \cdot b) \cdot c = a \cdot (b \cdot c)$.
- **Identity** — there is $e$ with $e \cdot a = a \cdot e = a$. The "do nothing" move.
- **Inverse** — every $a$ has $a^{-1}$ with $a \cdot a^{-1} = e$. Every move undoes.

**Abelian** if $a\cdot b = b\cdot a$ for all elements; otherwise non-abelian, which is the interesting case — rotations about different axes, matrix products, most symmetry groups.

## The group vs. its representations

The group is the abstract structure: elements and a composition rule. Nothing in the axioms mentions matrices — the integers under addition are a group with no matrix anywhere.

- Matrices enter when the moves must **act on something**. A representation assigns each element a matrix so that matrix multiplication reproduces composition.
- **The tell that a group is not its matrices:** the *same* group has *many* representations — the rotation group acts on spin-$\tfrac12$ as $2\times2$ matrices and on 3-vectors as $3\times3$. So it cannot *be* either one; it is the common structure behind both.
- Some groups are *defined* as matrices ($SU(2)$ = the $2\times2$ unitaries with $\det = 1$), but that is still one representation among many.
- Guarantee worth knowing: every finite group and every compact Lie group has a **faithful** matrix representation, so matrices are always available even when they are not the definition.

## Maps between groups

| Map | Definition | What it does |
|---|---|---|
| **Homomorphism** | $\varphi(a\cdot b) = \varphi(a)\cdot\varphi(b)$ | carries structure across; may lose information |
| **Isomorphism** | bijective homomorphism | $G \cong H$ — the same group in different clothing |
| **Kernel** | $\ker\varphi = \{g : \varphi(g) = e_H\}$ | exactly what the map forgets; trivial kernel ⇔ injective |

A **representation is precisely a homomorphism** $\rho: G \to GL(V)$ into invertible matrices ([[Group Representations]]).

## Internal structure

- **Conjugacy class** of $a$: $\{gag^{-1}\}$ — the same move seen from every reframing. In a rotation group, all rotations by angle $\theta$ (any axis) form one class. Classes partition the group and characters are constant on them ([[Conjugation]]).
- **Normal subgroup** $N \trianglelefteq G$: closed under conjugation, $gNg^{-1} = N$. Kernels of homomorphisms are exactly the normal subgroups.
- **Quotient group** $G/N$: collapse $N$ to the identity; elements are cosets $gN$. **First isomorphism theorem:** $G/\ker\varphi \cong \mathrm{im}\,\varphi$.
- **Center** $Z(G)$: elements commuting with everything. Quotients by subgroups of the center give the covering relations, e.g. $SO(3) \cong SU(2)/\{\pm\mathbb 1\}$ ([[Lie Groups]]).
- **Lagrange's theorem** (finite groups): $|H|$ divides $|G|$ for any subgroup — the cosets tile the group. Element orders divide $|G|$ as a corollary.
- **Direct product** $G\times H$: componentwise composition, two independent symmetries side by side. Contrast the **semidirect** product, where one factor acts on the other.

Normal subgroup : quotient group :: **ideal : quotient algebra**. The algebra-side version, and why only ideals may be discarded, is [[Subalgebras, Ideals, and Quotients]].

## Worked example — symmetries of an equilateral triangle

Label the vertices $1,2,3$. The rigid motions mapping the triangle to itself: identity $e$; rotations $r, r^2$ by $120°, 240°$; reflections $s_1, s_2, s_3$ through each vertex. Six elements — the **dihedral group $D_3$**, non-abelian since rotation-then-reflection differs from the reverse.

| Concept | In $D_3$ |
|---|---|
| **Isomorphism** | each symmetry permutes the vertices, and all $3! = 6$ permutations appear, so $D_3 \cong S_3$ — rigid motions of a shape and reshufflings of a list are one group |
| **Representation** | place it in the plane: each symmetry is a $2\times2$ matrix on position vectors, all six distinct, so a faithful 2D representation |
| **Homomorphism** | send rotations to $+1$, reflections to $-1$. Valid ($(-1)(-1) = +1$: two reflections compose to a rotation) but not injective |
| **Kernel** | of that map: the rotations $\{e, r, r^2\} = A_3$ — the even permutations. This is the sign-of-a-permutation map, and the structure behind the determinant's sign |
| **Normal subgroup** | $\{e, r, r^2\} \trianglelefteq D_3$ (conjugating a rotation gives a rotation) |
| **Quotient** | $D_3/\{e,r,r^2\} \cong \mathbb Z_2$ — exactly the orientation sign |
| **Classes** | $\{e\}$, $\{r, r^2\}$, $\{s_1,s_2,s_3\}$ — three classes, hence three irreps, of dimensions $1,1,2$ (check: $1+1+4 = 6 = |G|$) |

Where it appears: $D_3$ as the point group $C_{3v}$ is the symmetry of a triangular molecule such as $\mathrm{NH_3}$ along its axis; $S_3$ governs three identical particles.

> [!question]- If two groups are isomorphic, what is the same and what can differ?
> Everything structural: multiplication table, element orders, which subgroups exist, whether it is abelian. Only the *labels* differ — what the elements "are" (rigid motions, permutations, matrices) and how the operation is written.

# Map of this folder

**Foundations** — the machinery everything else assumes.

| Page | Answers |
|---|---|
| [[Lie Groups]] | continuous groups as manifolds; compactness; covering groups and why spin-$\tfrac12$ exists |
| [[Lie Algebras (Atlas)]] | generators, structure constants, $\mathrm{ad}$, Casimirs, rank — the entry point for the algebra side |
| [[Conjugation]] | $gxg^{-1}$ as frame change; invariants vs. viewpoint; $\mathrm{Ad}$, $\mathrm{ad}$, the Hadamard series |

**Structure and classification** — what an algebra is made of, and what may be discarded.

| Page | Answers |
|---|---|
| [[Subalgebras, Ideals, and Quotients]] | subalgebra vs. ideal; when a truncation is legitimate; nilpotent vs. solvable; Levi |
| [[Graded and Filtered Lie Algebras]] | does the bracket *add* your index? Whether a degree cutoff is an ideal |
| [[Cartan Subalgebras, Roots, and Weights]] | roots, weights, highest-weight irreps, the $A_n$–$D_n$ classification, real forms |
| [[Universal Enveloping Algebra and PBW Basis]] | where $J^2$ and the Casimirs live; PBW ordering; Lie-closure vs. product-closure |
| [[Weyl Algebra and Degree Filtration]] | polynomials in $a, a^\dagger$; why degree truncation fails; $F_2$ closes and $F_3$ does not |
| [[Free Algebras, Words, and Gradings]] | alphabets, words, length grading; why BCH is a universal formula and closure is a property of the substitution |

**Specific groups** — look-up pages.

| Page | Answers |
|---|---|
| [[The Classical Groups Reference]] | the catalogue: defining condition, algebra, dimension, physics home |
| [[Bilinear Forms and Preserved Structures]] | how each classical group is manufactured from a preserved form |
| [[Symplectic Group]] | $Sp(2n,\mathbb R)$; Williamson, Bloch–Messiah, Gaussian states |
| [[SU(2) and SO(3)]] | the double cover; spinors vs. vectors |
| [[Point Groups and Character Tables]] | finite symmetry groups of molecules and defect sites |

**Putting it to work.**

| Page | Answers |
|---|---|
| [[Group Representations]] | irreps, characters, Schur, tensor products and Clebsch–Gordan |
| [[Noether's Theorem]] | symmetry ⇒ conservation; degeneracy as irrep dimension; hidden symmetry |
| [[Dynamical Lie Algebras and Closure]] | what can this Hamiltonian reach, and is it exactly solvable? |
| [[Solving Dynamics on Closed Lie Algebras]] | Wei–Norman, disentangling identities, moment propagation |

**Suggested route if starting cold:** this page → [[Lie Groups]] → [[Lie Algebras (Atlas)]] → [[Conjugation]] → [[Subalgebras, Ideals, and Quotients]] → then branch by need.

# Connections

- [[Symmetry in Quantum Mechanics]] — how a group becomes physical: symmetries as unitary operators on states
- [[Pauli Group]] — a finite non-abelian group central to error correction
- [[Clifford Group]] — the larger finite group generated from it
- [[Magnus Expansion]] / [[Propagators, Time Ordering, and the Dyson Series]] — the time-evolution pages that lean on this folder
- [[(Guide) Thinking Mathematically]] — specializing and generalizing, the two moves this subject is built from

---
Source: Artin, *Algebra*, Ch. 2; Zee, *Group Theory in a Nutshell for Physicists*, Ch. I; Dresselhaus, *Group Theory: Application to the Physics of Condensed Matter*, Ch. 1–3
