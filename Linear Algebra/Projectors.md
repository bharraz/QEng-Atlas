#linear-algebra #math

**$P^2 = P$: apply it twice, nothing more happens — the operator that answers "what part of this vector lives in that subspace."** Quantum measurement is projection: the Born rule weighs states with projectors, and collapse *is* applying one.

# Reference

Idempotence $P^2 = P$ defines a projector; adding Hermiticity $P = P^\dagger$ makes it an **orthogonal** projector (projects along the perpendicular, the only kind QM uses). Eigenvalues are 0 and 1; $\mathrm{Tr}\,P = \mathrm{rank}\,P$ = dimension of the target subspace. Complement: $\mathbb{1} - P$ projects onto the orthogonal subspace.

Rank-1 case, onto normalized $|v\rangle$:

$$
P = |v\rangle\langle v|, \qquad P|\psi\rangle = \langle v|\psi\rangle\, |v\rangle
$$

**Completeness / resolution of identity** — the workhorse identity: for any orthonormal basis,

$$
\sum_i |v_i\rangle\langle v_i| = \mathbb{1}
$$

Insert it anywhere ("insert a complete set of states") to expand in a basis; it's also why probabilities sum to 1.

**Measurement dictionary:** outcome $m$ ↔ projector $P_m$, mutually orthogonal ($P_mP_{m'} = \delta_{mm'}P_m$), complete ($\sum_m P_m = \mathbb{1}$). Probability $p_m = \langle\psi|P_m|\psi\rangle$; post-measurement state $P_m|\psi\rangle/\sqrt{p_m}$. Non-orthogonal generalizations are POVMs.

**Gotcha:** non-Hermitian idempotents exist (oblique projectors, e.g. $\begin{pmatrix}1 & 1\\ 0 & 0\end{pmatrix}$) — they show up in non-orthogonal mode decompositions and can have norm $\gg 1$.

> [!question]- Why must projectors for distinct measurement outcomes be orthogonal, $P_1 P_2 = 0$?
> Outcomes must be repeatable and exclusive: after getting outcome 1, re-measuring must give 1 with certainty, so the post-measurement state must have zero probability of outcome 2 — $\langle\psi|P_1 P_2 P_1|\psi\rangle = 0$ for all $\psi$ forces $P_2 P_1 = 0$.

# Connections

- [[Projective Measurement and POVMs]] — projective measurement formalized, and what replaces it when projectors are too restrictive
- [[Spectral Theorem]] — every normal operator is a $\lambda$-weighted sum of orthogonal projectors
- [[Hermitian Matrices]] — orthogonal projectors are the Hermitian idempotents; observables decompose into them
- [[Block Matrices]] — $P$ and $\mathbb{1}-P$ split space into blocks; invariant subspaces = block-diagonal structure

---
Source: Nielsen & Chuang §2.1.6 & §2.2.5.
