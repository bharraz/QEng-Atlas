#group-theory #math

**For spin, one operator $J_z$ labels the states and two operators $J_\pm$ step between them by a fixed amount; every symmetry algebra used in physics has the same anatomy — a largest set of mutually commuting generators supplies the quantum numbers, and every other generator is a ladder operator that shifts them by a fixed vector, called a root.** **In practice:** from the commutation relations alone you can read off how many quantum numbers label a multiplet, which states it contains, which transitions an operator can drive, and whether two algebras (such as $\mathfrak{su}(2)$ and $\mathfrak{su}(1,1)$) are really the same.

The $\mathfrak{su}(2)$ template ($J_z$, $J_\pm$, $|j,m\rangle$) is on [[Lie Algebras (Atlas)]]. Extending that machinery to an arbitrary algebra lets you read multiplet structure off the commutation relations alone.

# Reference

**Formally:** pick a maximal commuting set of generators, diagonalize everything else against it, and any semisimple Lie algebra decomposes into ladder operators labeled by roots — the $\mathfrak{su}(2)$ construction, run in general.

## Killing form and semisimplicity

$$K(X, Y) = \mathrm{Tr}\big(\mathrm{ad}_X\, \mathrm{ad}_Y\big)$$

**Picture:** a weight diagram, one dot per state placed by its commuting quantum numbers; each ladder operator is a fixed arrow (a root) from dot to dot.

**Cartan's criterion:** $\mathfrak g$ is semisimple iff $K$ is nondegenerate. The Killing form is the invariant metric on the algebra — it is what raises and lowers root indices, and its signature separates compact from non-compact real forms (negative definite ⇔ compact). For $\mathfrak{su}(N)$ it reduces to $K(X,Y) \propto \mathrm{Tr}(XY)$, the familiar trace inner product.

## Root space decomposition

A **Cartan subalgebra** $\mathfrak h$ is a maximal abelian subalgebra of simultaneously diagonalizable elements. $\dim\mathfrak h = \mathrm{rank}\,\mathfrak g$ = the number of independent quantum numbers you can assign at once, and = the number of independent Casimirs ([[Universal Enveloping Algebra and PBW Basis]]).

Diagonalize $\mathrm{ad}_H$ for all $H \in \mathfrak h$ simultaneously:
$$\mathfrak g = \mathfrak h \;\oplus \bigoplus_{\alpha \in \Delta} \mathfrak g_\alpha, \qquad [H, E_\alpha] = \alpha(H)\, E_\alpha$$

- **Roots** $\alpha \in \Delta$ are the nonzero eigenvalue-functionals on $\mathfrak h$ — vectors in $\mathfrak h^*$ of dimension = rank.
- **Root vectors** $E_\alpha$ are the ladder operators. Each shifts the Cartan eigenvalues by exactly $\alpha$.
- Root spaces are one-dimensional, and $\alpha \in \Delta \Rightarrow -\alpha \in \Delta$.

**This decomposition is a grading by the root lattice:**
$$[\mathfrak g_\alpha, \mathfrak g_\beta] \subseteq \mathfrak g_{\alpha+\beta}$$
(zero if $\alpha + \beta \notin \Delta \cup \{0\}$, and inside $\mathfrak h$ if $\beta = -\alpha$). Brackets *add* roots, so this is a genuine grading and root-based cutoffs are ideals — unlike degree filtrations ([[Graded and Filtered Lie Algebras]]).

**Every root generates an $\mathfrak{su}(2)$.** The triple $\{E_\alpha,\, E_{-\alpha},\, H_\alpha = [E_\alpha, E_{-\alpha}]\}$ closes as $\mathfrak{sl}(2)$. So the entire subject reduces to "many copies of angular momentum, glued along a lattice" — and every $\mathfrak{su}(2)$ fact you know applies inside each copy.

## Weights and highest-weight representations

For a representation $V$, **weights** are the simultaneous eigenvalues of $\mathfrak h$ on states: $H|\lambda\rangle = \lambda(H)|\lambda\rangle$. Root vectors move between weights, $E_\alpha: |\lambda\rangle \mapsto |\lambda + \alpha\rangle$ — the general form of a selection rule.

The construction, identical in shape to the $\mathfrak{su}(2)$ one:

1. Choose a splitting of $\Delta$ into positive and negative roots.
2. A **highest weight** $\lambda$ is a weight annihilated by every positive root vector.
3. Apply lowering operators until states annihilate. The result is the irrep $V_\lambda$.
4. **Every finite-dimensional irrep of a semisimple algebra arises exactly once this way**, labeled by its highest weight — which is why $\lambda$ (equivalently the Dynkin labels) is a complete name for the multiplet.

| $\mathfrak{su}(2)$ | General semisimple |
|---|---|
| $J_z$ | Cartan subalgebra $\mathfrak h$ |
| $J_\pm$ | root vectors $E_{\pm\alpha}$ |
| $m$ values | weights $\lambda$ |
| $j$ (highest $m$) | highest weight |
| $J^2 = j(j+1)$ | Casimirs, one per rank |
| spin multiplet | weight diagram |

**Tensor products decompose by adding weights**, which is the general Clebsch–Gordan problem: $V_\lambda \otimes V_\mu = \bigoplus_\nu N^\nu_{\lambda\mu} V_\nu$. Coupling two spins is the rank-1 case ([[Group Representations]]).

## Classification

Semisimple complex Lie algebras are exhausted by four families plus five exceptions:

| Family | Algebra | Rank | Dimension | Physics home |
|---|---|---|---|---|
| $A_n$ | $\mathfrak{su}(n{+}1)$ | $n$ | $n(n{+}2)$ | qubits, flavor, color |
| $B_n$ | $\mathfrak{so}(2n{+}1)$ | $n$ | $n(2n{+}1)$ | odd-dimensional rotations |
| $C_n$ | $\mathfrak{sp}(2n)$ | $n$ | $n(2n{+}1)$ | phase space, Gaussian optics ([[Symplectic Group]]) |
| $D_n$ | $\mathfrak{so}(2n)$ | $n$ | $n(2n{-}1)$ | even rotations, Lorentz |
| Exceptional | $G_2, F_4, E_6, E_7, E_8$ | 2, 4, 6, 7, 8 | 14, 52, 78, 133, 248 | GUTs, string compactifications |

Note $B_n$ and $C_n$ share a dimension, and $\mathfrak{sp}(2n)$ having the same dimension $n(2n+1)$ as the symplectic generator count is not a coincidence — it is the same algebra.

**Real forms matter more than the classification.** One complex algebra has several inequivalent real forms, distinguished by the signature of the Killing form, and they behave completely differently in the lab:

| Real form | Compact? | Group | Behavior |
|---|---|---|---|
| $\mathfrak{su}(2)$ | yes | $SU(2)$ | bounded, periodic — Rabi oscillation |
| $\mathfrak{su}(1,1) \cong \mathfrak{sp}(2,\mathbb R)$ | no | $SU(1,1)$ | unbounded, exponential — squeezing, parametric gain |

Both complexify to $\mathfrak{sl}(2,\mathbb C)$, so they have *identical structure constants up to signs*. That is precisely why the disentangling identities differ only by $\tan \leftrightarrow \tanh$ ([[Solving Dynamics on Closed Lie Algebras]]): same algebra, different real form, trigonometric versus hyperbolic. Whenever you meet a new three-generator algebra, identifying which real form it is tells you immediately whether the dynamics oscillates or runs away ([[The Classical Groups Reference]]).

> [!question]- A three-generator algebra has $[K_0, K_\pm] = \pm K_\pm$ and $[K_+, K_-] = -2K_0$. What do you know before solving anything?
> Rank 1, one root pair, so it is a real form of $\mathfrak{sl}(2,\mathbb C)$ — and the sign of $[K_+,K_-]$ makes it $\mathfrak{su}(1,1)$, not $\mathfrak{su}(2)$. Non-compact: unbounded orbits, exponential growth, $\tanh$ rather than $\tan$, and no finite-dimensional unitary representation.

# Connections

- [[Lie Algebras (Atlas)]] — the $\mathfrak{su}(2)$ template, Casimirs, rank, adjoint representation
- [[Graded and Filtered Lie Algebras]] — root-space decomposition as a genuine grading
- [[Subalgebras, Ideals, and Quotients]] — semisimplicity, and the Levi decomposition this half handles
- [[Universal Enveloping Algebra and PBW Basis]] — Casimirs as the center; highest-weight modules
- [[Group Representations]] — irreps, characters, Clebsch–Gordan
- [[SU(2) and SO(3)]] — the rank-1 case and its covering map
- [[The Classical Groups Reference]] — compact vs. non-compact, and the group each algebra generates
- [[Symplectic Group]] — $C_n$ realized as phase-space transformations
- [[Solving Dynamics on Closed Lie Algebras]] — where the $\tan$ / $\tanh$ split shows up in practice

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 7–8; Georgi, *Lie Algebras in Particle Physics*, Ch. 6–8
