#group-theory #math

**Conjugation $x \mapsto gxg^{-1}$ is the same operation seen from a transformed viewpoint — and reading a sandwiched product as a conjugation tells you at once what is invariant and what is merely frame.**

# Reference

**Two readings of $gxg^{-1}$:**

- **Passive** — $x$ unchanged, described in $g$'s coordinates. A change of basis or frame.
- **Active** — transform by $g$, apply $x$, transform back. "Rotate the apparatus, run the pulse, rotate back" = the same pulse about a rotated axis.

**It is an automorphism** for each fixed $g$: products, inverses and brackets all survive,
$$g(xy)g^{-1} = (gxg^{-1})(gyg^{-1}), \qquad g[x,y]g^{-1} = [gxg^{-1},\, gyg^{-1}].$$
Every algebraically defined property is therefore conjugation-invariant.

**Invariant (the intrinsic data of $x$):** eigenvalue spectrum, trace, determinant, rank, characteristic polynomial, Jordan structure, order of a group element. **Not invariant (viewpoint):** matrix entries, eigenvector components.

**Conjugacy class** $= \{gxg^{-1} : g \in G\}$, the orbit under change of viewpoint. Classes partition the group and characters are constant on them ([[Group Representations]], [[Point Groups and Character Tables]]). For a rotation group: angle is intrinsic, axis is viewpoint, so a class is "all rotations by the same angle."

**Structures stable under conjugation get names:**

| Fixed by all conjugations | Name | Where it matters |
|---|---|---|
| A subgroup | **normal** subgroup | kernels of homomorphisms; quotient groups exist ([[(Map) Group Theory]]) |
| An element (commutes with all) | **center** | global phases, Casimirs |
| A subspace of $\mathfrak g$ | **ideal** | quotient algebras exist ([[Subalgebras, Ideals, and Quotients]]) |

## Ad, ad, and the Hadamard series

Conjugating an algebra element by a group element stays in the algebra — the algebra is the tangent space at the identity and conjugation fixes the identity, so it can only rotate that tangent space into itself:
$$\mathrm{Ad}_g(X) = g\,X\,g^{-1} \in \mathfrak g \qquad (g \in G,\; X \in \mathfrak g).$$
This is the **adjoint representation**: the group acting on its own generators. Differentiate along $g = e^{tA}$ and conjugation becomes the commutator:
$$\mathrm{ad}_A(X) = [A, X], \qquad e^{A} X e^{-A} = e^{\mathrm{ad}_A} X = X + [A,X] + \tfrac{1}{2!}[A,[A,X]] + \cdots$$
**Conjugation is the group-level operation, $\mathrm{ad}$ its infinitesimal version, and the Hadamard series $e^{\mathrm{ad}_A}$ the bridge.** The structure constants of $\mathfrak g$ are the matrix elements of $\mathrm{ad}$; $\mathrm{ad}$ on $\mathfrak{su}(2)$ is spin 1, which is why conjugating a Pauli by a rotation rotates it as a vector ([[SU(2) and SO(3)]]).

**Reading $\mathrm{ad}_A^{\,n} X$ fluently** is the prerequisite for the Magnus and BCH literature — every term there is a string of nested brackets $\mathrm{ad}_{A_1}\mathrm{ad}_{A_2}\cdots X$. Four cases cover most of what appears:

| Condition on $\mathrm{ad}_A$ | Consequence | Example |
|---|---|---|
| $\mathrm{ad}_A X = 0$ | conjugation is trivial | $X$ in the center; conserved quantity |
| $\mathrm{ad}_A X = c\,\mathbb 1$ (c-number) | series stops at first order | $[a, a^\dagger] = 1$; [[Displacement Operator]] |
| **ad-nilpotent:** $\mathrm{ad}_A^{\,n} = 0$ for some $n$ | $e^{\mathrm{ad}_A}$ is a **finite sum** — exact, non-perturbative | nilpotent algebras; [[Magnus Expansion]] terminates |
| $\mathrm{ad}_A^{\,2} X = -\omega^2 X$ | series resums to $\cos/\sin$ | Pauli rotations, $[J_z,J_\pm] = \pm J_\pm$ |

**The one function identity** — for invertible $g$ and any $f$ defined by a power series:
$$g\,f(X)\,g^{-1} = f\big(gXg^{-1}\big), \qquad \text{in particular} \quad g\,e^{X}g^{-1} = e^{\,gXg^{-1}}.$$
Never transform an exponential term by term; conjugate its generator.

## Where it appears, by name

| Context | The conjugation | What it delivers |
|---|---|---|
| Linear algebra | similarity $S X S^{-1}$ | basis change; spectrum invariant ([[Matrix Decompositions in Practice]]) |
| Quantum frames | $\tilde H = VHV^\dagger + i\hbar\dot V V^\dagger$ | rotating frame, interaction picture — extra term because the frame moves ([[Rotating Frame Transformation]]) |
| Heisenberg picture | $A(t) = U^\dagger A U$ | dynamics moved onto operators |
| Cliffords / stabilizers | $U P U^\dagger$ for Pauli $P$ | gate propagation; stabilizer updates ([[Clifford Group]]) |
| Composite pulses | $R\,(\text{pulse})\,R^{-1}$ | same angle, rotated axis — the error-compensation building block |
| Toggling frame | $H \to U_c^\dagger(t)\, H\, U_c(t)$ | average Hamiltonian theory: noise conjugated by the control |
| Wei–Norman reordering | $e^{gX_i} X_j e^{-gX_i}$ | re-expands in the basis of $\mathfrak g$ ([[Solving Dynamics on Closed Lie Algebras]]) |
| Group theory | conjugacy classes | the "same up to relabeling" partition; characters live here |

Contrast with **congruence** $S^{\mathsf T} B S$, which is what acts on bilinear forms: it preserves signature rather than spectrum ([[Bilinear Forms and Preserved Structures]]).

> [!question]- Without multiplying matrices, what single operation is $R_y(\pi/2)\, R_x(\theta)\, R_y(-\pi/2)$?
> A conjugation, so the angle $\theta$ is unchanged (angle is the class label) and only the axis moves. $R_y(\pi/2)$ sends $\hat x \to -\hat z$, so this is $R_z(-\theta)$.

# Connections

- [[Operators and Superoperators]] — $\mathrm{ad}_H$ as a superoperator; $e^{\mathrm{ad}}$ between rungs
- [[(Map) Group Theory]] — conjugacy classes, normal subgroups, the center
- [[Lie Algebras (Atlas)]] — structure constants and the adjoint representation
- [[Subalgebras, Ideals, and Quotients]] — ideals as the conjugation-stable subspaces
- [[Generators and the Exponential Map]] — the group–algebra bridge conjugation respects
- [[Rotating Frame Transformation]] / [[Interaction Picture]] — frame change as conjugation plus the moving-frame term
- [[Magnus Expansion]] — nested $\mathrm{ad}$ strings; ad-nilpotency as the exactness mechanism
- [[Bilinear Forms and Preserved Structures]] — congruence, the contrasting transform

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 3; Stillwell, *Naive Lie Theory*, Ch. 5
