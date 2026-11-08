#quantum-info

**Take any physical system with two states that can be prepared, coherently driven into superpositions, and told apart by a measurement — two hyperfine levels of an ion, the two lowest levels of a superconducting circuit, the two polarizations of a photon, two spin projections of an electron — and it holds a qubit: a state $\alpha|0\rangle + \beta|1\rangle$ whose relative phase has no classical counterpart.**

# Reference

$|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ with $|\alpha|^2+|\beta|^2=1$; global phase is unphysical, leaving two real parameters:

$$
|\psi\rangle = \cos\tfrac{\theta}{2}|0\rangle + e^{i\phi}\sin\tfrac{\theta}{2}|1\rangle
$$

- $\theta$ — polar angle on the [[Bloch Sphere]] (rad): sets the populations $\cos^2\tfrac\theta2$, $\sin^2\tfrac\theta2$
- $\phi$ — azimuthal angle (rad): the relative phase between $|0\rangle$ and $|1\rangle$

**The phase $\phi$ is the quantum resource**: populations alone are a classical coin. It is invisible in a measurement of $|0\rangle$ vs $|1\rangle$ and becomes visible only after a rotation converts it into population, which is what [[Ramsey Interferometry]] does.

**Picture:** whatever it is made of, a qubit behaves as a spin-½ in a magnetic field — the same Bloch equations for every platform ([[Two-Level Systems]]).

**What a physical qubit needs**, and how each requirement fails in practice:

| Requirement | Meaning | How it fails |
|---|---|---|
| two well-defined levels | other levels far enough away not to be driven | leakage out of the qubit subspace ([[Leakage, Erasure, and Biased Noise]]) |
| initialization | prepare $\lvert 0\rangle$ reliably | thermal population, imperfect [[Optical Pumping\|optical pumping]] |
| coherent control | rotations about any axis | amplitude and detuning errors, crosstalk ([[Single-Qubit Gates]]) |
| a switchable coupling to other qubits | an interaction that can be turned on for gates | always-on coupling, spectator qubits ([[Two-Qubit Gate Mechanisms]]) |
| single-shot readout | distinguish $\lvert 0\rangle$ from $\lvert 1\rangle$ in one measurement | overlapping readout signals, transitions during readout |
| coherence long compared with operations | $T_1$, $T_2$ much longer than a gate | [[T1 and T2]] |

**Physical realizations** (what $|0\rangle, |1\rangle$ are):

| Platform | Encoding | Splitting | Controlled by | Read out by |
|---|---|---|---|---|
| Trapped ion | hyperfine clock states (¹⁷¹Yb⁺ 12.6 GHz), Zeeman states, or optical S↔D | MHz–GHz; hundreds of THz for optical qubits | lasers, microwaves | state-dependent fluorescence |
| Neutral atom | hyperfine or nuclear-spin states in an optical tweezer | GHz | lasers, microwaves | fluorescence imaging |
| Transmon | two lowest levels of an anharmonic LC oscillator | ~5 GHz | microwave pulses, flux | dispersive shift of a resonator ([[Circuit QED]]) |
| Spin in a quantum dot | electron spin in a field, or singlet–triplet pairs | GHz | voltage pulses, microwaves | spin-to-charge conversion ([[Quantum Dots]]) |
| Defect spin (NV) | $m_s$ sublevels of a spin triplet | GHz | microwaves | spin-dependent fluorescence ([[NV Centers (atlas)]]) |
| Photon | polarization, path, or time-bin | — | linear optics | single-photon detection ([[Photonic Quantum Computing]]) |
| Oscillator mode | cat or GKP code words in one mode | — | qubit-assisted displacements | ancilla qubit ([[Bosonic Codes]]) |

Every platform trades coherence time against gate speed and connectivity; the formalism is identical everywhere.

**What each basic measurement tells you:**

| Measurement | What it tells you |
|---|---|
| spectroscopy (signal vs drive frequency) | the qubit frequency, and its sensitivity to fields |
| [[Rabi Oscillations\|Rabi oscillations]] (population vs pulse length) | drive strength and the π-pulse time |
| Ramsey fringes | detuning from the drive, and $T_2^*$ from the fringe decay |
| echo decay | $T_2$, with slow noise refocused ([[Spin Echo and Dynamical Decoupling]]) |
| population decay after a π pulse | $T_1$ |
| readout histograms for prepared $\lvert 0\rangle$ and $\lvert 1\rangle$ | assignment fidelity of the measurement ([[Binomial Errors in State Detection]]) |

> [!question]- Why isn't a qubit a noisy classical bit with probability $|\alpha|^2$?
> Because amplitudes interfere: a Hadamard on $(|0\rangle+|1\rangle)/\sqrt2$ gives $|0\rangle$ deterministically, while on a 50/50 *mixture* it gives a coin flip. The relative phase is real, controllable, and measurable.

# Connections

- [[Bloch Sphere]] — the geometry of the single-qubit state space
- [[Two-Level Systems]] — the physics side of the same abstraction: gap + coupling
- [[Hyperfine Structure]] — where the ion qubit lives
- [[Single-Qubit Gates]] — the operations that move the state around
- [[T1 and T2]] — the two coherence times every qubit is specified by
- [[Two-Qubit Gate Mechanisms]] — how each platform couples its qubits
- [[Leakage, Erasure, and Biased Noise]] — what happens when the two-level picture fails

---
Source: Nielsen & Chuang, *Quantum Computation and Quantum Information*, §1.2; D. P. DiVincenzo, "The physical implementation of quantum computation," *Fortschr. Phys.* 48, 771 (2000)
