#linear-algebra #math

**A tensor is an object whose components transform in a fixed way under change of basis, and index notation is the bookkeeping that makes every multilinear operation on them mechanical.**

# Reference

**Einstein summation:** a repeated index is summed over. $v^i w_i \equiv \sum_i v^i w_i$.

Two kinds of index, and the discipline that catches most errors:

| | Appears | Called | Rule |
|---|---|---|---|
| **Free** index | once per term | names the equation's slots | must match on both sides of `=` and in every term |
| **Dummy** index | twice per term, once up once down | summed away | its name is arbitrary; never let it appear three times |

An index appearing three times, or a free index that differs across terms, is always an error — check this before checking the algebra.

**Up vs. down.** Components with an upper index (**contravariant**, vectors $v^i$) and a lower index (**covariant**, covectors $\omega_i$) transform *inversely*:
$$v^{i'} = \frac{\partial x^{i'}}{\partial x^{i}}\, v^{i}, \qquad \omega_{i'} = \frac{\partial x^{i}}{\partial x^{i'}}\, \omega_{i}$$

That is the whole point: the two Jacobians cancel, so the contraction $\omega_i v^i$ is the **same number in every basis**. A rank-$(p,q)$ tensor has $p$ upper and $q$ lower indices and transforms with $p$ copies of the Jacobian and $q$ of its inverse.

**The metric raises and lowers**: $v_i = g_{ij}v^j$, $\;v^i = g^{ij}v_j$, with $g^{ij}g_{jk} = \delta^i_k$. In an orthonormal Cartesian basis $g_{ij} = \delta_{ij}$, which is exactly why physicists working in Cartesian coordinates can put every index downstairs and never notice. The distinction becomes unavoidable in curvilinear coordinates ([[Curvilinear Coordinates]]) and in Minkowski space, where $\eta_{\mu\nu} = \mathrm{diag}(-1,1,1,1)$ and raising flips a sign.

## The operations

| Operation | In indices | Effect on rank |
|---|---|---|
| Outer product | $T^{ij} = v^i w^j$ | adds |
| **Contraction** | $T^{i}{}_{i}$ | subtracts 2 — the basis-independent trace |
| Symmetrize | $T_{(ij)} = \tfrac12(T_{ij} + T_{ji})$ | same |
| Antisymmetrize | $T_{[ij]} = \tfrac12(T_{ij} - T_{ji})$ | same |
| Raise / lower | $g^{ij}T_{jk}$ | same |

Any rank-2 tensor splits uniquely as $T_{ij} = T_{(ij)} + T_{[ij]}$, and the two halves never mix under rotation — which is why the symmetric and antisymmetric parts of a physical tensor mean different things ([[Bilinear Forms and Preserved Structures]]).

**The two invariant symbols.**

$$\delta_{ij} = \begin{cases}1 & i=j\\ 0 & \text{else}\end{cases} \qquad\qquad \varepsilon_{ijk} = \begin{cases}+1 & ijk \text{ an even permutation of } 123\\ -1 & \text{odd}\\ 0 & \text{repeated index}\end{cases}$$

$\varepsilon$ is the totally antisymmetric symbol, and it converts every cross product and curl into index algebra:
$$(\mathbf a \times \mathbf b)_i = \varepsilon_{ijk}a_j b_k, \qquad (\nabla\times\mathbf A)_i = \varepsilon_{ijk}\partial_j A_k, \qquad \det M = \varepsilon_{ijk}M_{1i}M_{2j}M_{3k}$$

**The one identity to memorize** — it generates essentially every vector identity:
$$\boxed{\;\varepsilon_{ijk}\,\varepsilon_{ilm} = \delta_{jl}\delta_{km} - \delta_{jm}\delta_{kl}\;}$$
with the contracted forms $\varepsilon_{ijk}\varepsilon_{ijl} = 2\delta_{kl}$ and $\varepsilon_{ijk}\varepsilon_{ijk} = 6$.

Everything in the vector-identity table falls out of it in two lines:

| Identity | Route |
|---|---|
| $\mathbf a\times(\mathbf b\times\mathbf c) = \mathbf b(\mathbf a\cdot\mathbf c) - \mathbf c(\mathbf a\cdot\mathbf b)$ | two $\varepsilon$'s, apply the box |
| $\nabla\times(\nabla\times\mathbf A) = \nabla(\nabla\cdot\mathbf A) - \nabla^2\mathbf A$ | same, with $\partial$ for $\mathbf a,\mathbf b$ ([[Laplacian]], [[Curl]]) |
| $\nabla\cdot(\nabla\times\mathbf A) = 0$ | $\varepsilon_{ijk}\partial_i\partial_j = 0$: antisymmetric $\times$ symmetric |
| $\mathbf a\cdot(\mathbf b\times\mathbf c)$ cyclic | cyclic symmetry of $\varepsilon_{ijk}$ |

The third row is the general principle worth extracting: **a fully antisymmetric object contracted with a symmetric one vanishes.** Most "why is this zero" questions in index notation are that observation.

**Why the formalism earns its keep:** a tensor equation with matching free indices is basis-independent, so *if it holds in one frame it holds in all*. Choosing a convenient frame to prove an identity is then legitimate rather than a cheat.

## Where they appear

| Tensor | Rank | Note |
|---|---|---|
| Moment of inertia $I_{ij}$ | 2, symmetric | principal axes = its eigenvectors |
| Stress / strain $\sigma_{ij}$ | 2, symmetric | diagonal = pressure, off-diagonal = shear |
| Polarizability $\alpha_{ij}$, susceptibility $\chi_{ij}$ | 2 | why response need not be parallel to drive ([[Dielectrics and Polarizability]], [[Birefringence]]) |
| Field tensor $F^{\mu\nu}$ | 2, antisymmetric | $\mathbf E$ and $\mathbf B$ as one object ([[Maxwell's Equations]]) |
| Metric $g_{\mu\nu}$ | 2, symmetric | the raiser/lowerer itself |
| Structure constants $f_{abc}$ | 3 | $[X_a, X_b] = if_{abc}X_c$ ([[Lie Algebras (Atlas)]]) |

**One caveat, flagged not developed:** in curved space or general coordinates, $\partial_i$ of a tensor is *not* a tensor — the derivative of the basis contributes. Repairing this is what covariant derivatives and Christoffel symbols do, and the Christoffel symbols are themselves not tensors.

> [!question]- Derive $\mathbf a\times(\mathbf b\times\mathbf c) = \mathbf b(\mathbf a\cdot\mathbf c) - \mathbf c(\mathbf a\cdot\mathbf b)$ in index notation.
> $[\mathbf a\times(\mathbf b\times\mathbf c)]_i = \varepsilon_{ijk}a_j\varepsilon_{klm}b_l c_m$. Cycle to $\varepsilon_{kij}\varepsilon_{klm} = \delta_{il}\delta_{jm} - \delta_{im}\delta_{jl}$, giving $a_j b_i c_j - a_j b_j c_i = b_i(\mathbf a\cdot\mathbf c) - c_i(\mathbf a\cdot\mathbf b)$.

# Connections

- [[Multilinear Maps and Polarization]] — the coordinate-free object whose components these indices are
- [[Bilinear Forms and Preserved Structures]] — the rank-2 case, and the symmetric/antisymmetric split
- [[Curvilinear Coordinates]] — where up/down stops being cosmetic
- [[Curl]] / [[Divergence]] / [[Laplacian]] — the vector identities this notation proves in two lines
- [[Stokes and Divergence Theorems]] — antisymmetry and orientation
- [[Tensor Product]] — the algebraic construction behind outer products
- [[Lie Algebras (Atlas)]] — structure constants as a rank-3 tensor
- [[Maxwell's Equations]] — $F^{\mu\nu}$ and index gymnastics in relativistic form

---
Source: Riley, Hobson & Bence, *Mathematical Methods for Physics and Engineering*, Ch. 26; Schutz, *A First Course in General Relativity*, Ch. 3 (transformation-law view)
