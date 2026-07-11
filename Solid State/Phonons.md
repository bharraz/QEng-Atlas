#solid-state

**A phonon is a quantum of lattice vibration — the normal modes of the atoms in a crystal are harmonic oscillators, and their excitations are bosonic quanta that carry heat, scatter electrons, and glue Cooper pairs together.** It is second quantization applied to a lattice, with the same ladder-operator algebra as photons.

# Reference

Atoms coupled by effective springs have normal modes with dispersion $\omega(\mathbf{k})$. Quantizing each mode as a [[Quantum Harmonic Oscillator]] gives excitations of energy $E = \hbar\omega$ and crystal momentum $\hbar\mathbf{k}$ — phonons, created and destroyed by [[Ladder Operators]] exactly as photons are. (Structurally identical to quantizing the normal modes of an ion chain — see [[Normal Modes of Ion Chains]] — except the modes number $\sim 10^{23}$ and form continuous branches.)

**The 1D chain — the solvable template.** Masses $M$, spring constant $K$, spacing $a$:

$$\omega(k) = 2\sqrt{\frac{K}{M}}\,\left|\sin\frac{ka}{2}\right|.$$

Linear near $k=0$ ($\omega \approx v_s k$ with sound speed $v_s = a\sqrt{K/M}$), flat at the zone boundary $k = \pi/a$ (group velocity zero — standing wave, Bragg condition). With **two alternating masses** the zone halves and the branch folds into two: an **acoustic** branch ($\omega \to 0$, cells move together) and an **optical** branch (finite $\omega$ at $k=0$, atoms within a cell beat against each other), separated by a gap at the zone edge.

**Branches in 3D:**
- **Acoustic** — 3 branches (one longitudinal, two transverse); these are sound.
- **Optical** — $3p - 3$ branches for $p$ atoms per cell; the $k\approx 0$ optical modes are what IR light and Raman scattering couple to (light's tiny $k$ pins you to the zone center).

**Occupation and thermodynamics.** Phonons are **bosons** with zero chemical potential (their number is not conserved); each mode holds

$$\bar{n}(\omega) = \frac{1}{e^{\hbar\omega/k_BT} - 1}$$

quanta (see [[Thermal States]]). The **Debye model** replaces the acoustic branches by $\omega = v_s k$ up to a cutoff $k_D$ chosen to get the mode count right, defining the **Debye temperature** $\Theta_D = \hbar v_s k_D / k_B$ (diamond: $2230$ K — stiff bonds, light atoms; lead: $105$ K). Heat capacity:

$$C \xrightarrow{T \ll \Theta_D} \frac{12\pi^4}{5} N k_B \left(\frac{T}{\Theta_D}\right)^3, \qquad C \xrightarrow{T \gg \Theta_D} 3Nk_B \;\; \text{(Dulong–Petit)}.$$

The $T^3$ is pure mode counting: the thermally accessible phonon sphere has radius $\propto T$, hence $\propto T^3$ modes, each carrying $\sim k_B$.

**Zero-point motion and the Debye–Waller factor.** Atoms are never at rest; the mean-square displacement $\langle u^2 \rangle$ (zero-point + thermal) multiplies every diffraction peak by $e^{-G^2\langle u^2\rangle/3}$ — the Debye–Waller factor — attenuating high-$\mathbf{G}$ peaks without broadening them. The same physics as the [[Lamb-Dicke Regime]] factor on sideband transitions: recoil taken up elastically by the whole lattice (Mössbauer) vs. phonon-creating events.

**Why they matter beyond heat:** electron–phonon scattering is a main source of electrical resistance, and the same electron–phonon coupling provides the attractive interaction that binds Cooper pairs in conventional [[Superconductivity]].

> [!question]- How is a phonon like a photon, and where does the analogy break?
> Both are bosonic quanta of a harmonic field with $E=\hbar\omega$ and the same $a,a^\dagger$ algebra. The differences: a phonon is an excitation of atomic displacement, so it needs a medium (no vacuum phonons); its dispersion is bounded by the Brillouin zone rather than running to infinity; and there is a finite number of branches fixed by the atoms per unit cell.

# Connections

- [[Quantum Harmonic Oscillator]] — each normal mode is one, exactly
- [[Ladder Operators]] — phonon creation/annihilation and the $\hbar\omega(n+\tfrac12)$ ladder
- [[Second Quantization]] — the field-quantization framing shared with photons
- [[Thermal States]] — Bose–Einstein occupation sets heat capacity and mode population
- [[Superconductivity]] — phonon exchange is the pairing glue in BCS
- [[Crystal Lattices and Reciprocal Space]] — modes are labeled by $\mathbf{k}$ in the Brillouin zone
- [[Normal Modes of Ion Chains]] — the same quantization on a finite chain; phonons are its $N \to \infty$ limit
- [[Lamb-Dicke Regime]] — Debye–Waller and Lamb-Dicke are the same recoil-suppression factor

---
Source: Ashcroft & Mermin, *Solid State Physics*, Ch. 22–23; Kittel, *Introduction to Solid State Physics*, Ch. 4–5
