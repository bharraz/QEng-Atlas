#quantum #AMO #ions

**Coulomb coupling turns $N$ ions' motion into $N$ collective normal modes per axis — lasers talk to modes, not to individual ions' motion, and that shared bus is what makes multi-ion gates possible at all.**

# Reference

Expand the potential (trap + mutual Coulomb) around the equilibrium positions and diagonalize the Hessian: $N$ modes per axis with frequencies $\omega_m$ and orthonormal **participation vectors** $b_i^m$ (how much ion $i$ moves in mode $m$).

**Axial modes, the standard sequence:** center-of-mass (COM) at $\omega_z$ with uniform participation $b_i = 1/\sqrt{N}$; stretch (breathing) at $\sqrt{3}\,\omega_z$ with $b_i \propto z_i^{(0)}$ (antisymmetric); third mode at $\sqrt{29/5}\,\omega_z \approx 2.41\,\omega_z$ — the first two frequencies are $N$-independent, higher ones nearly so.

**Coupling:** ion $i$'s Lamb–Dicke parameter for mode $m$ is

$$\eta_i^m = \eta_m\, b_i^m, \qquad \eta_m = k\sqrt{\frac{\hbar}{2 M \omega_m}}$$

- $\eta_i^m$ — [[Lamb-Dicke Regime|Lamb–Dicke parameter]] for driving ion $i$ through mode $m$ (dimensionless): how strongly a laser on ion $i$ pushes that mode
- $b_i^m$ — participation of ion $i$ in mode $m$ (dimensionless, $\sum_i (b_i^m)^2 = 1$): ion $i$'s component of the mode eigenvector
- $\eta_m$ — the mode's Lamb–Dicke parameter for unit participation
- $k$ — laser wavevector projected on the mode's direction of motion (m⁻¹)
- $M$ — mass of one ion (kg)
- $\omega_m$ — mode frequency (rad/s)

Sideband Rabi rates and gate strengths scale with $\eta_i^m$, so participation decides which ions a mode couples. A gate through the stretch mode does not drive the center-of-mass motion, which matters because COM heats fastest: uniform electric-field noise pushes every ion the same way, which is exactly the COM pattern, while stretch and higher modes are far quieter. Since $\eta_m \propto 1/\sqrt{\omega_m}$, higher-frequency modes couple more weakly (slower gates) but sit further from low-frequency noise and heat less.

**Picture:** masses connected by springs: pluck one and the motion spreads, but the chain has a set of patterns (centre-of-mass, stretch, and higher) that each oscillate independently at their own frequency.

**Why gates address modes:** an MS-type spin-dependent force is applied *through one mode*; its participation vector sets which ions feel it and with what sign. **Spectral crowding limits scaling:** $N$ modes per axis pack into a fixed band (radial modes especially — they bunch below the single-ion radial frequency), so off-resonant coupling to spectator modes grows with $N$; fixes are amplitude/phase-modulated pulses that close all loops, or splitting chains. Mode frequencies drift with trap voltages — gate detunings need recalibration against them.

> [!question]- Why do two-qubit gates in long chains often use radial modes and pulse shaping, despite radial modes being spectrally crowded?
> Axial confinement must weaken as $N$ grows (to keep the chain linear), degrading axial $\eta$ and speed; radial modes keep high frequencies. The price — dense mode spectrum — is paid with modulated pulses engineered to close the phase-space loops of *all* modes simultaneously.

# Connections

- [[Linear ODE Systems]] — coupled oscillators diagonalized; participation vectors are the eigenvectors
- [[Molmer-Sorensen Gate]] — the consumer: force applied through one mode, phases weighted by $b_i^m$
- [[Paul Traps]] — provides the well and sets $\omega_z$, plus the RF-null line the chain sits on
- [[Quantum Harmonic Oscillator]] — each mode is one, independently quantized
- [[Qubit Transport and Shuttling]] — splitting, moving, and merging chains

---
Source: Leibfried, Blatt, Monroe & Wineland, *Rev. Mod. Phys.* 75, 281 (2003); mode tables in James, *Appl. Phys. B* 66, 181 (1998)
