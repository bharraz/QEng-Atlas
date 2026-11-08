#group-theory #math

**When you restrict a calculation to a subset of operators — keep $a, a^\dagger, \mathbb 1$ and drop $a^2$, or keep the first few orders of an expansion — two separate things must hold: the operators you keep must close among themselves (a subalgebra, so the dynamics stays inside), and the ones you drop must never generate the ones you keep (an ideal, so they can be discarded).** **In practice:** test both with commutators; only the second makes a truncation legitimate.

# Reference

**Formally:** a subalgebra is closed under bracketing with itself; an ideal is closed under bracketing with everything — and only ideals give quotients, which is what makes a truncation legitimate or illegitimate.

**Picture:** a subalgebra is a room the dynamics cannot leave; an ideal is a drain, where anything that falls in stays in, so it can be discarded without affecting the rest.

| Object | Condition | What it gives you |
|---|---|---|
| Subspace | closed under $+$, scalars | nothing structural |
| **Subalgebra** $\mathfrak h$ | $[\mathfrak h, \mathfrak h] \subseteq \mathfrak h$ | a self-contained sub-dynamics: start in $\mathfrak h$, stay in $\mathfrak h$ |
| **Ideal** $\mathfrak h$ | $[\mathfrak g, \mathfrak h] \subseteq \mathfrak h$ | the quotient $\mathfrak g/\mathfrak h$ exists — you may *discard* $\mathfrak h$ |

Every ideal is a subalgebra; the converse fails badly. In a Lie algebra left and right ideals coincide, by antisymmetry of the bracket — so there is only one notion, unlike rings.

**Why only ideals give quotients.** Define a bracket on cosets by $[X + \mathfrak h,\; Y + \mathfrak h] = [X,Y] + \mathfrak h$. Expanding with representatives $X + h_1$, $Y + h_2$:
$$[X + h_1,\, Y + h_2] = [X,Y] + \underbrace{[X, h_2] + [h_1, Y] + [h_1, h_2]}_{\text{must lie in } \mathfrak h}$$
The three correction terms land in $\mathfrak h$ for arbitrary $X, Y \in \mathfrak g$ **iff** $[\mathfrak g, \mathfrak h] \subseteq \mathfrak h$. If $\mathfrak h$ is only a subalgebra, the answer depends on which representatives you picked — the quotient is not well defined, and "working modulo $\mathfrak h$" is meaningless.

**This is the truncation criterion.** Discarding a set of operators is consistent only if what you discard is an ideal, so brackets can never feed it back into what you kept. If the discarded set is merely a subalgebra — or not even that — commutators of the terms you *kept* regenerate the terms you *threw away*, and the error is uncontrolled at every subsequent order. See [[Graded and Filtered Lie Algebras]] for when a degree cutoff does and does not produce an ideal, and [[Weyl Algebra and Degree Filtration]] for the case where it demonstrably does not.

**"Exact at a given order" is a statement about a quotient.** It means: the computation was performed in $\mathfrak g/\mathfrak h$, the neglected $\mathfrak h$ is an ideal, and its contribution is bounded by the order parameter. Absent the ideal property there is no such statement to make.

**Homomorphisms** — for a Lie algebra map $\varphi: \mathfrak g \to \mathfrak g'$:

- $\ker\varphi$ is always an **ideal**: $\varphi([X,k]) = [\varphi X, \varphi k] = [\varphi X, 0] = 0$.
- $\mathrm{im}\,\varphi$ is always a **subalgebra**, not generally an ideal.
- $\mathfrak g/\ker\varphi \cong \mathrm{im}\,\varphi$ (first isomorphism theorem). Ideals and quotients are exactly the kernels and images of maps.

## Ways algebras assemble

| Assembly | Structure | Bracket between the pieces |
|---|---|---|
| **Direct sum** $\mathfrak h \oplus \mathfrak k$ | both are ideals | $[\mathfrak h, \mathfrak k] = 0$ — independent, decoupled sectors |
| **Semidirect** $\mathfrak h \rtimes \mathfrak k$ | $\mathfrak h$ ideal, $\mathfrak k$ subalgebra | $[\mathfrak k, \mathfrak h] \subseteq \mathfrak h$ — $\mathfrak k$ *acts on* $\mathfrak h$ |
| **Central extension** | $\mathfrak z$ central ideal | $[\mathfrak g, \mathfrak z] = 0$, but $\mathfrak z$ appears in brackets of $\mathfrak g/\mathfrak z$ |

Worked examples, all from oscillator practice:

- **$\mathfrak h_3 = \{a, a^\dagger, \mathbb 1\}$ is a central extension** of the abelian 2-dimensional $\{a, a^\dagger\}$. The center $\{\mathbb 1\}$ is an ideal, and $\mathfrak h_3 / \{\mathbb 1\}$ is abelian — which is exactly the statement that displacements commute *up to a phase* ([[Displacement Operator]]).
- **$\mathrm{osc} = \mathfrak h_3 \rtimes \{a^\dagger a\}$ is semidirect, not direct.** $\mathfrak h_3$ is an ideal, since $[a^\dagger a, a] = -a$ and $[a^\dagger a, a^\dagger] = a^\dagger$ stay in $\mathfrak h_3$. But $\{a^\dagger a\}$ is *not* an ideal, since $[a, a^\dagger a] = a \notin \{a^\dagger a\}$. You may quotient out the displacements; you may not quotient out the number operator.
- **The Mølmer–Sørensen structure is semidirect:** spin acting on displacement, which is why the result is a *spin-dependent* displacement rather than two independent factors ([[Molmer-Sorensen Gate]]).
- **$\mathfrak{su}(1,1) = \{a^2, a^{\dagger 2}, a^\dagger a\}$ is simple** — no nontrivial ideals at all. There is no consistent way to drop part of the squeezing sector; you keep all three generators or you leave the algebra ([[Symplectic Group]]).

## The two canonical chains

Each term of both series is an ideal of $\mathfrak g$, which is what makes the chains meaningful:

| | Series | Terminates ⇒ | Gives |
|---|---|---|---|
| **Derived** | $\mathfrak g^{(k+1)} = [\mathfrak g^{(k)}, \mathfrak g^{(k)}]$ | **solvable** | Wei–Norman triangular: quadratures only |
| **Lower central** | $\mathfrak g^{k+1} = [\mathfrak g, \mathfrak g^{k}]$ | **nilpotent** | BCH and Magnus **terminate** |

Nilpotent $\Rightarrow$ solvable, never the reverse. The lower central series brackets against *all* of $\mathfrak g$ each time, so it is the harder condition and the stronger result.

**The resulting classification:**

| Name | Definition | Example |
|---|---|---|
| Abelian | $[\mathfrak g, \mathfrak g] = 0$ | $\mathfrak u(1)$ |
| Nilpotent | lower central series → 0 | $\mathfrak h_3$ |
| Solvable | derived series → 0 | $\mathrm{osc}$; upper-triangular matrices |
| **Simple** | non-abelian, no ideals but $0$ and $\mathfrak g$ | $\mathfrak{su}(2)$, $\mathfrak{su}(1,1)$ |
| **Semisimple** | direct sum of simples; no nonzero solvable ideal | $\mathfrak{su}(n)$, $\mathfrak{sp}(2n,\mathbb R)$ |

**Levi decomposition** splits any finite-dimensional Lie algebra as
$$\mathfrak g = \mathfrak s \ltimes \mathrm{rad}(\mathfrak g),$$
semisimple part acting on the **radical** (the maximal solvable ideal). Practical reading: solve the solvable part by quadrature and the semisimple part by representation theory ([[Cartan Subalgebras, Roots, and Weights]]). Semisimple means $\mathrm{rad} = 0$; solvable means $\mathfrak s = 0$.

> [!question]- You keep $\{a, a^\dagger, \mathbb 1\}$ and discard $\{a^2, a^{\dagger 2}\}$. Is that legitimate?
> No. $[a, a^{\dagger 2}] = 2a^\dagger$ lands back in what you kept, so the discarded set is not an ideal — the quadratic terms contaminate the linear sector. The reverse works: $\mathfrak h_3$ *is* an ideal in the quadratic-plus-linear algebra, so displacements can be quotiented away.

# Connections

- [[Dynamical Lie Algebras and Closure]] — the algebra whose ideals these are; the closure table
- [[Graded and Filtered Lie Algebras]] — when "degree $> N$" is an ideal and truncation is exact
- [[Weyl Algebra and Degree Filtration]] — the case where it is not, and why
- [[Cartan Subalgebras, Roots, and Weights]] — the semisimple half of the Levi decomposition
- [[Lie Algebras (Atlas)]] — structure constants, $\mathrm{ad}$, Casimirs
- [[Conjugation]] — ideals as the conjugation-stable subspaces; normal subgroups upstairs
- [[Solving Dynamics on Closed Lie Algebras]] — what solvable and nilpotent give computationally
- [[The Classical Groups Reference]] — semidirect products in the group catalogue
- [[(Map) Group Theory]] — normal subgroups and quotient groups, the group-level analog

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 3; Fulton & Harris, *Representation Theory*, §9 (Levi, radical)
