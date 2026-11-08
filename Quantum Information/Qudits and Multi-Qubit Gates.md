#quantum-info

**Physical systems offer more than two levels per particle and interactions that reach more than two particles at once — a trapped ion has many hyperfine and Zeeman states, a transmon has a ladder of levels, a Rydberg excitation blocks every atom within its radius, one laser beam can illuminate a whole ion chain — so some processors use $d$-level qudits instead of qubits, or apply gates acting on three or more qubits in one step.** Both reduce the number of operations a circuit needs, in exchange for more levels or more qubits that each operation can disturb.

# Reference

**Qudits.** A $d$-level system replaces $\log_2 d$ qubits. Its generalized Pauli operators are the shift and clock operators:

$$
X|j\rangle = |j+1 \bmod d\rangle, \qquad Z|j\rangle = \omega^j|j\rangle, \qquad \omega = e^{2\pi i/d}
$$

- $\lvert j\rangle$ — the levels $0, \dots, d-1$
- $X$ — shift: raises the level cyclically
- $Z$ — clock: phases each level by a power of $\omega$

They satisfy $ZX = \omega XZ$, generalizing the qubit anticommutation, and single-qudit gates plus one entangling two-qudit gate are universal ([[Pauli Group]], [[Universal Gate Sets]]).

**Picture:** a qudit is a dial instead of a switch; a multi-qubit gate is one handshake among several people instead of a chain of pairwise ones.

| | Advantage | Cost |
|---|---|---|
| qudits | fewer particles for the same Hilbert space; natural for spin-$s$ models and some lattice gauge theories; fewer entangling gates in some circuits | more transitions to calibrate (each pair of levels); more leakage paths; readout with $d$ outcomes; higher levels often decay faster |
| multi-qubit gates | one operation replaces a decomposition into many two-qubit gates | errors correlated across all participating qubits; harder calibration; crosstalk |

**Platforms for qudits:** trapped ions (several Zeeman and hyperfine levels addressed by laser or microwave transitions), transmons (lowest three or four levels, with each higher level decaying faster), photons (orbital angular momentum, time bins, frequency bins), and atoms with large nuclear spins ([[Angular Momentum in QM]]).

**Native multi-qubit gates:**

| Gate | Mechanism | Platform |
|---|---|---|
| global Mølmer–Sørensen gate | one bichromatic beam on all ions couples every pair, making an $N$-qubit GHZ state in one step | trapped ions ([[Molmer-Sorensen Gate]]) |
| CCZ via blockade | three atoms within one another's blockade radius; a phase appears only for one specific excitation pattern | Rydberg atoms ([[Rydberg Atoms and Blockade]]) |
| Toffoli or CCZ using a third level | the control's $\lvert 1\rangle$ is temporarily moved to $\lvert 2\rangle$, so one two-qubit interaction becomes doubly conditioned | transmons, photons |
| global rotations and parallel gates | one drive acts on many qubits at once | ions, neutral atoms |

A Toffoli gate decomposed into standard gates takes six CNOTs plus single-qubit and $T$ gates; a native CCZ replaces that with one operation of comparable duration, which pays off when its error is below that of the decomposition.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| readout histograms for each prepared level | qudit assignment fidelity, level by level |
| truth table of a CCZ or Toffoli (output populations for all eight inputs) | the classical action of the gate |
| parity oscillations of the GHZ state a multi-qubit gate makes, at $N$ times the analysis phase | $N$-qubit coherence ([[State and Gate Fidelity]]) |
| lifetime of each qudit level | which levels limit a qudit circuit |

> [!question]- Why does using a transmon's $|2\rangle$ level temporarily make a Toffoli gate cheaper?
> The third level is a state distinguishable from both qubit states. Moving one control's $|1\rangle$ into $|2\rangle$, conditionally, lets a single two-qubit interaction act only when both controls were set, so the doubly conditioned phase needs one two-qubit gate and two qubit–qutrit gates — three interactions instead of six CNOTs. The cost is time spent in $|2\rangle$, which decays faster than $|1\rangle$.

# Connections

- [[Entangling Gates]] — the two-qubit case and its classification
- [[Two-Qubit Gate Mechanisms]] — the interactions multi-qubit gates extend
- [[Molmer-Sorensen Gate]] — the global gate on ion chains
- [[Rydberg Atoms and Blockade]] — blockade among three or more atoms
- [[Superconducting Qubits]] — the transmon ladder used as a qudit
- [[Universal Gate Sets]] — universality with qudits
- [[Pauli Group]] — the qubit case of the clock and shift operators
- [[Leakage, Erasure, and Biased Noise]] — the extra levels as an error channel when not used on purpose
- [[Angular Momentum in QM]] — spin-$s$ systems as natural qudits

---
Source: Y. Wang, Z. Hu, B. C. Sanders & S. Kais, "Qudits and high-dimensional quantum computing," *Front. Phys.* 8, 589504 (2020); M. Ringbauer et al., "A universal qudit quantum processor with trapped ions," *Nature Phys.* 18, 1053 (2022); H. Levine et al., "Parallel implementation of high-fidelity multiqubit gates with neutral atoms," *Phys. Rev. Lett.* 123, 170503 (2019)
