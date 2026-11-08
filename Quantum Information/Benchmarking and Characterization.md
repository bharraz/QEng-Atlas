#quantum-info

**A quantum processor's errors can be measured at very different levels of detail — one number per gate, a complete error model per gate, or one score for whole circuits — and each method that scales to many qubits does so by assuming something about the noise.** Choosing a method means choosing which assumption to trust; the table lists them.

# Reference

| Method | What it returns | Assumes | Scales to many qubits | Insensitive to SPAM |
|---|---|---|---|---|
| [[Randomized Benchmarking\|randomized benchmarking]] and its variants | average error per Clifford or per gate; crosstalk from simultaneous runs | noise independent of the gate and of time | yes | yes |
| cycle benchmarking / Pauli noise learning | Pauli error rates of a whole layer of gates | noise twirled into a Pauli channel | yes | yes |
| gate set tomography (GST) | a self-consistent model of every gate, preparation, and measurement | noise independent of time | one or two qubits | yes: SPAM is part of the model |
| [[Quantum Process Tomography\|process tomography]] | full process matrix of one gate | perfect preparation and measurement | one or two qubits | no |
| cross-entropy benchmarking (XEB) | fidelity of random circuits | errors scramble the output toward uniform noise | until the ideal circuit can no longer be simulated | partly |
| quantum volume | largest square random circuit the device runs successfully | — | until the ideal circuit can no longer be simulated | partly |
| mirror circuits / Loschmidt echo | probability of returning after a circuit and its inverse | inverse is as noisy as the forward circuit | yes | partly |
| classical shadows / randomized measurements | many observables, fidelities, and Rényi entropies from random-basis snapshots | — | yes, for few-body quantities | robust variants exist |
| Hamiltonian learning | the couplings of the device's native Hamiltonian | the Hamiltonian's form | yes, for local Hamiltonians | depends |

**Linear cross-entropy benchmarking:**

$$
F_\text{XEB} = 2^n \left\langle P_\text{ideal}(x_i) \right\rangle_i - 1
$$

- $n$ — number of qubits
- $x_i$ — the $i$-th measured bitstring
- $P_\text{ideal}(x_i)$ — that bitstring's probability in a classical simulation of the ideal circuit
- $F_\text{XEB}$ — estimated circuit fidelity: 1 if perfect, 0 for uniform noise

A perfect device samples the bitstrings the ideal circuit favours, so their average ideal probability is above $2^{-n}$; noise pushes the samples toward uniform and the average toward $2^{-n}$. Under errors that scramble the output, $F_\text{XEB}$ estimates the circuit fidelity.

**Quantum volume** $V_Q = 2^m$: $m$ is the largest width-equals-depth random circuit for which the device's outputs are "heavy" — bitstrings with above-median ideal probability — more than two-thirds of the time, with statistical confidence.

**Picture:** benchmarks are a fuel-economy rating, one number under a standard cycle; characterization is the engine diagnostic, which tells you which component wastes the fuel.

**Randomized compiling.** Inserting random Pauli gates around each layer, and compiling them into the neighbouring single-qubit gates, turns coherent errors into stochastic Pauli errors without changing the computation. The average error stays the same, but the worst case shrinks, and benchmarks measured on twirled noise then predict circuit performance ([[Quantum Channels]]).

**Gauge freedom in GST.** A gate set and its preparations and measurements can be transformed together without changing any measured probability, so individual-gate quantities such as fidelity depend on a gauge choice; only gauge-invariant predictions are unambiguous.

**What each measurement tells you:**

| Observation | What it points to |
|---|---|
| XEB or mirror-circuit fidelity decaying exponentially with depth | the error per layer, from the decay rate |
| large variation between random circuits of the same size | coherent errors, which depend on the specific circuit |
| circuit fidelity below the product of the gates' benchmarked fidelities | context-dependent errors: crosstalk, spectator effects, errors during parallel operation |
| benchmarks that change from hour to hour | drift; time-resolved benchmarking separates drift from noise |
| Pauli error rates concentrated on particular qubit pairs | crosstalk or a faulty coupler |

> [!question]- Each gate on a device benchmarks well in isolation, but whole-circuit fidelity is lower than the product of the gate fidelities predicts. What does the discrepancy point to?
> Errors that depend on context: ZZ crosstalk and spectator excitation when neighbours operate at the same time, readout crosstalk, leakage that accumulates over depth, drift during long runs, and coherent errors adding in amplitude. Simultaneous randomized benchmarking and cycle benchmarking of full layers isolate them.

# Connections

- [[Randomized Benchmarking]] — the base protocol and its variants
- [[Quantum Process Tomography]] — full characterization of one gate
- [[Quantum State Tomography (Atlas)]] — full reconstruction, and where it stops being feasible
- [[State and Gate Fidelity]] — the quantities these methods estimate
- [[Quantum Channels]] — Pauli channels and twirling
- [[Quantum Error Mitigation]] — using learned noise models to correct averages
- [[Two-Qubit Gate Mechanisms]] — the crosstalk sources benchmarks expose
- [[Quantum Entropies and Information]] — Rényi entropies from randomized measurements

---
Source: J. Eisert et al., "Quantum certification and benchmarking," *Nature Rev. Phys.* 2, 382 (2020); F. Arute et al., *Nature* 574, 505 (2019); A. W. Cross et al., *Phys. Rev. A* 100, 032328 (2019); E. Nielsen et al., *Quantum* 5, 557 (2021); H.-Y. Huang, R. Kueng & J. Preskill, *Nature Phys.* 16, 1050 (2020); J. J. Wallman & J. Emerson, *Phys. Rev. A* 94, 052325 (2016)
