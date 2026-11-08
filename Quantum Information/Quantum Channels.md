#quantum-info

**A system that interacts with an environment you do not track ends up in a density matrix that depends linearly on its initial one; that map is a quantum channel, and it must output valid states even when the system started entangled with something else — the requirement called complete positivity.** Formally, a quantum channel is the most general physical evolution of a density matrix: a completely positive, trace-preserving (CPTP) linear map — unitaries, noise, and measurement-and-forget are all special cases.

# Reference

$\mathcal{E}(\rho)$ must be linear, trace-preserving, and **completely** positive: $(\mathcal{E}\otimes\mathbb{1})$ positive on any enlarged system. Plain positivity isn't enough because your system may be entangled with a bystander — transpose is positive but $(\mathrm{T}\otimes\mathbb{1})$ on half a Bell state goes negative (which is precisely why partial transpose works as an entanglement *test*).

Every channel has a Kraus form $\mathcal{E}(\rho) = \sum_k K_k \rho K_k^\dagger$, $\sum_k K_k^\dagger K_k = \mathbb{1}$.

**Four ways to write the same channel** — papers switch between them freely:

| Representation | Definition | Best for |
|---|---|---|
| Kraus operators | $\mathcal E(\rho) = \sum_k K_k\rho K_k^\dagger$ | modelling mechanisms ([[Kraus Operators]]) |
| Choi matrix | $J = (\mathcal E\otimes\mathbb 1)(\lvert\Omega\rangle\langle\Omega\rvert)$, $\lvert\Omega\rangle = \sum_i \lvert ii\rangle$ | testing physicality: CP ⇔ $J \ge 0$, TP ⇔ $\mathrm{Tr}_\text{out} J = \mathbb 1$ |
| Pauli transfer matrix (PTM) | $R_{ij} = \tfrac1d \mathrm{Tr}[P_i\, \mathcal E(P_j)]$ | composing channels by matrix multiplication; real-valued; reading off Bloch-vector maps |
| process ($\chi$) matrix | $\mathcal E(\rho) = \sum_{mn}\chi_{mn} P_m\rho P_n^\dagger$ | what process tomography reports ([[Quantum Process Tomography]]) |

- $P_i$ — Pauli strings on $n$ qubits ($4^n$ of them)
- $d$ — Hilbert-space dimension, $2^n$
- $\lvert\Omega\rangle$ — unnormalized maximally entangled state of system and a copy

**Picture:** the Choi matrix is the channel's output when its input is half of a maximally entangled pair — one state that remembers everything the channel does to every input.

For one qubit the PTM has the block form $R = \begin{pmatrix}1 & 0\\ \vec t & M\end{pmatrix}$: the Bloch vector maps as $\vec r \to M\vec r + \vec t$, so $M$ shrinks and rotates it and $\vec t$ shifts it (amplitude damping has $\vec t \ne 0$; unital channels have $\vec t = 0$).

**Standard qubit noise channels:**

| Channel | Kraus operators | What it does |
|---|---|---|
| Depolarizing | $\sqrt{1-\tfrac{3p}{4}}\,\mathbb{1},\ \sqrt{\tfrac{p}{4}}\,\sigma_{x,y,z}$ | shrinks Bloch vector isotropically |
| Dephasing | $\sqrt{1-p}\,\mathbb{1},\ \sqrt{p}\,Z$ | removes the off-diagonal elements, $z$ untouched |
| Amplitude damping | $\begin{pmatrix}1&0\\0&\sqrt{1-\gamma}\end{pmatrix},\ \begin{pmatrix}0&\sqrt{\gamma}\\0&0\end{pmatrix}$ | decay toward $\lvert 0\rangle$ ($T_1$) |

**Pauli channels** — $\mathcal E(\rho) = \sum_i p_i P_i\rho P_i$, a random Pauli error with probability $p_i$ — are the model error correction and most benchmarks assume. Twirling (averaging the channel over random Pauli conjugations) turns any channel into a Pauli channel with the same average fidelity, which is why randomized protocols measure Pauli error rates ([[Benchmarking and Characterization]]).

Continuous-time noise integrates to a channel: $\mathcal{E}_t = e^{\mathcal{L}t}$ with $\mathcal{L}$ a Lindblad generator. Depolarizing is the "averaged" noise every RB twirl produces.

**Distances between channels.** Average gate fidelity compares outputs over all inputs; the **diamond norm** $\lVert\mathcal E - \mathcal F\rVert_\diamond$ is the largest trace distance between outputs, allowing the input to be entangled with an ancilla — the worst case, and the quantity fault-tolerance proofs need. It cannot be measured directly; it is bounded from fidelities and from the coherence of the error ([[State and Gate Fidelity]]).

> [!question]- Why demand *complete* positivity rather than positivity alone?
> Apply the map to half an entangled pair: a merely-positive map like transpose sends $|\Phi^+\rangle\langle\Phi^+|$ to an operator with eigenvalue $-\tfrac12$. Physics must stay positive even when the map acts on part of a larger state — and your qubit is never guaranteed to be unentangled.

# Connections

- [[Kraus Operators]] — the representation theorem and where it comes from
- [[Lindblad Master Equation]] — the differential generator of these maps
- [[Density Matrix]] — the object channels act on
- [[Positive Semidefinite Matrices]] — the cone all of this must preserve
- [[Quantum Process Tomography]] — measuring $\chi$ or the PTM
- [[State and Gate Fidelity]] — average fidelity and the diamond norm compared
- [[Vectorization and Superoperators]] — channels as matrices acting on flattened $\rho$

---
Source: Nielsen & Chuang, Ch. 8.2–8.3; J. Watrous, *The Theory of Quantum Information* (Cambridge, 2018), Ch. 2 and 3
