#linear-algebra #math

**A multilinear map is linear in each slot separately — and polarization is the move that recovers the whole map from what it does when every slot holds the same object.**

The practical payoff is a change of viewpoint: a Magnus or BCH term stops being a fixed expression and becomes a map with slots you can fill independently.

# Reference

$T: V_1\times\cdots\times V_k \to W$ is **$k$-linear** if it is linear in each argument with the others held fixed:
$$T(\dots,\; \alpha u + \beta v,\; \dots) = \alpha\,T(\dots, u, \dots) + \beta\,T(\dots, v, \dots)$$

**It is not linear as a function on the product space.** $T(2v, 2w) = 4\,T(v,w)$, not $2\,T(v,w)$ — a $k$-linear map scales as $\lambda^k$ when you scale every slot. This is the most common misreading of the definition.

| $k$ | Name       | Examples                                                                                      |
| --- | ---------- | --------------------------------------------------------------------------------------------- |
| 1   | linear     | any operator                                                                                  |
| 2   | bilinear   | inner product, $u^{\mathsf T}Bv$, cross product ([[Bilinear Forms and Preserved Structures]]) |
| 3   | trilinear  | $(X,Y,Z)\mapsto [X,[Y,Z]]$; scalar triple product                                             |
| $n$ | $n$-linear | $\det$, as a function of the $n$ columns                                                      |
| $k$ | $k$-linear | a nested-bracket string of length $k$                                                         |

**Components are a tensor.** Fix bases and evaluate on basis vectors:
$$T_{i_1 i_2 \dots i_k} = T(e_{i_1}, e_{i_2}, \dots, e_{i_k})$$
Multilinearity means these numbers determine $T$ completely, and "tensor of rank $k$" and "$k$-linear map" are two descriptions of one object — the map is the coordinate-free version, the tensor is its components ([[Index Notation and Tensors]]).

**Symmetry types.** A $k$-linear map is **symmetric** if swapping any two slots leaves it unchanged, **alternating** if a swap flips the sign. Alternating maps vanish whenever two slots hold the same vector — which is why $\det$ is zero on repeated columns, and why the antisymmetry of a commutator makes $[X,X] = 0$.

## Restriction to the diagonal, and polarization

**Filling every slot with the same object** gives a function of one variable:
$$Q(v) = T(v, v, \dots, v)$$

A quadratic form is exactly the diagonal of a bilinear form; $\lVert v\rVert^2$ is the diagonal of the inner product. Information is apparently lost — one argument instead of $k$.

**Polarization is the statement that nothing is lost**, provided $T$ is symmetric. For $k=2$:
$$T(u,v) = \tfrac12\big[Q(u+v) - Q(u) - Q(v)\big]$$

which as the **polarization identity** for an inner product reads $\langle u,v\rangle = \tfrac12(\lVert u+v\rVert^2 - \lVert u\rVert^2 - \lVert v\rVert^2)$: the geometry of angles is already contained in the lengths.

Two general forms, both worth recognizing:

$$k!\;T(v_1,\dots,v_k) = \sum_{S\subseteq\{1,\dots,k\}} (-1)^{k-|S|}\, Q\!\left(\sum_{i\in S} v_i\right)$$

$$T(v_1,\dots,v_k) = \frac{1}{k!}\,\frac{\partial^k}{\partial t_1 \cdots \partial t_k}\, Q\big(t_1 v_1 + \cdots + t_k v_k\big)$$

The second is usually the more useful reading: **the multilinear map is the mixed $k$-th derivative of its own diagonal.** Feeding in a combination and differentiating once per slot un-fills the slots.

**Conditions worth stating:**

- Needs symmetry. On a non-symmetric $T$, polarization returns only the symmetric part — the antisymmetric part is invisible on the diagonal, since $T(v,v)$ kills it.
- Needs division by $k!$, so it works over $\mathbb R$ and $\mathbb C$ and fails in characteristic 2. Not a practical concern here, but it is why the theorem carries a hypothesis.
- Over $\mathbb C$ with a sesquilinear form the real-part formula above is not enough; the full identity needs four terms with $\pm i$ shifts.

## The payoff: Magnus and BCH terms as maps with slots

Each Magnus term is built from nested brackets of the generator at different times. Read as an expression, $\Omega_2$ is a fixed double integral. Read as a map, it is a **bilinear** map fed the same function twice:

| | Expression view | Multilinear view |
|---|---|---|
| $\Omega_2$ | $\tfrac12\int\!\!\int [A(t_1), A(t_2)]$ | the bilinear map $B(f,g) = \tfrac12\int\!\!\int[f(t_1), g(t_2)]$, evaluated at $f = g = A$ |
| $\Omega_k$ | a $k$-fold integral of nested brackets | a $k$-linear map, diagonal-evaluated |

What the second view buys:

- **Slots can be filled differently.** Split $A = A_0 + V$ and expand each slot independently: $B(A_0 + V,\, A_0 + V) = B(A_0,A_0) + B(A_0,V) + B(V,A_0) + B(V,V)$. Every cross term appears automatically and none is forgotten. This is the systematic route to interaction-picture and average-Hamiltonian expansions ([[Magnus Expansion]]).
- **Symmetry becomes bookkeeping.** Time ordering and the bracket's antisymmetry are statements about slot exchange, so symmetrizing over slots is a legal operation — which is precisely the Fubini step that converts time ordering into commutators ([[Propagators, Time Ordering, and the Dyson Series]]).
- **Degree counting becomes grading.** A $k$-linear map is degree $k$ in its argument, so the Magnus series is graded by slot count. That is the grading which makes order-by-order truncation legitimate ([[Graded and Filtered Lie Algebras]]).
- **The universal terms are maps, not formulas.** The BCH coefficients are properties of the $k$-linear bracket-words themselves, independent of what you substitute — see [[Free Algebras, Words, and Gradings]].

**No new mathematics is involved**, which is the point: you already use bilinear forms and tensors. The move is to stop reading $\Omega_k$ as a formula in $A$ and start reading it as a map awaiting $k$ arguments.

> [!question]- Why does thinking of $\Omega_2$ as a bilinear map make the split $H = H_0 + V$ easier?
> A bilinear map expands in each slot independently, so $B(H_0{+}V, H_0{+}V)$ mechanically produces all four terms with correct ordering — including the two mixed terms, which are the ones dropped by hand. As an expression there is no rule telling you what to expand; as a map, linearity in each slot is the rule.

# Connections

- [[Index Notation and Tensors]] — the components of a multilinear map, and the operations on them
- [[Bilinear Forms and Preserved Structures]] — the $k=2$ case in full; symmetric vs. antisymmetric
- [[Free Algebras, Words, and Gradings]] — bracket-words as the universal multilinear maps BCH is built from
- [[Magnus Expansion]] — $\Omega_k$ as a $k$-linear map; expanding slots to get average-Hamiltonian theory
- [[Propagators, Time Ordering, and the Dyson Series]] — slot symmetrization as the Fubini step
- [[Baker-Campbell-Hausdorff]] — universal bracket-word coefficients
- [[Graded and Filtered Lie Algebras]] — slot count as the grading that licenses truncation
- [[Inner Products and Orthogonality]] — the polarization identity in its most familiar form
- [[Determinant Identities]] — $\det$ as the alternating $n$-linear map on columns

---
Source: Greub, *Multilinear Algebra*, Ch. 1; Blanes, Casas, Oteo & Ros, "The Magnus expansion and some of its applications," *Phys. Rep.* 470, 151 (2009), §2
