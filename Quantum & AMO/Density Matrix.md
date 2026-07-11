#quantum

**The state when you don't have a ket: a probability-weighted mixture of projectors, carrying exactly the information that survives ignorance and entanglement.** Classical uncertainty and quantum superposition in one object.

# Reference

$$
\rho = \sum_i p_i\, |\psi_i\rangle\langle\psi_i|, \qquad \langle O \rangle = \mathrm{Tr}(\rho\, O), \qquad i\hbar\,\dot\rho = [H,\rho]
$$

Properties: Hermitian, $\mathrm{Tr}\,\rho = 1$, positive semidefinite ($p_i \geq 0$).

**Purity:** $\mathrm{Tr}\,\rho^2 = 1$ iff pure ($\rho = |\psi\rangle\langle\psi|$, a rank-1 projector); $\mathrm{Tr}\,\rho^2 \geq 1/d$ with the minimum at the maximally mixed $\mathbb{1}/d$. The decomposition $\{p_i, |\psi_i\rangle\}$ is **not unique** — infinitely many ensembles give the same $\rho$, and no measurement can tell them apart. $\rho$ is the complete operational state.

**Reduced states:** for entangled $AB$, subsystem $A$ alone is $\rho_A = \mathrm{Tr}_B\,\rho_{AB}$ — generally mixed even when $\rho_{AB}$ is pure. Entanglement seen locally *is* mixedness.

**Qubit form (Bloch vector):**
$$
\rho = \tfrac{1}{2}\left(\mathbb{1} + \vec{r}\cdot\vec{\sigma}\right), \qquad \vec{r} = \langle\vec\sigma\rangle,\quad |\vec{r}| \leq 1 \;(=1 \text{ pure})
$$

Decoherence in this language: T1/T2 processes shrink $\vec r$ — coherences (off-diagonals in the energy basis) decay at $1/T_2$, populations relax at $1/T_1$.

> [!question]- A qubit entangled with another qubit in a Bell state — what does its own density matrix look like, and why can't local measurements reveal the entanglement?
> $\rho_A = \mathbb{1}/2$, maximally mixed: every local measurement is a coin flip, identical to a classical random bit. The information lives entirely in correlations, accessible only by comparing results on both halves.

# Connections

- [[Bloch Sphere]] — the qubit $\rho$ drawn as a point inside the ball
- [[T1 and T2]] — how $\rho$ decays in real hardware
- [[Positive Semidefinite Matrices]] — the cone $\rho$ lives in
- [[Trace Identities]] — partial trace and $\mathrm{Tr}(\rho O)$ mechanics
- [[Lindblad Master Equation]] — $\dot\rho$ when the environment gets a vote

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §3.4
