#solid-state #quantum

**A quantum dot is a semiconductor structure small enough that electrons are confined in all three dimensions, discretizing the band states into atom-like levels — an "artificial atom" whose energy spectrum, electron number, and couplings are set by fabrication and gate voltages instead of nature.** Two nearly separate research worlds share the name: optically active dots (photon sources) and gate-defined dots (spin qubits).

# Reference

**Confinement scale.** Discreteness matters when the dot size $L$ approaches the electron's effective wavelength. Particle-in-a-box with the band's effective mass:

$$\Delta E \sim \frac{\hbar^2 \pi^2}{2 m^* L^2}.$$

Because $m^* \ll m_e$ in semiconductors (GaAs: $0.067\,m_e$), the relevant "Bohr radius" is nanometers-to-tens-of-nm — confinement is achievable lithographically. Level spacing must beat $k_B T$: a 50 nm GaAs dot has $\Delta E \sim$ meV, hence millikelvin operation for spin qubits; a 5 nm colloidal dot has $\Delta E \sim$ eV, visible at room temperature (size-tunable fluorescence — the display/biolabel application, and the Brus-formula regime where emission color reads out diameter).

**Picture:** an artificial atom: a box for electrons small enough that both its energy levels and the energy to add one more electron become discrete and tunable by gates.

**Charging energy — the other quantization.** Adding one electron to a small capacitor costs

$$E_C = \frac{e^2}{C_\Sigma},$$

typically 1–10 meV for gate-defined dots. When $E_C \gg k_B T$ and the contacts are weakly coupled (tunnel resistance $\gg h/e^2 = 25.8$ kΩ), electron number $N$ is a good quantum number: **Coulomb blockade**. Sweeping a gate produces conductance peaks at each $N \to N{+}1$ degeneracy — the standard fingerprint, and the way you count electrons down to $N = 1$ exactly. (Same physics as the superconducting island in [[Superconducting Qubits]] — there $4E_C(\hat n - n_g)^2$; a quantum dot is the normal-state, few-electron version.)

**The three families:**

- **Colloidal** (chemically synthesized nanocrystals, CdSe/InP): cheap, room-temperature, size-tuned optics; broad inhomogeneous distributions, blinking — ensemble photonics, not qubits.
- **Self-assembled** (InAs islands grown epitaxially on GaAs): single-photon and entangled-pair sources; excellent single-emitter optics (lifetime-limited lines at 4 K, Purcell-enhanced in cavities — [[Purcell Effect]]); random nucleation positions and spectral wandering are the main problems.
- **Gate-defined** (electrostatic gates deplete a 2DEG or accumulate in Si/SiGe): electron number and tunnel couplings tunable in situ down to the last electron — the spin-qubit platform.

**Spin qubits in gate-defined dots.** A single confined spin is the qubit. Two encodings are in use, and they trade differently:

| Encoding | Qubit basis | Driven by | Trade |
|---|---|---|---|
| **Loss–DiVincenzo** (single spin) | $\lvert\!\uparrow\rangle, \lvert\!\downarrow\rangle$ in one dot | ESR microwaves, or EDSR via a micromagnet gradient | simplest; needs a static field and a microwave line per qubit |
| **Singlet–triplet** (two spins) | $\lvert S\rangle, \lvert T_0\rangle$ across two dots | gate voltages only — all-electrical | immune to global field noise (a decoherence-free subspace against uniform $B$), but sensitive to *gradients* and to charge noise |

The central two-spin physics: at zero detuning two neighboring dots realize the **exchange interaction**

$$H = J(V)\; \mathbf{S}_1 \cdot \mathbf{S}_2, \qquad J \approx \frac{4t_c^2}{U} \;\;(\text{Hubbard limit}),$$

- $J$ — exchange splitting between singlet and triplet (J, or quoted as $J/h$ in MHz–GHz): the two-qubit coupling rate
- $t_c$ — interdot tunnel coupling (J), set by the barrier gate voltage
- $U$ — on-site charging energy for double occupancy (J)

The form is second-order perturbation theory (coupling² / energy cost): spins exchange only by virtually hopping onto the same dot, which costs $U$ and is allowed only for the singlet by Pauli exclusion — hence the singlet-triplet splitting. Since $t_c$ depends *exponentially* on barrier height, $J \propto t_c^2$ is exponentially gate-tunable, which is what makes ns-scale on/off two-qubit gates possible and simultaneously makes $J$ exquisitely sensitive to charge noise on that gate.

Pulsing $J$ gives $\sqrt{\text{SWAP}}$ and CZ directly — the two-qubit gate is a voltage pulse on a barrier gate.

**Readout is always spin-to-charge conversion**, because a single magnetic moment is undetectable directly:

- **Pauli spin blockade** — a triplet cannot tunnel into the singlet $(0,2)$ state, so *whether the electron moves* depends on the spin. Spin becomes a charge configuration.
- **Energy-selective tunnelling** (Elzerman) — bias so only one spin state has enough energy to leave to a reservoir.

Either way the resulting charge motion is detected by a nearby sensor, read out by RF reflectometry ([[Charge Sensing and Reflectometry]]).

**What limits coherence** — two mechanisms, with opposite fixes:

| Channel | Mechanism | Scaling / fix |
|---|---|---|
| **Nuclear spin bath** | hyperfine coupling to host nuclei; quasi-static, so it dephases $T_2^*$ but echoes away | fluctuation $\propto 1/\sqrt{N_{\text{nuclei}}}$; fatal in GaAs (every Ga, As has spin), removed by isotopic purification to $^{28}$Si ([[Spin Echo and Dynamical Decoupling]]) |
| **Charge noise** | $1/f$ potential fluctuations move the barrier, and $J \propto t_c^2$ with $t_c$ exponential in barrier height | enters as $\partial J/\partial V$ — operate at a sweet spot where the derivative is small, or use symmetric (barrier-only) control ([[Flicker Noise]], [[TLS and Dielectric Loss]]) |

The exponential tunability that makes fast gates possible is the same exponential sensitivity that makes $J$ noisy. That trade is structural, not a materials problem.

**Silicon's own complication: valley degeneracy.** Si's conduction band has multiple degenerate minima, and confinement at an interface splits them by a **valley splitting** that depends on atomic-scale interface disorder — so it varies dot to dot on the same chip. If the valley splitting is not comfortably larger than the Zeeman energy, the "qubit" has extra states to leak into. This is the price silicon charges for its nuclear-spin-free lattice ([[Bloch's Theorem and Band Structure]]).

> [!question]- Why did the field migrate from GaAs — with its cleaner heterostructures — to silicon for spin qubits?
> Every Ga and As nucleus carries spin, and the hyperfine-coupled nuclear bath limits $T_2^*$ to ~10 ns in GaAs. Silicon's dominant isotope $^{28}$Si is nuclear-spin-zero, and isotopic purification pushes the residual $^{29}$Si below 100 ppm — the bath essentially vanishes, buying five orders of magnitude in coherence and making the materials problems (valley states, interface disorder) worth solving.

# Connections

- [[Bloch's Theorem and Band Structure]] — the effective mass $m^*$ that sets every confinement scale, and the valleys
- [[Charge Sensing and Reflectometry]] — how the charge configuration is measured
- [[Superconducting Qubits]] — the same charging-energy physics, superconducting flavor
- [[TLS and Dielectric Loss]] — the surface origin of the charge noise that rattles $J$
- [[T1 and T2]] — the coherence vocabulary; nuclear bath vs charge noise
- [[Spin Echo and Dynamical Decoupling]] — how quasi-static hyperfine noise is echoed away
- [[Magnetism in Solids]] — exchange: the same $\mathbf{S}_1\cdot\mathbf{S}_2$ that orders magnets, used as a gate
- [[Lithography]] — gate-defined dots are drawn by electron-beam lithography
- [[Exchange Interactions]] — kinetic exchange in general, and the other platforms' spin–spin couplings
- [[Two-Qubit Gate Mechanisms]] — exchange gates compared with other platforms
- [[Qubit Transport and Shuttling]] — moving electron spins along silicon channels
- [[Hubbard Models and Mott Insulators]] — dot arrays as Fermi–Hubbard simulators

---
Source: Hanson et al., "Spins in few-electron quantum dots," *Rev. Mod. Phys.* 79, 1217 (2007); Burkard et al., "Semiconductor spin qubits," *Rev. Mod. Phys.* 95, 025003 (2023); Senellart et al., *Nat. Nanotech.* 12, 1026 (2017) (photon sources)
