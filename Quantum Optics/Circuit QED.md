#quantum-optics #solid-state

**Put a superconducting qubit beside a microwave resonator on a chip and they exchange energy like an atom and a cavity mode; detune them and the qubit instead shifts the resonator's frequency by an amount that depends on the qubit's state, so a microwave tone reflected from the resonator reads the qubit without exciting it.** The same Josephson nonlinearity that makes the qubit also makes the resonator's photons interact, which is what turns the resonator into a controllable quantum system in its own right.

# Reference

**Coupling regimes** (coupling $g$, qubit–resonator detuning $\Delta = \omega_q - \omega_r$, resonator linewidth $\kappa$, qubit decay $\gamma$):

| Regime | Condition | What happens |
|---|---|---|
| resonant, strong coupling | $\Delta \approx 0$, $g \gg \kappa, \gamma$ | vacuum Rabi oscillations; split resonator line ([[Jaynes-Cummings Model (Atlas)]]) |
| dispersive | $\lvert\Delta\rvert \gg g$ | no exchange; state-dependent frequency shifts, used for readout |
| strong dispersive | dispersive shift larger than $\kappa$ and $\gamma$ | each photon number shifts the qubit line separately (photon-number splitting) |
| ultrastrong | $g/\omega \gtrsim 0.1$ | the rotating-wave approximation fails; the ground state contains photons |

**The dispersive Hamiltonian, with the transmon's extra levels kept:**

$$
H/\hbar = \omega_r a^\dagger a + \omega_q b^\dagger b + \frac{\alpha}{2}\, b^{\dagger 2} b^2 + \chi_{qr}\, a^\dagger a\, b^\dagger b + \frac{K}{2}\, a^{\dagger 2} a^2
$$

- $a, b$ — annihilation operators of the resonator mode and the transmon
- $\omega_r, \omega_q$ — resonator and qubit frequencies (rad/s)
- $\alpha$ — transmon anharmonicity (rad/s): the qubit's own self-Kerr, negative
- $\chi_{qr}$ — cross-Kerr (rad/s): resonator frequency change per qubit excitation
- $K$ — resonator self-Kerr (rad/s): frequency change per photon

Every nonlinear term comes from expanding the junction's cosine, and every mode coupled to the junction inherits a share of it: $\lvert\chi_{qr}\rvert \approx 2\sqrt{\lvert\alpha K\rvert}$ in this Hamiltonian's convention. Conventions differ by factors of 2 — in the two-level form $\hbar\chi\sigma_z a^\dagger a$ used on [[Superconducting Qubits]], $\chi_{qr} = 2\chi$ ([[Conventions and Factor-of-Two Traps]]).

**Picture:** the qubit is a small weight on a string — it changes the string's pitch depending on its state, and listening to the pitch reads the state without touching it.

**Readout.** A tone near $\omega_r$ is reflected or transmitted with a phase that depends on the qubit state; integrated and plotted in the quadrature (IQ) plane, each prepared state gives a cluster of points.

- **Speed and contrast:** the two states' resonator frequencies differ by $\lvert\chi_{qr}\rvert$; distinguishability per unit time is largest when that difference is about the linewidth ($\lvert\chi_{qr}\rvert \approx \kappa$, i.e. $2\chi \approx \kappa$). A larger $\kappa$ lets information out faster but opens Purcell decay of the qubit through the resonator ([[Purcell Effect]]); a Purcell filter blocks the qubit frequency while passing the resonator's.
- **Measurement-induced dephasing:** photons in the resonator carry information about the qubit, so they dephase it at $\Gamma_m = 8\chi^2\bar n/\kappa$ (for $\chi \ll \kappa$, two-level convention). The same mechanism makes stray thermal photons dephase idle qubits, which is why lines into the cryostat are attenuated and filtered ([[Cryogenics]]).
- **The amplifier chain:** a near-quantum-limited parametric amplifier (JPA or travelling-wave TWPA) first, then a cryogenic HEMT amplifier, then room-temperature electronics; circulators and isolators keep amplifier noise off the qubit. The first amplifier sets the signal-to-noise ratio, and its efficiency is quoted as a measurement efficiency $\eta$.
- **Measurement-induced transitions:** at high photon number, the readout drive itself excites the transmon to higher levels, which caps the usable readout power.

**Photon-number splitting.** In the strong dispersive regime the qubit's transition frequency depends on the resonator's photon number $n$, splitting into separate lines spaced by $\chi_{qr}$. Qubit spectroscopy then reads the resonator's photon-number distribution directly, and qubit pulses selective on one $n$ are the basis of resonator control and parity measurement ([[Controlling Bosonic Modes]]).

**Kerr and photon blockade.** With self-Kerr $K$ larger than $\kappa$, the resonator's levels are unequally spaced, so a drive resonant with $0\to1$ is off resonance for $1\to2$ and admits only one photon at a time — photon blockade. A two-photon drive combined with Kerr stabilizes a pair of coherent states, the Kerr-cat qubit ([[Bosonic Codes]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| resonator spectroscopy against drive power | low power: the dressed frequency shifted by the qubit; high power: the bare frequency returns ("punch-out"), confirming a coupled qubit |
| qubit spectroscopy against flux | the qubit's tuning curve and sweet spot; an avoided crossing with the resonator gives $g$ |
| qubit spectroscopy while the resonator is driven | an AC Stark shift of $\chi_{qr}$ per photon, which calibrates the photon number $\bar n$ |
| photon-number-resolved spectroscopy | $\chi_{qr}$ and the resonator's photon distribution |
| IQ histograms for prepared $\lvert 0\rangle$ and $\lvert 1\rangle$ | assignment fidelity; a tail from the $\lvert 1\rangle$ cluster toward $\lvert 0\rangle$ is decay during readout |
| Ramsey on the qubit against readout-tone amplitude | measurement-induced dephasing rate |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| Purcell decay | the qubit radiates through the readout resonator | $T_1$ that depends on the qubit–resonator detuning |
| thermal photons in the resonator | insufficient attenuation or filtering of lines | dephasing of idle qubits; residual excited population |
| amplifier saturation | readout signal too strong for the parametric amplifier | assignment fidelity falls as readout power rises |
| frequency collisions | multiplexed resonators, or qubits, sit too close in frequency | crosstalk between readout channels |
| measurement-induced transitions | strong readout drives qubit leakage | population in higher levels after readout ([[Leakage, Erasure, and Biased Noise]]) |

> [!question]- Why is readout fastest when the dispersive shift is about one resonator linewidth, rather than as large as possible?
> The two qubit states put the resonator at frequencies $\lvert\chi_{qr}\rvert$ apart, and the readout signal is the difference between the two reflected fields, which leaks out at rate $\kappa$. If the separation is much larger than $\kappa$, the two responses already differ completely, so a larger shift adds nothing while the narrow linewidth still lets the field out slowly. If $\kappa$ is much larger than the separation, the field leaks out quickly but the two responses barely differ. The rate at which distinguishing information leaves is largest in between, with the separation about one linewidth.

# Connections

- [[Jaynes-Cummings Model (Atlas)]] — the Hamiltonian, and its dispersive limit
- [[Cavity QED]] — the same physics with atoms and optical cavities
- [[Superconducting Qubits]] — the transmon and its coherence limits
- [[Josephson Junction]] — the nonlinearity behind every Kerr term
- [[Input-Output Theory]] — how the reflected readout field is computed
- [[Purcell Effect]] — the decay channel readout opens
- [[Controlling Bosonic Modes]] — number-selective control and parity measurement
- [[Bosonic Codes]] — cat and GKP qubits in microwave resonators
- [[Two-Qubit Gate Mechanisms]] — resonator-mediated and coupler-mediated gates
- [[Homodyne Detection]] — measuring the two quadratures of the readout field
- [[Effective Hamiltonians and Adiabatic Elimination]] — dispersive shifts as second-order terms

---
Source: A. Blais, A. L. Grimsmo, S. M. Girvin & A. Wallraff, "Circuit quantum electrodynamics," *Rev. Mod. Phys.* 93, 025005 (2021); P. Krantz et al., "A quantum engineer's guide to superconducting qubits," *Appl. Phys. Rev.* 6, 021318 (2019)
