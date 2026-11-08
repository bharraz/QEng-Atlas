#solid-state

**Cool a gas of identical bosons until each particle's thermal de Broglie wavelength reaches the spacing between particles, and a macroscopic fraction of them falls into the single lowest-energy state, forming one coherent matter wave with a definite phase.** The same physics, a macroscopically occupied state with phase coherence, underlies superfluid helium, superconductors through paired electrons, and the dilute atomic condensates of AMO labs, which makes condensation the bridge between AMO and solid state.

You should read Murray Holland’s work

# Reference

**The onset.** Bosons have no exclusion principle, so nothing stops many of them occupying one state. In a uniform 3D gas, the chemical potential reaches the lowest energy when

$$
n\,\lambda_{\mathrm{dB}}^3 = 2.612, \qquad \lambda_{\mathrm{dB}} = \frac{h}{\sqrt{2\pi m k_B T}}
$$

- $n$ — number density (m⁻³)
- $\lambda_\text{dB}$ — thermal de Broglie wavelength (m)
- $2.612$ — $\zeta(3/2)$, the Riemann zeta value for a 3D box

and every additional particle goes into the ground state ([[Quantum Statistics and Fermi Gases]]). In a harmonic trap, the more common experimental case:

$$
k_BT_c \approx 0.94\,\hbar\bar\omega\,N^{1/3}, \qquad \frac{N_0}{N} = 1 - \left(\frac{T}{T_c}\right)^3
$$

- $\bar\omega$ — geometric mean of the three trap frequencies (rad/s)
- $N$ — total number of atoms
- $N_0$ — number in the condensate, for an ideal gas

**Picture:** a crowd of people each humming at random settles into one choir singing the same note in phase — the many become a single wave.

**The order parameter.** The condensate is described by one complex field, $\psi = \sqrt{n}\,e^{i\varphi}$: one wavefunction for the entire population, carrying a definite macroscopic phase. The general definition, which also covers interacting and strongly depleted systems, is off-diagonal long-range order: the one-body density matrix $\langle\hat\psi^\dagger(\mathbf r)\hat\psi(\mathbf r')\rangle$ stays finite as $|\mathbf r - \mathbf r'| \to \infty$ (Penrose–Onsager) ([[Coherent States]], [[Second Quantization (Atlas)]]).

**Interactions: the Gross–Pitaevskii equation.** For a dilute gas with s-wave scattering length $a$:

$$
i\hbar\,\partial_t\psi = \left(-\frac{\hbar^2\nabla^2}{2m} + V(\mathbf r) + g\,|\psi|^2\right)\psi, \qquad g = \frac{4\pi\hbar^2 a}{m}
$$

- $\psi$ — condensate wavefunction, normalized to the atom number
- $V(\mathbf r)$ — trapping potential (J)
- $g$ — contact interaction strength (J·m³)
- $a$ — s-wave scattering length (m): positive for repulsion

Two length scales follow:
- **Thomas–Fermi shape.** When interactions dominate kinetic energy, the density takes the inverted shape of the trap, $n(\mathbf r) = [\mu - V(\mathbf r)]/g$.
- **Healing length.** $\xi = 1/\sqrt{8\pi n a}$ is the distance over which the condensate recovers from a disturbance, and the core size of a vortex.

**Excitations and superfluidity.** Small excitations of a uniform condensate follow the Bogoliubov dispersion:

$$
E(k) = \sqrt{\epsilon_k\left(\epsilon_k + 2gn\right)}, \qquad \epsilon_k = \frac{\hbar^2k^2}{2m}, \qquad c = \sqrt{\frac{gn}{m}}
$$

- $E(k)$ — excitation energy at wavevector $k$ (J)
- $c$ — speed of sound (m/s): the slope of $E(k)$ at small $k$

Phonon-like at small $k$, particle-like at large $k$. An obstacle moving slower than $c$ cannot create excitations (Landau's criterion), so the flow is frictionless. This is a subtle point: an *ideal* Bose gas condenses but is not superfluid, since its dispersion $\epsilon_k$ has zero critical velocity; interactions are what make a condensate superfluid. Circulation around any loop is quantized in units of $h/m$, so rotation enters as discrete vortices ([[Topology and Topological Invariants]]).

**Condensates compared:**

| System | What condenses | Interactions | Temperature scale |
|---|---|---|---|
| dilute alkali gases | atoms (bosonic isotopes) | weak, tunable by Feshbach resonances | 10 nK – 1 µK |
| superfluid $^4$He | He atoms | strong; condensate fraction only about 10% | 2.17 K |
| superconductors | Cooper pairs of electrons | pairing mediated by phonons or other mechanisms | mK to above 100 K ([[Superconductivity]]) |
| exciton-polaritons, magnons | quasiparticles | driven–dissipative | up to room temperature |
| fermionic atomic gases | pairs, from BCS to tightly bound molecules | tuned across the BEC–BCS crossover by Feshbach resonances | 10–100 nK |

Fermions must first pair into bosons before they can condense ([[Hubbard Models and Mott Insulators]]).

**Making an atomic condensate.** Laser cooling and a magneto-optical trap bring atoms to tens of microkelvin ([[Doppler Cooling]], [[Magneto-Optical Traps]]). Atoms are then transferred to a magnetic or optical trap, where evaporative cooling removes the most energetic atoms and lets the rest rethermalize, gaining orders of magnitude in phase-space density at the cost of most of the atoms. In two dimensions the transition is of the Berezinskii–Kosterlitz–Thouless type rather than true condensation ([[Phase Transitions and Critical Phenomena]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| time-of-flight image: a narrow peak on a broad thermal cloud (bimodal) | condensation, and the condensate fraction |
| aspect ratio inverting during expansion | a condensate: a thermal cloud expands isotropically, while a condensate expands fastest along its tightest trap axis |
| interference fringes between two released condensates | phase coherence |
| vortex lattice in a rotated cloud | superfluidity and quantized circulation |
| Bragg spectroscopy of the excitation spectrum | the Bogoliubov dispersion and the speed of sound |

> [!question]- What distinguishes a BEC from a cold gas in which most atoms sit in the ground state?
> Coherence and a single macroscopic phase. The condensate is one wavefunction, not a population statistic, so two independent condensates released and overlapped show interference fringes. Phase coherence — off-diagonal long-range order — not low energy or high ground-state occupation alone, is what makes it a distinct state of matter.

# Connections

- [[Thermal States]] — Bose–Einstein statistics and the occupation that condenses
- [[Quantum Statistics and Fermi Gases]] — bosons and fermions compared, and the onset condition
- [[Coherent States]] — the order parameter behaves like a classical coherent field with a definite phase
- [[Superconductivity]] — Cooper-pair condensation, the charged and paired counterpart
- [[Second Quantization (Atlas)]] — the bosonic field whose ground mode becomes macroscopically occupied
- [[Doppler Cooling]] — the first stage of the cooling chain that reaches condensation
- [[Phase Transitions and Critical Phenomena]] — condensation as a phase transition with a phase as its order parameter
- [[Hubbard Models and Mott Insulators]] — condensates in optical lattices and the superfluid–Mott transition

---
Source: Pethick & Smith, *Bose–Einstein Condensation in Dilute Gases*, Ch. 1–2; Pitaevskii & Stringari, *Bose–Einstein Condensation*; F. Dalfovo, S. Giorgini, L. P. Pitaevskii & S. Stringari, *Rev. Mod. Phys.* 71, 463 (1999)
