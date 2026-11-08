#solid-state #labwork

**A nearby conductor tuned to the steepest point of its own conductance curve reports the movement of a single electron — the readout mechanism behind every gate-defined qubit, because spin is converted to charge and only charge is measurable.**

# Reference

You cannot measure a single spin magnetically: one Bohr magneton produces a field far below any usable sensitivity. Every gate-defined-qubit experiment therefore runs **spin-to-charge conversion** first, then detects charge ([[Quantum Dots]]).

**The sensor.** Place a second conductor capacitively coupled to the dot — a quantum point contact (QPC) or a single-electron transistor (SET). Its conductance $G(V_g)$ has regions of steep slope: a QPC biased on the flank of a conductance step, or an SET biased on the side of a Coulomb-blockade peak. An electron leaving the dot changes the sensor's electrostatic potential by $\Delta V = e\,C_c/C_\Sigma$, and the sensor converts that to a current change

$$\Delta I \approx \frac{\partial G}{\partial V_g}\, \Delta V\, V_{\text{sd}}$$

**Picture:** a gate-tuned conductor balanced on the steepest part of its conductance curve: one nearby electron moving shifts the curve and swings the current.

- **Bias on the steepest slope.** $\partial G/\partial V_g$ is the entire gain; at a peak or plateau the sensor is blind. Retuning the sensor after every gate-voltage change is a standard part of operating these devices.
- **SET beats QPC** in sensitivity because a Coulomb peak is sharper than a conductance step, at the cost of being harder to keep tuned.
- The sensor is a *charge* detector, so it also sees every stray charge rearrangement — which is why the same devices that read out the qubit are excellent detectors of the charge noise limiting it ([[TLS and Dielectric Loss]], [[Flicker Noise]]).

**Charge stability diagram.** Sweeping two gate voltages while watching the sensor maps out honeycomb cells of fixed occupation $(N_1, N_2)$. Cell boundaries are where an electron enters, leaves, or moves between dots; the geometry of the honeycomb gives the capacitances and the tunnel couplings. This map is the primary diagnostic — you navigate to the $(1,1)\!\leftrightarrow\!(0,2)$ boundary because that is where the physics lives.

## Why RF reflectometry, not DC

DC transport through a sensor is bandwidth-limited by the $RC$ of the cabling: a megohm-scale device driving a coax with pF of capacitance rolls off in the kHz. Since spin relaxation happens in microseconds, DC is far too slow to read a qubit before the answer decays.

**The fix is impedance matching.** Embed the sensor in an $LC$ tank circuit and probe it with a reflected RF carrier at the tank's resonance:

$$\Gamma = \frac{Z_{\text{tank}} - Z_0}{Z_{\text{tank}} + Z_0}, \qquad Z_{\text{tank}}(\omega_0) \approx \frac{L}{C R_{\text{device}}}$$

- The tank transforms a megohm device into something near $Z_0 = 50\ \Omega$, so power couples in and out ([[Characteristic Impedance and Reflection]]).
- Bandwidth becomes the resonator's, not the cable's — MHz, so readout finishes in well under a microsecond.
- The reflected amplitude and phase track $R_{\text{device}}$, hence the sensor's conductance, hence the charge state.
- Multiple sensors at staggered tank frequencies are read on one line by **frequency multiplexing** — the reason large arrays are wireable at all.

**Dispersive gate sensing** removes the sensor entirely. Connect the tank to a *gate* and measure the dot's contribution to the circuit's admittance. Two distinct contributions appear:

| Contribution | Physical origin | What it measures |
|---|---|---|
| **Tunnelling capacitance** | charge moving between dots adiabatically as the drive oscillates | curvature of the charge state's energy, $\propto \partial^2 E/\partial\varepsilon^2$ — sensitive to the interdot tunnel coupling $t_c$ |
| **Sisyphus / relaxation resistance** | charge lagging the drive, dissipating energy | the relaxation rate relative to the drive frequency |

The quantum-capacitance route is a genuinely different measurement: it reports the *curvature* of an energy level rather than a current, needs no ohmic contacts or electron reservoir, and scales because the gate already had to be there. It is the same physics as dispersive readout in circuit QED — probe a resonator whose properties depend on the state ([[Superconducting Qubits]]).

**As with any amplifier chain, the first stage sets the noise floor:** cryogenic HEMTs, or parametric amplifiers for the quantum-limited case ([[Amplifier Noise]]).

> [!question]- Why does a spin-qubit experiment measure charge rather than the spin it cares about?
> A single magnetic moment is undetectable directly. Pauli spin blockade (or energy-selective tunnelling) makes an electron's *ability to move* depend on its spin, so the spin state becomes a charge configuration — and a single charge, unlike a single spin, shifts a nearby conductor's potential enough to be amplified.

# Connections

- [[Quantum Dots]] — the device being read; Pauli spin blockade as the conversion step
- [[Characteristic Impedance and Reflection]] — matching, $\Gamma$, and why the tank circuit is necessary
- [[LC Resonators]] — the tank; $Q$, bandwidth, and multiplexing
- [[Amplifier Noise]] — the first-stage noise floor that sets sensitivity
- [[Superconducting Qubits]] — dispersive readout, the same principle in a different circuit
- [[Flicker Noise]] / [[TLS and Dielectric Loss]] — the charge noise these sensors both suffer and measure
- [[Binomial Errors in State Detection]] — turning discriminated counts into error bars
- [[Lock-In Detection]] — the demodulation the reflected carrier requires

---
Source: Vigneau et al., "Probing quantum devices with radio-frequency reflectometry," *Appl. Phys. Rev.* 10, 021305 (2023); Hanson et al., "Spins in few-electron quantum dots," *Rev. Mod. Phys.* 79, 1217 (2007)
