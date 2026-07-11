#solid-state #quantum

**A quantum dot is a semiconductor structure small enough that electrons are confined in all three dimensions, discretizing the band states into atom-like levels — an "artificial atom" whose energy spectrum, electron number, and couplings are set by fabrication and gate voltages instead of nature.** Two nearly separate research worlds share the name: optically active dots (photon sources) and gate-defined dots (spin qubits).

# Reference

**Confinement scale.** Discreteness matters when the dot size $L$ approaches the electron's effective wavelength. Particle-in-a-box with the band's effective mass:

$$\Delta E \sim \frac{\hbar^2 \pi^2}{2 m^* L^2}.$$

Because $m^* \ll m_e$ in semiconductors (GaAs: $0.067\,m_e$), the relevant "Bohr radius" is nanometers-to-tens-of-nm — confinement is achievable lithographically. Level spacing must beat $k_B T$: a 50 nm GaAs dot has $\Delta E \sim$ meV, hence millikelvin operation for spin qubits; a 5 nm colloidal dot has $\Delta E \sim$ eV, visible at room temperature (size-tunable fluorescence — the display/biolabel application, and the Brus-formula regime where emission color reads out diameter).

**Charging energy — the other quantization.** Adding one electron to a small capacitor costs

$$E_C = \frac{e^2}{C_\Sigma},$$

typically 1–10 meV for gate-defined dots. When $E_C \gg k_B T$ and the contacts are weakly coupled (tunnel resistance $\gg h/e^2 = 25.8$ kΩ), electron number $N$ is a good quantum number: **Coulomb blockade**. Sweeping a gate produces conductance peaks at each $N \to N{+}1$ degeneracy — the standard fingerprint, and the way you count electrons down to $N = 1$ exactly. (Same physics as the superconducting island in [[Superconducting Qubits]] — there $4E_C(\hat n - n_g)^2$; a quantum dot is the normal-state, few-electron version.)

**The three families:**

- **Colloidal** (chemically synthesized nanocrystals, CdSe/InP): cheap, room-temperature, size-tuned optics; broad inhomogeneous distributions, blinking — ensemble photonics, not qubits.
- **Self-assembled** (InAs islands grown epitaxially on GaAs): single-photon and entangled-pair sources; excellent single-emitter optics (lifetime-limited lines at 4 K, Purcell-enhanced in cavities — currently the brightest on-demand single-photon sources); random nucleation positions and spectral wander are the fight.
- **Gate-defined** (electrostatic gates deplete a 2DEG or accumulate in Si/SiGe): electron number and tunnel couplings tunable in situ down to the last electron — the spin-qubit platform.

**Spin qubits in gate-defined dots.** A single confined spin is the qubit ($T_2$ in isotopically purified $^{28}$Si: ms with echo; single-qubit fidelities > 99.9%). The workhorse two-spin physics: at zero detuning two neighboring dots realize the **exchange interaction**

$$H = J(V)\; \mathbf{S}_1 \cdot \mathbf{S}_2, \qquad J \approx \frac{4t_c^2}{U} \;\;(\text{Hubbard limit}),$$

with $t_c$ the interdot tunnel coupling and $U$ the on-site charging energy — gate-voltage-tunable over decades on ns timescales; $\sqrt{\text{SWAP}}$ and CZ gates come directly from pulsing $J$. Readout is spin-to-charge conversion: **Pauli spin blockade** (a triplet cannot tunnel into a singlet (0,2) state) turns spin into a charge movement detected by a nearby charge sensor. Single-spin rotations: ESR microwaves or electrically via micromagnet gradients (EDSR). Main decoherence: nuclear-spin bath (fatal in GaAs, engineered away in $^{28}$Si) and charge noise rattling $J$.

> [!question]- Why did the field migrate from GaAs — with its cleaner heterostructures — to silicon for spin qubits?
> Every Ga and As nucleus carries spin, and the hyperfine-coupled nuclear bath limits $T_2^*$ to ~10 ns in GaAs. Silicon's dominant isotope $^{28}$Si is nuclear-spin-zero, and isotopic purification pushes the residual $^{29}$Si below 100 ppm — the bath essentially vanishes, buying five orders of magnitude in coherence and making the materials fight (valley states, interface disorder) worth having.

# Connections

- [[Bloch's Theorem and Band Structure]] — the effective mass $m^*$ that sets every confinement scale
- [[Superconducting Qubits]] — the same charging-energy physics, superconducting flavor
- [[T1 and T2]] — the coherence vocabulary; nuclear bath vs charge noise
- [[Spin Echo and Dynamical Decoupling]] — how quasi-static hyperfine noise is echoed away
- [[Magnetism in Solids]] — exchange: the same $\mathbf{S}_1\cdot\mathbf{S}_2$ that orders magnets, tamed as a gate
- [[Lithography]] — gate-defined dots are drawn by electron-beam lithography

---
Source: Hanson et al., "Spins in few-electron quantum dots," *Rev. Mod. Phys.* 79, 1217 (2007); Burkard et al., "Semiconductor spin qubits," *Rev. Mod. Phys.* 95, 025003 (2023); Senellart et al., *Nat. Nanotech.* 12, 1026 (2017) (photon sources)
