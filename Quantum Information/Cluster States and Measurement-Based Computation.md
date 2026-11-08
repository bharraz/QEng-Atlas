#quantum-info

**Prepare one large entangled state first, then compute by measuring its qubits one at a time in adaptively chosen bases — entanglement becomes a consumable resource rather than something gates create.**

# Reference

**Graph state.** Given a graph, put every qubit in $|+\rangle$ and apply CZ along every edge:
$$|G\rangle = \prod_{(i,j)\in E} \mathrm{CZ}_{ij}\;|+\rangle^{\otimes n}$$
A **cluster state** is the graph state on a regular lattice. Since every CZ commutes with every other, the entire state can be built in **one step** regardless of size — the entanglement is not generated sequentially.

Equivalently, it is a stabilizer state fixed by $K_i = X_i \prod_{j\in N(i)} Z_j$, one generator per qubit ([[Stabilizer Formalism]]).

**Picture:** a lattice of qubits entangled in advance like a sheet of fabric; measuring qubits one by one cuts a path through it, and the measurement angles program the computation carried along the path.

**Computing by measuring.** Measure qubits one at a time in the basis $\cos\theta\,X + \sin\theta\,Y$. Each measurement:

- **teleports** the logical state one step across the lattice, and
- applies a rotation set by the angle $\theta$ — so the *choice of measurement basis is the program*.

| Ingredient | Provided by |
|---|---|
| Single-qubit rotations | measurement angle $\theta$ on a chain |
| Two-qubit entangling gate | the lattice's transverse connectivity (CZ already built in) |
| Universality | a 2D lattice suffices; a 1D chain gives single-qubit gates only |

**Adaptivity is mandatory, and it is what sets the clock.** Each measurement outcome is random, leaving a known Pauli byproduct. Later measurement angles must be adjusted for earlier outcomes, so the computation proceeds in a **time order fixed by feed-forward**, even though the resource state was made in one shot. The classical control loop must therefore beat the qubits' coherence — in photonics this means fast switching, and it is the dominant engineering constraint.

**Byproduct operators** are the bookkeeping: outcomes leave Paulis that either get corrected by adjusting later angles or tracked classically to the end (**Pauli frame tracking**, so no physical correction is ever applied to non-Clifford-critical steps).

## Why compute by measurement

| | Circuit model | Measurement-based |
|---|---|---|
| Entanglement | created gate by gate, during the computation | created once, up front, offline |
| Computation is | unitary evolution | adaptive single-qubit measurement |
| Failure of an entangling operation | corrupts the run | can often be **retried** before computing starts |
| Depth | limited by gate errors accumulating | limited by feed-forward latency |

The third row is why photonics adopted it. Entangling photons is **probabilistic** — a fusion attempt succeeds with bounded probability — but if entanglement is generated *before* the computation, a failed attempt is repeated. A probabilistic gate is fatal mid-circuit and merely inconvenient during resource-state assembly ([[Photonic Quantum Computing]]).

**Fusion-based computing** is the modern refinement: rather than assembling one huge cluster, build small identical entangled resource states and join them with two-qubit **fusion measurements**. Failures are absorbed by redundancy, and the fault-tolerance analysis is done on the resulting measurement pattern.

**Equivalences worth knowing:** MBQC and the circuit model are polynomially equivalent — this is a different way to *implement* computation, not a different computational power. A cluster state is a stabilizer state, so preparing one is Clifford and efficiently simulable ([[Magic and Nonstabilizerness]]); all the computational hardness sits in the non-Clifford measurement angles.

**Beyond photonics:** neutral-atom arrays can build graph states with global Rydberg pulses ([[Rydberg Atoms and Blockade]]); the same formalism underpins measurement-based error correction, where the surface code is naturally described as a repeated pattern of stabilizer measurements ([[Surface Code]]).

> [!question]- Why does a probabilistic entangling gate ruin a circuit-model computation but not a measurement-based one?
> In the circuit model the gate happens *during* the computation, so a failure corrupts a state that already carries the result. In MBQC entanglement is built beforehand, so a failed attempt is retried on a state that carries no information yet. Probabilistic operations are acceptable in resource preparation and not in the computation itself.

# Connections

- [[Photonic Quantum Computing]] — the platform this model exists to serve
- [[Stabilizer Formalism]] — graph states as stabilizer states; $K_i = X_i\prod Z_j$
- [[Quantum Teleportation]] — the one-qubit primitive each measurement performs
- [[Surface Code]] — error correction as a repeated measurement pattern
- [[Magic and Nonstabilizerness]] — why the non-Clifford measurement angles carry the hardness
- [[Entangling Gates]] — the circuit-model alternative being traded away
- [[Rydberg Atoms and Blockade]] — graph-state preparation on atom arrays
- [[Universal Gate Sets]] — what a 2D lattice plus adaptive measurement is equivalent to
- [[Mid-Circuit Measurement and Feedforward]] — adaptive measurement as a hardware primitive

---
Source: Raussendorf & Briegel, *Phys. Rev. Lett.* 86, 5188 (2001); Briegel et al., "Measurement-based quantum computation," *Nat. Phys.* 5, 19 (2009)
