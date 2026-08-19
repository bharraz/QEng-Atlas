#quantum-optics #quantum-info

**Photons barely decohere and barely interact — the first fact makes them the natural flying qubit, the second means every entangling operation must be bought with measurement and probability.**

# Reference

**The structural trade.** A photon in a low-loss medium has essentially no thermal bath to couple to: no cryogenics required for the qubits themselves, and coherence is limited by loss rather than dephasing. The same weak coupling to everything means two photons pass through each other, so there is no deterministic two-qubit gate available.

| | Consequence |
|---|---|
| No bath ⇒ no dephasing | room-temperature qubits; long-distance transmission; the only flying qubit |
| No photon–photon interaction | entangling gates must be **measurement-induced and probabilistic** |
| **Loss is the error model** | not $T_1/T_2$ — a lost photon is an erasure, and erasures are located, which makes them cheaper to correct than unlocated errors |

That last row is the platform's real asymmetry: **photonic errors are mostly erasures**, and knowing *where* an error occurred is worth a great deal to error correction.

**Encodings** — the choice of what carries the qubit:

| Encoding | Basis states | Note |
|---|---|---|
| Polarization | $H, V$ | simple, waveplate-controlled ([[Waveplates]], [[Jones Calculus]]) |
| Dual-rail / path | photon in arm 0 or 1 | native to integrated waveguides; the standard on-chip choice |
| Time-bin | early / late | robust in fibre, where polarization drifts |
| Continuous-variable | quadratures of a squeezed mode | different machine entirely — see below |

**Single-qubit gates are free**: beamsplitters and phase shifters implement any $SU(2)$ on dual-rail, and any $n$-mode passive network is a unitary you can build from them ([[Beamsplitter Transformation]]).

## The entangling problem, and KLM

Two photons on a beamsplitter interfere ([[Hong-Ou-Mandel Interference]]) but do not interact. **KLM** showed universality is nonetheless reachable using only linear optics, ancilla photons, and photon-number-resolving detection: the measurement of the ancillas induces an effective nonlinearity on the signal modes, heralding success some fraction of the time.

- The gate is **probabilistic but heralded** — you know when it worked.
- Boosting success toward 1 costs ancillas and switching, and the overhead is what made naive KLM impractical.
- The resolution is architectural, not optical: build entanglement *before* computing, so failures can be retried ([[Cluster States and Measurement-Based Computation]]). Essentially every modern photonic architecture is measurement-based or fusion-based for this reason.

## What the hardware has to deliver

| Component | Requirement | Why it is hard |
|---|---|---|
| **Single-photon source** | on demand, indistinguishable, high purity | indistinguishability requires identical spectra and no which-path information; quantum dots and SPDC/SFWM heralding are the two routes ([[Quantum Dots]]) |
| **Detectors** | high efficiency, low dark count, number-resolving | superconducting nanowires (SNSPDs) — which is why the *detectors* need cryogenics even though the qubits do not |
| **Low-loss circuits** | dB/cm matters | loss is the error budget; every component is a loss budget line |
| **Fast switching** | feed-forward inside the coherence window | the classical control loop sets the clock ([[Cluster States and Measurement-Based Computation]]) |

**Indistinguishability is the quantity to watch** when reading a photonic paper: HOM visibility is the standard figure, and it is what determines whether interference-based gates work at all. A source can be bright and pure and still useless if its photons are distinguishable.

## Two different machines share the name

- **Discrete-variable** — single photons, dual-rail qubits, KLM/fusion, measurement-based fault tolerance. The route to a universal fault-tolerant machine.
- **Continuous-variable** — squeezed light, quadrature encoding, homodyne measurement, Gaussian operations that are exactly the symplectic group ([[Symplectic Group]], [[Squeezed States]]). Gaussian resources alone are efficiently simulable, so a non-Gaussian element (photon subtraction, GKP states, cubic phase) is required for universality.

**Boson sampling** sits outside both: send $n$ indistinguishable photons into a large random interferometer and sample the output distribution, whose amplitudes are matrix **permanents** — believed classically hard, but not universal and not error-corrected. It is a complexity demonstration, not a computer.

> [!question]- Photons are called the best qubits and the hardest to compute with. Reconcile these.
> The same weak coupling does both. Nothing in the environment couples strongly enough to dephase a photon, which is why they are ideal carriers; and nothing couples two photons either, so no deterministic entangling gate exists. The platform's whole architecture is the workaround: buy entanglement probabilistically, offline, where failure is retryable.

# Connections

- [[Cluster States and Measurement-Based Computation]] — the architecture probabilistic gates force
- [[Hong-Ou-Mandel Interference]] — the two-photon interference every linear-optical gate rests on
- [[Beamsplitter Transformation]] — the mode transformation single-qubit gates are made of
- [[Quantum Dots]] — the leading deterministic single-photon source
- [[Purcell Effect]] — cavity enhancement for source brightness and indistinguishability
- [[Squeezed States]] / [[Symplectic Group]] — the continuous-variable branch and its Gaussian limits
- [[Photon Statistics and g2]] — how single-photon purity is actually measured
- [[Quantum Teleportation]] — the primitive that makes measurement-induced gates work
- [[Photodetection and Shot Noise]] — detector efficiency and dark counts as the error budget

---
Source: Knill, Laflamme & Milburn, *Nature* 409, 46 (2001); Slussarenko & Pryde, "Photonic quantum information processing," *Appl. Phys. Rev.* 6, 041303 (2019)
