#quantum-info

**Measure some qubits partway through a computation while the others keep their quantum state, and use the outcomes to decide what happens next — reset a qubit, apply a correction, choose the next gate.** The classical record becomes part of the circuit; error correction, teleportation, and measurement-based computing all depend on it.

# Reference

**Three operations:**

| Operation | What it does | Typical use |
|---|---|---|
| mid-circuit measurement | projects some qubits while others stay coherent | syndrome extraction, heralding |
| reset | returns a qubit to $\lvert 0\rangle$, by measuring and conditionally flipping or by dissipative pumping | reusing ancillas every round |
| feedforward | classical logic on the outcomes selects later operations | corrections, adaptive circuits |

**Picture:** a mid-circuit measurement is a branch in a program — the circuit continues differently depending on the outcome, and the branch must be chosen before the remaining qubits lose their state.

**The two hard problems.**

*Not disturbing the other qubits.* Reading a qubit usually means scattering photons or driving a resonator, and that disturbance reaches the neighbours:

| Platform | How readout disturbs neighbours | Countermeasures |
|---|---|---|
| trapped ions, neutral atoms | resonant fluorescence photons are absorbed by nearby qubits | move the measured qubits to a separate zone ([[Qubit Transport and Shuttling]]); shelve spectators in levels the light does not address; use a second atomic species for ancillas |
| superconducting circuits | readout photons dephase other qubits through residual coupling; readout tones leak into neighbouring resonators | frequency planning, Purcell filters, careful readout power ([[Circuit QED]]) |
| spin qubits | operating the charge sensor and pulsing gates shift the energies of neighbouring dots | separating readout in time and space from sensitive operations |

*Latency.* Measurement, classical processing, and the conditional pulse must all finish within a small fraction of the coherence time, and for error correction the decoder must keep up with the rounds as they arrive ([[Control Beyond PID]]).

**Many corrections never need applying.** When a correction is a Pauli and the following gates are Cliffords, it can be propagated through the circuit in software and absorbed by relabelling the final outcomes — Pauli-frame tracking. Physical feedforward is needed only before non-Clifford gates and where an operation's choice truly depends on the outcome.

**Uses:**

| Use | Role of the measurement |
|---|---|
| error correction | ancillas measured and reset every round ([[Quantum Error Correction (Atlas)]]) |
| teleportation and gate teleportation | outcomes select the Pauli correction ([[Quantum Teleportation]]) |
| measurement-based computing | outcomes choose later measurement bases ([[Cluster States and Measurement-Based Computation]]) |
| constant-depth state preparation | measurement plus feedforward builds long-range entangled states (GHZ, topological states) in fixed depth instead of depth growing with size |
| erasure and leakage handling | flags and resets errors as they occur ([[Leakage, Erasure, and Biased Noise]]) |
| monitored circuits | studying how repeated measurements compete with entangling dynamics; entanglement undergoes a transition as the measurement rate changes, an open research area |

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Ramsey or echo on idle qubits while a neighbour is read | readout crosstalk onto spectators |
| repeating the same measurement twice | whether readout is quantum non-demolition: repeat agreement |
| residual excited population after reset | reset fidelity |
| time from measurement to the start of the conditional pulse | feedforward latency |

> [!question]- In teleportation the final correction depends on the measurement outcomes. Why can a circuit sometimes skip applying that correction at all?
> The correction is a Pauli. If only Clifford gates follow, a Pauli can be pushed through them — it turns into another Pauli — and its effect on the final results is undone by flipping the interpretation of the measured bits. Only before a non-Clifford gate must the correction be resolved physically, so that is where feedforward latency matters.

# Connections

- [[Quantum Error Correction (Atlas)]] — repeated syndrome measurement and reset
- [[Surface Code]] — the measure-and-reset cycle, and lattice surgery by joint measurements
- [[Quantum Teleportation]] — the protocol that needs feedforward
- [[Cluster States and Measurement-Based Computation]] — computation driven entirely by adaptive measurement
- [[Projective Measurement and POVMs]] — what a measurement does to the state
- [[Circuit QED]] — readout and its crosstalk in superconducting circuits
- [[Qubit Transport and Shuttling]] — moving qubits to separate readout zones
- [[Optical Pumping]] — dissipative reset in atoms and ions
- [[Control Beyond PID]] — real-time classical control and its latency

---
Source: Nielsen & Chuang, §4.4 (deferred measurement); J. M. Pino et al., "Demonstration of the trapped-ion quantum CCD computer architecture," *Nature* 592, 209 (2021); B. Skinner, J. Ruhman & A. Nahum, "Measurement-induced phase transitions in the dynamics of entanglement," *Phys. Rev. X* 9, 031009 (2019)
