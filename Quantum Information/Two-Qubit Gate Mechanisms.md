#quantum-info

**Every two-qubit gate works the same way — an interaction that depends on both qubits is switched on long enough to build up a conditional phase or an exchange of excitation — but each platform switches a different interaction: a shared vibrational mode for trapped ions, a Rydberg excitation for neutral atoms, a capacitive coupling for superconducting circuits, wavefunction overlap for electron spins, and a measurement for photons.** The interaction sets the gate's native form, its speed, and its dominant errors.

# Reference

**Across platforms:**

| Platform | Interaction | Native gate | Switched by | Dominant errors | Typical duration |
|---|---|---|---|---|---|
| trapped ions | spin-dependent force on a shared motional mode | Mølmer–Sørensen ($XX$), light-shift ($ZZ$) | laser or microwave pulses | motional heating, mode-frequency drift, laser phase and intensity noise, scattering from Raman beams | tens to hundreds of µs |
| neutral atoms | Rydberg blockade | CZ, and native multi-qubit CZ | Rydberg laser pulses | Rydberg decay, Doppler dephasing, laser noise, atom loss | ~0.1–1 µs |
| superconducting circuits | capacitive or inductive coupling, controlled by frequency or drive | CZ, iSWAP/fSim, cross-resonance ($ZX$) | flux pulses, microwave drives, tunable couplers | leakage, ZZ crosstalk, two-level-system defects, flux noise | tens of ns |
| spins in quantum dots | exchange $J$ from wavefunction overlap | $\sqrt{\mathrm{SWAP}}$; CZ when the two spins' Zeeman energies differ | voltage on the barrier gate | charge noise on $J$, nuclear-spin noise | tens of ns |
| defect spins (NV and others) | dipolar coupling, or hyperfine coupling to a nuclear spin | conditional rotations | microwave and RF pulses | weak coupling, spin-bath noise | µs to ms |
| photons | no direct interaction; measurement and feedforward | probabilistic CZ, fusion | detection | loss, distinguishability | — |

How each coupling arises physically is on [[Exchange Interactions]]; the trapped-ion and Rydberg gates have their own pages ([[Molmer-Sorensen Gate]], [[Rydberg Atoms and Blockade]]).

**Picture:** the platforms differ in the wire, not the message — the message is always a conditional phase or an exchange; the wire is a phonon, a blockade, a capacitor, or overlapping wavefunctions.

**Superconducting gates in detail:**

| Gate | Mechanism | Notes |
|---|---|---|
| CZ through the $\lvert 11\rangle$–$\lvert 20\rangle$ crossing | a flux pulse tunes one transmon so $\lvert 11\rangle$ approaches $\lvert 20\rangle$ (or $\lvert 02\rangle$); the level repulsion shifts $\lvert 11\rangle$ by more than the sum of the shifts of $\lvert 10\rangle$ and $\lvert 01\rangle$, and that excess accumulates as the conditional phase | needs the population to return from $\lvert 20\rangle$, or it leaks ([[Landau-Zener Transitions]]) |
| iSWAP / fSim | tune $\lvert 01\rangle$ and $\lvert 10\rangle$ into resonance so the excitation swaps; fSim$(\theta, \varphi)$ combines a swap angle with a conditional phase | flux-tunable qubits |
| cross-resonance | drive the control qubit at the target's frequency; through the coupling, the target is driven with an amplitude that depends on the control's state, a $ZX$ interaction | fixed-frequency qubits; unwanted terms removed by echoes or cancellation tones |
| parametric gates | modulate a qubit or coupler frequency at the difference (or sum) of the two qubit frequencies to switch on a resonant exchange | fixed frequencies, gates selected by modulation frequency |
| tunable couplers | a third element whose frequency sets the effective coupling, including zero | turns off idle coupling between gates |

**ZZ crosstalk.** With an always-on coupling, each qubit's frequency depends on its neighbour's state by

$$
\zeta = (E_{11} - E_{10} - E_{01} + E_{00})/h
$$

- $E_{ij}$ — energy of the two-qubit state $\lvert ij\rangle$ (J), including all coupling shifts
- $\zeta$ — ZZ coupling (Hz): conditional frequency shift, active even when idle

so idle qubits accumulate unwanted conditional phase. It grows as the square of the coupling, comes from the qubits' higher levels, and is removed by tunable couplers or by pairing qubits whose anharmonicities have opposite signs.

**The speed–error trade, on every platform:** shorter gates spend less time decohering but have broader spectra, which reach unwanted transitions — leakage levels of a transmon, other motional modes and the carrier for ions, the doubly excited Rydberg state for atoms. Pulse shaping is how that trade is moved ([[Pulse Shaping and Optimal Control]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| a chevron (population against pulse duration and detuning) | the coupling, from the oscillation frequency on resonance, and where resonance is; the V-shaped pattern comes from faster, shallower oscillations off resonance |
| Ramsey on one qubit with the other in $\lvert 0\rangle$, then $\lvert 1\rangle$ | the conditional phase of a gate, or $\zeta$ when idle |
| population outside the qubit levels after repeated gates | leakage per gate ([[Leakage, Erasure, and Biased Noise]]) |
| Bell-state fidelity from parity oscillations | entangling quality ([[State and Gate Fidelity]]) |
| interleaved randomized benchmarking | average gate error ([[Randomized Benchmarking]]) |

> [!question]- Why do two fixed-frequency transmons with an always-on coupling show ZZ crosstalk even when no gate is running?
> The coupling mixes $|11\rangle$ with the doubly excited states $|20\rangle$ and $|02\rangle$, which exist because transmons have levels above $|1\rangle$. That mixing shifts $|11\rangle$ by more than the sum of the shifts of $|10\rangle$ and $|01\rangle$, so $\zeta \ne 0$ and each qubit's frequency depends on its neighbour's state. Turning the coupling off with a tunable coupler, or cancelling the shift with an opposite-sign anharmonicity, removes it.

# Connections

- [[Entangling Gates]] — gate classes and their nonlocal coordinates
- [[Molmer-Sorensen Gate]] — the trapped-ion gate in full
- [[Rydberg Atoms and Blockade]] — the neutral-atom gate in full
- [[Superconducting Qubits]] — the transmon levels these gates use
- [[Circuit QED]] — the resonators and couplers between transmons
- [[Exchange Interactions]] — where each coupling comes from
- [[Quantum Dots]] — exchange gates on spin qubits
- [[Photonic Quantum Computing]] — gates made from measurement
- [[Leakage, Erasure, and Biased Noise]] — the error fast gates trade against
- [[Qudits and Multi-Qubit Gates]] — native gates on more than two qubits

---
Source: P. Krantz et al., *Appl. Phys. Rev.* 6, 021318 (2019); C. D. Bruzewicz, J. Chiaverini, R. McConnell & J. M. Sage, *Appl. Phys. Rev.* 6, 021314 (2019); M. Saffman, T. G. Walker & K. Mølmer, *Rev. Mod. Phys.* 82, 2313 (2010); G. Burkard, T. D. Ladd, A. Pan, J. M. Nichol & J. R. Petta, *Rev. Mod. Phys.* 95, 025003 (2023)
