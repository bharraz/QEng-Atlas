#quantum-info

**Instead of building an interaction between every pair of qubits, some processors move the qubits themselves: trapped ions are carried between trap zones by changing electrode voltages, neutral atoms ride in moving optical tweezers, electron spins travel in moving potential wells along a silicon channel, and photons fly through fiber.** The questions are whether the qubit's state and its motion survive the trip, and how long the trip takes.

# Reference

**Why move qubits:** any pair can be brought together, so connectivity is not fixed by wiring; gate, memory, and readout can happen in separate zones, which keeps readout light and crosstalk away from stored qubits ([[Mid-Circuit Measurement and Feedforward]]); and a processor can grow beyond a single interaction region.

| Platform | How it moves | Main costs | What is measured |
|---|---|---|---|
| trapped ions (quantum CCD) | time-varying DC electrode voltages move the trapping well; chains are split and merged; junctions route ions in 2D ([[Paul Traps]]) | motional excitation, transport time, and re-cooling with a second species | motional state after transport, qubit coherence across the move |
| neutral atoms | moving tweezers steered by acousto-optic deflectors carry atoms, and hand them to and from static traps ([[Optical Tweezers]]) | heating from acceleration, loss during hand-off, light shifts while moving | survival, temperature, coherence |
| electron spins in silicon | conveyor mode: a travelling wave of gate voltages carries the electron; bucket-brigade mode: tunnelling dot to dot ([[Quantum Dots]]) | spin dephasing from a position-dependent g-factor and spin–orbit coupling, valley excitation, charge errors | transfer fidelity, spin coherence after the move |
| superconducting qubits | the qubits stay put; states are swapped through couplers or sent as microwave photons along a cable | swap errors; cable loss | state-transfer fidelity |
| photons | flying qubits by construction ([[Remote Entanglement and Quantum Networks]]) | loss | arrival probability |

**Moving a trapped particle without heating it.** Carrying a harmonic trap of frequency $\omega$ along a path $x_0(t)$ leaves a particle that started at rest with energy set by the acceleration's spectral content at the trap frequency:

$$
\Delta \bar n = \frac{m}{2\hbar\omega}\left|\int_0^T \ddot x_0(t)\, e^{i\omega t}\, dt\right|^2
$$

- $m$ — mass of the particle (kg)
- $\omega$ — trap angular frequency (rad/s)
- $x_0(t)$ — position of the trap minimum along the path (m)
- $T$ — duration of the move (s)
- $\Delta\bar n$ — motional quanta added

A smooth trajectory lasting many trap periods has almost no acceleration at $\omega$ and adds almost nothing; a fast move can also add nothing if its acceleration profile is shaped to have no component at $\omega$ — the same displaced-oscillator physics as a spin-dependent force ([[Displacement Operator]], [[Adiabatic Ramps and Shortcuts]]).

**Picture:** carrying a full cup — accelerate smoothly, or with a rhythm that does not match the sloshing frequency, and nothing spills.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| sideband spectroscopy after transport | motional quanta added by the move ([[Resolved Sideband Cooling]]) |
| Ramsey across a transport | the phase picked up from field differences along the path, to be tracked or cancelled |
| survival probability after many moves | loss per move for atoms |
| spin-flip probability after shuttling | transfer fidelity for electron spins |
| repeated round trips | small errors per move, amplified |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| motional heating | a non-adiabatic trajectory, or electrode voltage noise | lower gate fidelity until re-cooled |
| phase error | position-dependent magnetic field or light shift along the path | a deterministic phase offset after transport |
| loss | trap too shallow during hand-off or acceleration | missing atoms |
| time cost | splitting, moving, merging, and re-cooling | wall-clock time dominated by transport rather than gates |

> [!question]- A trapped-ion processor's gates take tens of microseconds, yet its circuits run far slower than the gate count suggests. Why?
> Most of the time goes into moving ions: splitting chains, transporting them between zones, merging them, and re-cooling the motion that transport excites, often with sympathetic cooling by a second species. Gates are only a fraction of the schedule, so circuit duration is set by how quickly the ions can be rearranged.

# Connections

- [[Paul Traps]] — the electrode potentials that move ions
- [[Optical Tweezers]] — moving and static traps for atoms
- [[Quantum Dots]] — the silicon channels electrons are shuttled along
- [[Displacement Operator]] — why transport excites a coherent state of motion
- [[Adiabatic Ramps and Shortcuts]] — fast moves without excitation
- [[Resolved Sideband Cooling]] — measuring and removing transport heating
- [[Normal Modes of Ion Chains]] — the modes split and merged chains carry
- [[Mid-Circuit Measurement and Feedforward]] — separate readout zones that transport enables
- [[Remote Entanglement and Quantum Networks]] — photons as the qubits that travel furthest

---
Source: D. Kielpinski, C. Monroe & D. J. Wineland, "Architecture for a large-scale ion-trap quantum computer," *Nature* 417, 709 (2002); D. Bluvstein et al., "A quantum processor based on coherent transport of entangled atom arrays," *Nature* 604, 451 (2022); G. Burkard et al., *Rev. Mod. Phys.* 95, 025003 (2023)
