#quantum-info

**A system that touches an environment and is then separated from it ends up in one of several conditions, depending on what the environment recorded; one operator $K_k$ for each possible record, summed over the records nobody looked at, gives the evolution $\rho \to \sum_k K_k \rho K_k^\dagger$.** Each $K_k$ is one thing the environment might have done.

# Reference

$$
\mathcal{E}(\rho) = \sum_k K_k \rho K_k^\dagger, \qquad \sum_k K_k^\dagger K_k = \mathbb{1} \ \ (\text{trace preservation})
$$

- $\rho$ — density matrix of the system before the interaction
- $K_k$ — Kraus operator for environment outcome $k$
- $\mathcal E$ — the resulting channel ([[Quantum Channels]])

**Picture:** a Kraus decomposition is a list of the stories the environment could tell, each weighted by how likely it is, with the story itself discarded.

**Where they come from (Stinespring)**: every channel is a unitary on system + environment, traced out — $K_k = \langle k|_E\, U\, |0\rangle_E$. The Kraus index $k$ is "which state the environment ended in." At most $d^2$ operators needed (Choi rank). A unitary channel is the single-Kraus case.

**Non-uniqueness**: $\{K_k\}$ and $\{K'_j = \sum_k u_{jk} K_k\}$ ($u$ unitary) give the identical channel — different fictions about what the environment recorded, same physics. (Same freedom as purification ensembles of a density matrix.)

**Measurement is the special case where you *do* look**: outcome $m$ occurs with $p_m = \mathrm{Tr}(K_m\rho K_m^\dagger)$, post-state $K_m\rho K_m^\dagger / p_m$; the POVM element is $E_m = K_m^\dagger K_m$. A channel is a measurement with the record discarded.

**Looking continuously gives quantum trajectories.** If the environment's record is read out as it happens — photons counted as they are emitted, for example — each detection applies one jump operator and the state follows a stochastic trajectory; averaging over trajectories recovers the channel. This unravelling is how the [[Lindblad Master Equation]] is simulated and how photon-counting experiments are modelled.

| Kraus set | Physical story |
|---|---|
| $\{K_0, K_1\}$ for amplitude damping | an excited two-level system either did or did not emit a photon |
| $\{\sqrt{1-p}\,\mathbb 1, \sqrt p\,Z\}$ for dephasing | the environment either did nothing, or kicked the phase by π |
| projectors $\{\lvert 0\rangle\langle 0\rvert, \lvert 1\rangle\langle 1\rvert\}$ for dephasing | the environment measured the qubit in the $Z$ basis |

Numerically, Kraus sandwiches vectorize: $K\rho K^\dagger \to (K^* \otimes K)|\rho\rangle\rangle$ — channels become matrices acting on flattened $\rho$.

> [!question]- Dephasing can be written as $\{\sqrt{1-p}\,\mathbb{1}, \sqrt{p}\,Z\}$ or as two projector Kraus sets. Which describes what the environment "really" did?
> Neither — Kraus sets related by an isometry $u_{jk}$ are physically indistinguishable from inside the system. The environment's "story" is not observable; only the map is.

# Connections

- [[Quantum Channels]] — the maps these operators represent
- [[Vectorization and Superoperators]] — the $(K^*\otimes K)$ form for computing with them
- [[Projective Measurement and POVMs]] — keep the outcome instead of summing, and $E_m = K_m^\dagger K_m$
- [[Density Matrix]] — purification non-uniqueness is the same freedom
- [[Lindblad Master Equation]] — the continuous-time version, and its trajectory unravelling

---
Source: Preskill, Ph219 lecture notes, Ch. 3 (Foundations: measurement and evolution)
