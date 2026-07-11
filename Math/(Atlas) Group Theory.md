#group-theory #math

**A group is the set of transformations that leave some structure unchanged, together with the rule for composing them.** The axioms are the minimal conditions for "a system of reversible moves that stack": you can do one move after another, every move can be undone, and doing nothing counts as a move. This note is the entry point for the whole subject — axioms, the abstraction layer, and the maps between groups.

# Reference

A group is a set $G$ with a binary operation $\cdot$ satisfying four conditions:

- **Closure** — $a \cdot b \in G$. Composing two moves gives a move.
- **Associativity** — $(a \cdot b) \cdot c = a \cdot (b \cdot c)$.
- **Identity** — there is $e$ with $e \cdot a = a \cdot e = a$. The "do nothing" move.
- **Inverse** — every $a$ has $a^{-1}$ with $a \cdot a^{-1} = e$. Every move undoes.

If $a\cdot b = b\cdot a$ for all elements the group is **abelian**; otherwise non-abelian, which is the interesting case (rotations about different axes, matrix products, most symmetry groups).

## The abstraction layer — what a group *is* vs. how it shows up

A group is the abstract structure: a set of elements and a composition rule. Nothing in the definition mentions matrices. The elements are "moves" — rotations, permutations, integer shifts — and the operation is "do one, then the other." The integers under addition are a group and no matrix appears anywhere.

Matrices enter when you want those moves to *act on something*. A **representation** assigns each group element a matrix on a vector space so that matrix multiplication reproduces the group's composition. It is a realization of the group, not the group itself. The tell: the *same* group has *many* representations (the rotation group acts on spin-$\tfrac12$ as $2\times2$ matrices, on 3-vectors as $3\times3$), so the group cannot *be* any one matrix set — it is the common structure behind all of them. Some groups are *defined* as matrices ($SU(2)$ = the $2\times2$ unitaries with $\det=1$), but even then that is one representation among many. A useful guarantee: every finite group and every compact Lie group admits a **faithful** matrix representation — a matrix copy that reproduces it exactly — so matrices are always available even when they are not the definition.

## Maps between groups

- **Homomorphism** — a map $\varphi: G \to H$ preserving composition: $\varphi(a\cdot b) = \varphi(a)\cdot\varphi(b)$. It carries the structure across but may lose information (need not be one-to-one).
- **Isomorphism** — a bijective homomorphism. Then $G \cong H$: the two groups are the *same group in different clothing*, and any structural statement about one holds for the other.
- **Kernel** — the elements a homomorphism sends to the identity, $\ker\varphi = \{g : \varphi(g)=e_H\}$. It measures exactly what the map forgets; $\varphi$ is an isomorphism onto its image precisely when the kernel is trivial.

A **representation is exactly a homomorphism** $\rho: G \to GL(V)$ into invertible matrices — this is the formal link between the abstract group and its matrix realizations (see [[Group Representations]]).

## Internal structure — classes, normal subgroups, quotients

- **Conjugacy class** of $a$: $\{g a g^{-1} : g \in G\}$ — "the same move viewed from every reframing." In a rotation group, all rotations by angle $\theta$ (any axis) form one class. Classes partition the group, and characters of representations are constant on them — classes are the natural resolution at which representation theory sees the group.
- **Normal subgroup** $N \trianglelefteq G$: a subgroup closed under conjugation, $gNg^{-1} = N$. Kernels of homomorphisms are exactly the normal subgroups.
- **Quotient group** $G/N$: collapse $N$ to the identity; elements are cosets $gN$. The quotient is "$G$ with the $N$-information forgotten." The **first isomorphism theorem** ties it together: $G/\ker\varphi \cong \mathrm{im}\,\varphi$.
- **Lagrange's theorem**: for finite groups, $|H|$ divides $|G|$ for any subgroup $H$ — the coset decomposition tiles the group. Element orders divide $|G|$ as a corollary.
- **Center** $Z(G)$: elements commuting with everything. Quotients by (subgroups of) the center produce the covering-group relationships: $SO(3) \cong SU(2)/\{\pm\mathbb{1}\}$ (see [[Lie Groups]]).
- **Direct product** $G \times H$: pairs with componentwise composition — two independent symmetries side by side.

Worked instance in the triangle example below: the rotations $\{e, r, r^2\}$ are a normal subgroup of $D_3$ (conjugating a rotation by anything gives a rotation), the quotient $D_3/\{e,r,r^2\} \cong \mathbb{Z}_2$ is exactly the orientation sign, and the three reflections form a single conjugacy class. The classes of $D_3$ are $\{e\}, \{r, r^2\}, \{s_1, s_2, s_3\}$ — three classes, hence three irreps (dimensions $1, 1, 2$; check $1 + 1 + 4 = 6 = |G|$).

> [!question]- If two groups are isomorphic, what is actually the same and what can differ?
> Everything structural is the same — the multiplication table, orders of elements, which subgroups exist, whether it's abelian. What can differ is only the *labels*: what the elements "are" (rigid motions vs. permutations vs. matrices) and how the operation is written. Isomorphism is the precise statement that those surface descriptions are the same object.

## Worked example — the symmetries of an equilateral triangle

Label the vertices $1,2,3$. The rigid motions mapping the triangle onto itself are: the identity $e$; rotations $r, r^2$ by $120°$ and $240°$; and three reflections $s_1, s_2, s_3$ across the axis through each vertex. Six elements — this is the **dihedral group $D_3$**. Composition is "do one motion then the next," and it is non-abelian: a rotation followed by a reflection differs from the reverse.

**Isomorphism.** Each symmetry also permutes the three vertices: $r$ is the 3-cycle $1\to2\to3\to1$; each reflection is a transposition (swap two, fix one). Every permutation of three objects appears, and there are exactly $3! = 6$ of them, so the triangle's symmetry group *is the same abstract group* as $S_3$, the permutations of three things: $D_3 \cong S_3$. Two unrelated-sounding real objects — rigid motions of a shape and reshufflings of a list — are one group underneath. This is the abstraction layer earning its keep: a theorem about the abstract order-6 group holds for both at once.

**Representation.** Place the triangle in the plane; each symmetry becomes a $2\times2$ matrix on position vectors — rotations are rotation matrices, reflections are reflection matrices — and matrix products reproduce composition. The six matrices are distinct, so this is a faithful 2D representation. The abstract group, the permutations, and these matrices are three descriptions of one thing.

**Homomorphism and kernel.** Send each symmetry to $+1$ if it preserves orientation (a rotation) and $-1$ if it flips it (a reflection). This is a homomorphism $S_3 \to \{+1,-1\}$: two reflections compose to a rotation, matching $(-1)(-1)=+1$. It is not injective — all three reflections map to $-1$ — so it is a homomorphism but not an isomorphism. Its **kernel**, the elements mapping to $+1$, is exactly the rotations $\{e, r, r^2\}$, a subgroup (the even permutations, $A_3$). This is the sign-of-a-permutation map, the same structure behind the determinant's sign.

Where it shows up: $D_3$ (as the point group $C_{3v}$) is the symmetry group of a triangular molecule like $\mathrm{NH_3}$ viewed along its axis, and $S_3$ is the permutation group governing three identical particles.

# Connections

- [[Symmetry in Quantum Mechanics]] — how a group becomes physical: symmetries act on states as unitary operators
- [[Group Representations]] — a representation is a homomorphism into matrices; irreps are the building blocks
- [[Lie Groups]] — the case where the elements vary continuously (rotations, phases)
- [[Point Groups and Character Tables]] — the finite symmetry groups of molecules and defect sites; $D_3$ reappears as $C_{3v}$
- [[Pauli Group]] — a finite non-abelian group central to quantum error correction
- [[Clifford Group]] — a larger finite group generated from it

---
Source: Artin, *Algebra*, Ch. 2; Zee, *Group Theory in a Nutshell for Physicists*, Ch. I; Dresselhaus, *Group Theory: Application to the Physics of Condensed Matter*, Ch. 1–3
