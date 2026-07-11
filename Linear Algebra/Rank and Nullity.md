#linear-algebra #math

**Rank counts the dimensions a matrix actually uses; nullity counts the ones it throws away — and they always add up to the input dimension.** A matrix is exactly as informative as its rank.

# Reference

For $A: \mathbb{C}^n \to \mathbb{C}^m$:
$$
\mathrm{rank}(A) + \dim \ker(A) = n
$$
Every input dimension either survives into the range or dies in the kernel — no leaks, no double counting. Column rank = row rank always (not obvious, but true).

**Rank from the SVD:** rank = number of nonzero singular values. This is also the *only numerically honest definition* — in floating point nothing is exactly zero, so "rank" in practice means "number of $\sigma_i$ above a noise-set threshold." A cliff in the singular value spectrum is your rank; a gradual slope means the question is ill-posed.

**Low rank = compressibility.** Keeping the top $k$ singular triplets gives the best rank-$k$ approximation (Eckart-Young), storing $k(m+n)$ numbers instead of $mn$. A data matrix with low numerical rank has few independent things going on — this is why PCA works, and why a bipartite pure state with low Schmidt rank (= rank of the coefficient matrix) is weakly entangled: rank 1 means product state.

**Quick consequences:** $\mathrm{rank}(AB) \le \min(\mathrm{rank}\,A, \mathrm{rank}\,B)$; an outer product $|u\rangle\langle v|$ has rank 1; rank of a density matrix = number of pure states you genuinely need in the mixture.

> [!question]- Your measured $50\times 50$ cross-correlation matrix has singular values $\{12, 8, 3, 0.02, 0.019, \dots\}$. What's the effective rank and what does it tell you?
> Rank 3 — the cliff after $\sigma_3$ separates signal from noise floor. Only three independent modes/mechanisms are present in the data; the other 47 dimensions are noise.

# Connections

- [[Singular Value Decomposition]] — numerical rank and optimal low-rank approximation both live here
- [[Pseudo-Inverse]] — inverts precisely on the rank-$r$ subspace, zero on the null space
- [[Entanglement Measures]] — Schmidt rank of a bipartite state is a matrix rank; rank 1 ⇔ separable pure state
- [[Projectors]] — a rank-$r$ orthogonal projector has exactly $r$ unit eigenvalues; rank = dimension of the retained subspace

---
Source: Strang, *Linear Algebra and Its Applications*, §2.4 and §6.3
