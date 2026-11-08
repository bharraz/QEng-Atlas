#quantum-info

**A physical qubit is two levels of a larger system — a transmon has more levels above its first two, an atom has other hyperfine states and can leave its trap, a photon can be absorbed — so some errors take the qubit out of its two levels entirely (leakage), some announce where they happened (erasure), and some come almost always as one type of Pauli error (biased noise).** Each breaks the standard assumption of error correction that errors are random, invisible Paulis: leakage makes correction harder, erasure and bias make it cheaper.

# Reference

| | Leakage | Erasure | Biased noise |
|---|---|---|---|
| What happens | population leaves the qubit levels and stays out | an error occurs and its location is flagged | one Pauli error (usually $Z$) dominates the others |
| Where it comes from | fast pulses reaching the transmon's $\lvert 2\rangle$; off-resonant scattering into other atomic levels; atom loss; other valley or charge states in spin qubits | decay into a level that is detected without disturbing the qubit (e.g. metastable-level qubits in alkaline-earth-like atoms); photon loss in dual-rail encodings | encodings where bit flips are suppressed, such as cat qubits ([[Bosonic Codes]]) |
| Effect on error correction | the leaked qubit no longer behaves as a Pauli error; it persists over many rounds and corrupts its neighbours through entangling gates | a distance-$d$ code corrects up to $d-1$ erasures but only $\lfloor (d-1)/2\rfloor$ unknown errors | codes tailored to the dominant error reach much higher thresholds |
| Remedy | leakage-reduction operations: reset, swap with a fresh qubit, optical repumping; leakage-aware decoding; pulse shaping | make the conversion reliable, so few errors escape unflagged | gates that preserve the bias, so they never turn $Z$ errors into $X$ errors |

**Why knowing the location matters:**

$$
t_\text{unknown} = \left\lfloor \tfrac{d-1}{2} \right\rfloor, \qquad t_\text{erasure} = d - 1
$$

- $d$ — code distance ([[Quantum Error Correction (Atlas)]])
- $t_\text{unknown}$ — correctable errors at unknown positions
- $t_\text{erasure}$ — correctable errors at known positions

A code of distance $d$ distinguishes all error patterns of weight below $d$, but to correct an unknown error it must also infer where it is, which halves the margin. Known locations remove the inference, so roughly twice as many errors are tolerated; the surface code's threshold for pure erasures is about 50%, against 11–19% for unknown Pauli errors, in the idealized setting where only data qubits fail.

**Picture:** an erasure is a missing puzzle piece whose position is known; an unknown Pauli error is a wrong piece that must be found before it can be replaced.

**Leakage in more detail.** A transmon's $|2\rangle$ lies only one anharmonicity away from the qubit transition, so fast or strongly driven pulses reach it ([[Pulse Shaping and Optimal Control]]), and flux-pulse CZ gates pass close to $|20\rangle$ ([[Two-Qubit Gate Mechanisms]]). In atoms and ions, spontaneous scattering during laser gates can end in levels outside the qubit, and atoms can be lost entirely. Because a leaked qubit is invisible to ordinary readout (it is usually read as $|1\rangle$) and does not return by itself, it produces long streaks of detection events in an error-correction experiment.

**Bias, and keeping it.** A cat qubit's bit flips require the oscillator to jump between two well-separated coherent states, which is exponentially suppressed in the mean photon number, while phase flips grow only linearly with it. A repetition code against phase flips then suffices, provided the CNOT and other gates do not convert phase flips into bit flips; such bias-preserving gates exist for cat qubits but not for ordinary two-level qubits.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| leakage randomized benchmarking: population outside the qubit levels against sequence length | leakage rate per gate, and the rate of return ([[Randomized Benchmarking]]) |
| readout that resolves $\lvert 2\rangle$ (three-state readout) | leaked population directly ([[Circuit QED]]) |
| erasure detection with and without induced errors | detection efficiency, and the false-positive rate |
| Pauli error rates from noise learning | the bias ratio $p_Z/(p_X+p_Y)$ ([[Benchmarking and Characterization]]) |
| streaks of detection events in time on one qubit | leakage in an error-correction experiment |

> [!question]- Why does converting errors into erasures help, even if the total error rate stays the same?
> Because a distance-$d$ code corrects $d-1$ errors at known locations but only about half as many at unknown ones: knowing where an error is removes the need to infer it. The gain holds only if the conversion is reliable — errors that escape flagging return to being unknown errors, and the decoder must be told how often that happens.

# Connections

- [[Quantum Error Correction (Atlas)]] — distance, decoders, and the independence assumption
- [[Surface Code]] — where leakage and erasure thresholds are compared
- [[Bosonic Codes]] — cat qubits, the main source of strongly biased noise
- [[Superconducting Qubits]] — the transmon levels leakage goes to
- [[Rydberg Atoms and Blockade]] — erasure conversion in neutral atoms
- [[Optical Pumping]] — repumping leaked atoms and ions back into the qubit
- [[Pulse Shaping and Optimal Control]] — DRAG and other pulses that limit leakage
- [[Mid-Circuit Measurement and Feedforward]] — detecting erasures and resetting leaked qubits mid-circuit
- [[Photonic Quantum Computing]] — photon loss as a heralded error

---
Source: Y. Wu, S. Kolkowitz, S. Puri & J. D. Thompson, "Erasure conversion for fault-tolerant quantum computing in alkaline earth Rydberg atom arrays," *Nature Commun.* 13, 4657 (2022); S. Puri et al., "Bias-preserving gates with stabilized cat qubits," *Sci. Adv.* 6, eaay5901 (2020); C. J. Wood & J. M. Gambetta, "Quantification and characterization of leakage errors," *Phys. Rev. A* 97, 032306 (2018)
