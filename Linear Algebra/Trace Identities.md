#linear-algebra #math

**The trace is the basis-independent scalar you can always extract from an operator — and cyclic invariance is the identity you'll use daily.** Expectation values, purity, and fidelities are all traces because trace is the unique linear map that doesn't care what basis you compute in.

# Reference

$\mathrm{Tr}\,A = \sum_i A_{ii} = \sum_i \lambda_i$ (eigenvalues with multiplicity, even for non-diagonalizable $A$).

**Cyclic property** — the big one:

$$
\mathrm{Tr}(ABC) = \mathrm{Tr}(BCA) = \mathrm{Tr}(CAB) \qquad (\text{cyclic, NOT arbitrary: } \mathrm{Tr}(ABC) \ne \mathrm{Tr}(ACB) \text{ in general})
$$

Consequences: $\mathrm{Tr}(P^{-1}AP) = \mathrm{Tr}\,A$ (basis independence), $\mathrm{Tr}[A,B] = 0$ always (why $[x,p] = i\hbar$ has no finite-dimensional representation!), and you can rotate operators around inside quantum expectation values $\langle O \rangle = \mathrm{Tr}(\rho O)$.

**Kit of identities:**

| Identity | Use |
|---|---|
| $\mathrm{Tr}(A\otimes B) = \mathrm{Tr}A\cdot\mathrm{Tr}B$ | composite-system normalization |
| $\mathrm{Tr}(A^\dagger B) = \langle A, B\rangle_{HS}$ | Hilbert-Schmidt inner product — operators as vectors |
| $\mathrm{Tr}(|u\rangle\langle v| \, A) = \langle v|A|u\rangle$ | converting outer products to matrix elements |
| $\det e^A = e^{\mathrm{Tr}A}$ | bridge to determinants |
| $\mathrm{Tr}\,\sigma_i\sigma_j = 2\delta_{ij}$ | extracting Bloch components: $r_i = \mathrm{Tr}(\rho\,\sigma_i)$ |

**Partial trace** (pointer): $\mathrm{Tr}_B$ traces out subsystem $B$ only — $\mathrm{Tr}_B(A\otimes B) = A\,\mathrm{Tr}B$ — producing the reduced density matrix; the linear-algebra face of "ignoring the environment."

> [!question]- Use the cyclic property to show no finite-dimensional matrices can satisfy $[x,p]=i\hbar\mathbb{1}$.
> $\mathrm{Tr}[x,p] = \mathrm{Tr}(xp) - \mathrm{Tr}(px) = 0$ by cyclicity, but $\mathrm{Tr}(i\hbar\mathbb{1}) = i\hbar\,n \ne 0$. Contradiction — hence $x,p$ need infinite dimensions, where trace of the commutator is undefined rather than zero.

# Connections

- [[Density Matrix]] — everything measurable is $\mathrm{Tr}(\rho O)$; purity is $\mathrm{Tr}\rho^2$; reduced states via partial trace
- [[Tensor Product]] — the factorization $\mathrm{Tr}(A\otimes B) = \mathrm{Tr}A\,\mathrm{Tr}B$ and where partial trace lives
- [[Determinant Identities]] — trace's multiplicative sibling, joined by $\det e^A = e^{\mathrm{Tr}A}$
- [[Eigenvalues and Eigenvectors]] — $\mathrm{Tr} = \sum\lambda_i$: the free eigenvalue sanity check

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 1; Nielsen & Chuang §2.2.8 (partial trace).
