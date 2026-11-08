#quantum-info #math

**Measure many copies of a state and the outcomes are uncertain even when the state is known exactly; entropy quantifies that uncertainty, and the same quantity evaluated on part of an entangled system measures how strongly that part is correlated with the rest.** A handful of entropies — von Neumann, Rényi, relative entropy, mutual information — answer most quantitative questions about information and entanglement.

# Reference

$$
S(\rho) = -\mathrm{Tr}\,\rho\log\rho, \qquad S_\alpha(\rho) = \frac{1}{1-\alpha}\log\mathrm{Tr}\,\rho^\alpha
$$

- $\rho$ — density matrix of the system or subsystem
- $S$ — von Neumann entropy: Shannon entropy of $\rho$'s eigenvalues
- $S_\alpha$ — Rényi entropy of order $\alpha$; $\alpha \to 1$ recovers $S$
- $\log$ — base 2 gives bits; natural log gives nats

$S = 0$ exactly for a pure state and at most $\log d$ for $d$ levels. $S_2 = -\log\mathrm{Tr}\rho^2$ is minus the log of the purity, which is why it is the entropy experiments measure: $\mathrm{Tr}\rho^2$ is an overlap of two copies.

**Picture:** entropy counts effectively equally likely states — $2^{S}$ of them, with $S$ in bits. Half of a Bell pair has two.

| Quantity | Definition | Meaning | Where it appears |
|---|---|---|---|
| entanglement entropy | $S(\rho_A)$ for a pure global state | entanglement between $A$ and the rest ([[Entanglement Measures]]) | many-body physics, tensor networks |
| relative entropy | $S(\rho\Vert\sigma) = \mathrm{Tr}\,\rho(\log\rho - \log\sigma)$ | how distinguishable $\rho$ is from $\sigma$ over many copies | thermodynamics, resource theories, hypothesis testing |
| mutual information | $I(A{:}B) = S(A) + S(B) - S(AB)$ | all correlations between $A$ and $B$, classical and quantum | correlations in mixed and thermal states |
| conditional entropy | $S(A\vert B) = S(AB) - S(B)$ | can be negative; negative values certify entanglement | quantum communication |
| Holevo quantity | $\chi = S\!\left(\sum_i p_i\rho_i\right) - \sum_i p_i S(\rho_i)$ | maximum classical information extractable from states $\rho_i$ sent with probabilities $p_i$ | channel capacities ([[Remote Entanglement and Quantum Networks]]) |

**Properties used constantly:**
- subadditivity $S(AB) \le S(A) + S(B)$, so $I(A{:}B) \ge 0$;
- strong subadditivity $S(ABC) + S(B) \le S(AB) + S(BC)$ — the inequality behind most entropy bounds;
- $\lvert S(A) - S(B)\rvert \le S(AB)$, so a pure global state has $S(A) = S(B)$;
- data processing: no channel increases relative entropy, $S(\mathcal E(\rho)\Vert\mathcal E(\sigma)) \le S(\rho\Vert\sigma)$ ([[Quantum Channels]]).

**Scaling laws for a region of linear size $\ell$:**

| State | Entanglement entropy | Consequence |
|---|---|---|
| ground state of a gapped local Hamiltonian | grows with the region's boundary (area law) | efficiently represented by tensor networks ([[Tensor Networks and MPS]]) |
| ground state of a 1D critical chain | $\tfrac{c}{3}\log\ell$, with $c$ the central charge | logarithmic violation of the area law |
| thermalized state after a quench | grows with the region's volume (volume law) | hard to simulate classically ([[Quench Dynamics and Thermalization]]) |

**Measuring entropies:**

| Method | Gives | Requires |
|---|---|---|
| full tomography | any entropy | small systems only ([[Quantum State Tomography (Atlas)]]) |
| interference of two identical copies (beamsplitter or swap operation) | $S_2$ from the purity | two copies and a way to interfere them |
| randomized measurements | $S_2$ from correlations of outcomes in random bases | single-copy measurements, many random settings ([[Benchmarking and Characterization]]) |

> [!question]- After a quench, a subsystem's Rényi-2 entropy rises. Why does that show entanglement only if the global state stays nearly pure?
> A subsystem also becomes mixed if it entangles with the laboratory environment through decoherence, which is not entanglement within the system. Comparing with the full system: if the subsystem is more mixed than the global state, $S_2(A) > S_2(AB)$, that excess cannot come from the environment alone, and it certifies entanglement between $A$ and the rest of the system.

# Connections

- [[Entanglement Measures]] — Schmidt decomposition, concurrence, and separability
- [[Density Matrix]] — the object every entropy is computed from
- [[Thermal States]] — maximum entropy at fixed energy
- [[Quench Dynamics and Thermalization]] — entanglement growth after a quench
- [[Tensor Networks and MPS]] — why the area law makes ground states simulable
- [[Benchmarking and Characterization]] — randomized measurements of $S_2$
- [[Quantum Channels]] — data processing and channel capacities
- [[Fisher Information and the Cramér-Rao Bound]] — the information measure of parameter estimation

---
Source: Nielsen & Chuang, Ch. 11–12; M. M. Wilde, *Quantum Information Theory*, 2nd ed. (Cambridge, 2017); T. Brydges et al., "Probing Rényi entanglement entropy via randomized measurements," *Science* 364, 260 (2019)
