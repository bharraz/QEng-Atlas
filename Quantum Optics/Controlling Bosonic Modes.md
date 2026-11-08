#quantum-optics #quantum-info

**A harmonic oscillator — a microwave cavity, the motion of a trapped ion, a mechanical resonator — has equally spaced levels, so a drive that adds one quantum adds the next equally easily, and on its own the mode can only be displaced or squeezed.** Coupling it to a qubit, or giving it a nonlinearity, is what lets each photon number be addressed separately and any state be prepared, including the code words of bosonic error correction.

# Reference

**Why the oscillator alone is not enough.** Displacements, squeezing, and beam splitters between modes take Gaussian states to Gaussian states, and such evolution is efficiently simulable ([[Symplectic Group]]). Universal control needs a non-Gaussian element: a qubit coupled dispersively or through sidebands, or a Kerr nonlinearity.

**Control methods:**

| Method | Interaction | Operation | Platforms |
|---|---|---|---|
| displacement | resonant drive on the mode | $D(\alpha)$ ([[Displacement Operator]]) | all |
| squeezing | parametric drive at twice the mode frequency | $S(r)$ ([[Squeezed States]]) | all |
| SNAP (selective number-dependent arbitrary phase) | qubit pulses that act only at one photon number, possible when the dispersive shift exceeds the linewidths | $\sum_n e^{i\theta_n}\lvert n\rangle\langle n\rvert$; with displacements, universal | circuit QED ([[Circuit QED]]) |
| echoed conditional displacement (ECD) | dispersive shift plus large displacements and a qubit echo | a displacement whose sign depends on the qubit; with qubit rotations, universal | circuit QED; spin-dependent kicks for ions |
| sideband (Law–Eberly) control | red- and blue-sideband pulses move one excitation at a time between qubit and mode | builds any finite superposition of Fock states, one rung at a time ([[Sideband Transitions]]) | ions, circuit QED with parametric sidebands, optomechanics |
| spin-dependent force | a force whose sign depends on the qubit | entangles qubit with motion; cat and GKP preparation | ions ([[Molmer-Sorensen Gate]]) |
| beam splitter between modes | parametric coupling at the frequency difference | exchanges excitations between two modes | circuit QED with a driven coupler, ions (coupled motional modes), photonics |
| two-photon drive with Kerr or two-photon loss | engineered nonlinearity | confines the mode to a pair of coherent states | Kerr-cat and dissipative-cat qubits ([[Bosonic Codes]]) |

**Measuring photon-number parity.** With a dispersive coupling, a qubit's phase advances at $\chi$ per photon. A Ramsey sequence on the qubit with waiting time $t$ gives phase

$$
\varphi = \chi\, t\, n, \qquad W(\alpha) = \frac{2}{\pi}\left\langle D(\alpha)\,\Pi\, D^\dagger(\alpha)\right\rangle
$$

- $\chi$ — dispersive shift per photon (rad/s): $\chi_{qr}$ on [[Circuit QED]]
- $t$ — qubit waiting time between the two π/2 pulses (s)
- $n$ — photon number in the mode
- $\Pi = e^{i\pi a^\dagger a}$ — photon-number parity
- $W(\alpha)$ — the [[Wigner Function]] at phase-space point $\alpha$

At $t = \pi/\chi$ even and odd photon numbers leave the qubit in opposite states, so one qubit measurement reads the parity. Displacing the mode by $\alpha$ before measuring parity gives the Wigner function at $\alpha$ — direct Wigner tomography.

**Picture:** a qubit beside an oscillator is a gearbox — the oscillator alone turns only in uniform steps, but through the qubit each photon number can be turned separately.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| displaced parity at many points | the full Wigner function, and negativity as a certificate of non-classicality |
| photon-number-resolved qubit spectroscopy | the photon-number distribution |
| conditional displacements of varying size | the characteristic function, another complete description of the state |
| decay of a prepared Fock state | the mode's energy relaxation time |
| rotation rate of a coherent state against its amplitude | self-Kerr of the mode |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| ancilla errors during control | qubit decay or dephasing while it is entangled with the mode | random phase kicks or displacements of the mode |
| self-Kerr distortion | photon-number-dependent frequency shears large states | displaced states smeared into crescents |
| speed limit from $\chi$ | number-selective pulses must be longer than $1/\chi$ | slow operations, exposed to decay |
| thermal population | residual excitation in the mode or the qubit | mixed initial states, lower fidelity |

> [!question]- Why can't displacements and squeezing alone prepare a cat state or a GKP state?
> They map Gaussian states to Gaussian states, whose Wigner functions are positive. Cat and GKP states have negative regions in their Wigner functions, so preparing them needs a non-Gaussian ingredient: a qubit-conditioned operation, a Kerr nonlinearity, or a photon-number measurement.

# Connections

- [[Bosonic Codes]] — the code words this control prepares and protects
- [[Circuit QED]] — dispersive shifts, Kerr terms, and photon-number splitting
- [[Wigner Function]] — what displaced-parity measurements reconstruct
- [[Displacement Operator]] — the Gaussian building block
- [[Squeezed States]] — the other Gaussian operation
- [[Fock States]] — the number states selective control addresses
- [[Sideband Transitions]] — sideband control of motion in ions
- [[Molmer-Sorensen Gate]] — spin-dependent forces on motional modes
- [[Symplectic Group]] — why Gaussian operations are not universal
- [[Cavity Optomechanics]] — the same control on mechanical modes

---
Source: S. Krastanov et al., "Universal control of an oscillator with dispersive coupling to a qubit," *Phys. Rev. A* 92, 040303 (2015); A. Eickbusch et al., "Fast universal control of an oscillator with weak dispersive coupling to a qubit," *Nature Phys.* 18, 1464 (2022); C. K. Law & J. H. Eberly, *Phys. Rev. Lett.* 76, 1055 (1996)
