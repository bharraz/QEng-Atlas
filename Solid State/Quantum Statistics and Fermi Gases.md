#solid-state #quantum

**Identical particles cannot be labelled, so a many-particle state says only how many particles occupy each single-particle state; fermions allow at most one per state and bosons any number, and in thermal equilibrium this gives the Fermi–Dirac and Bose–Einstein occupations.** The difference matters once particles are dense or cold enough that their thermal wavelength reaches the spacing between them. Then fermions fill a "Fermi sea" up to a sharp energy and bosons pile into the lowest state. Electrons in metals, neutron stars, and ultracold atomic gases are all in this degenerate regime.

# Reference

**Occupation of a single-particle state** of energy $\varepsilon$ in equilibrium:

$$
\bar n(\varepsilon) = \frac{1}{e^{(\varepsilon - \mu)/k_BT} \pm 1}
$$

- $\bar n$ — mean number of particles in the state
- $+$ — fermions (Fermi–Dirac): $\bar n \le 1$
- $-$ — bosons (Bose–Einstein): $\bar n$ unbounded as $\varepsilon \to \mu$
- $\mu$ — chemical potential (J): fixed by the total particle number
- $T$ — temperature (K)

When $e^{(\varepsilon-\mu)/k_BT} \gg 1$ for every state, both reduce to the classical Maxwell–Boltzmann form $e^{-(\varepsilon-\mu)/k_BT}$. Photons and phonons, whose number is not conserved, have $\mu = 0$: the Planck and Debye distributions ([[Thermal States]], [[Phonons]]).

**When quantum statistics matter:**

$$
n\,\lambda_\text{dB}^3 \gtrsim 1, \qquad \lambda_\text{dB} = \frac{h}{\sqrt{2\pi m k_B T}}
$$

- $n$ — number density (m⁻³)
- $\lambda_\text{dB}$ — thermal de Broglie wavelength (m)

In this phase-space density regime the particles' wavepackets overlap. Electrons in a metal are deep in it at room temperature, because of their small mass and high density; atomic gases reach it only at nanokelvin to microkelvin temperatures.

**Picture:** fermions fill states like guests in a hotel with one guest per room, so the last guest ends up on a high floor even at zero temperature; bosons crowd into the lobby.

**The Fermi gas.** At zero temperature, $N$ fermions fill every state up to the Fermi energy:

$$
E_F = \frac{\hbar^2}{2m}\left(3\pi^2 n\right)^{2/3}, \qquad T_F = \frac{E_F}{k_B}
$$

- $E_F$ — Fermi energy (J): highest occupied energy, spin-$\tfrac12$ particles in 3D
- $T_F$ — Fermi temperature (K)

For copper $E_F \approx 7$ eV, $T_F \approx 8\times10^4$ K, so room temperature is "cold" for its electrons. For a trapped ultracold fermionic gas, $T_F$ is of order a microkelvin.

**Consequences of a degenerate Fermi sea.** Only particles within about $k_BT$ of $E_F$ can change state, because every lower state is already full. That single fact explains several properties:

| Property | Classical expectation | Degenerate Fermi gas |
|---|---|---|
| electronic heat capacity | $\tfrac32 Nk_B$ | $\propto N k_B\,T/T_F$: linear in $T$ and small |
| magnetic susceptibility | Curie law, $\propto 1/T$ | Pauli paramagnetism: nearly temperature-independent |
| pressure at $T = 0$ | zero | degeneracy pressure $\propto n^{5/3}$: holds up white dwarfs and neutron stars |
| scattering into occupied states | unrestricted | Pauli blocking: suppressed when final states are full |
| transport | all particles carry current | only the states near the Fermi surface matter ([[Electronic Transport]]) |

**Density of states.** How many single-particle states lie near a given energy depends on dimension, for particles with no potential:

| Dimension | $g(\varepsilon)$ | Example |
|---|---|---|
| 3D | $\propto \sqrt{\varepsilon}$ | bulk metals, 3D atomic gases |
| 2D | constant | quantum wells, 2D electron gases ([[Semiconductors and Junctions]]) |
| 1D | $\propto 1/\sqrt{\varepsilon}$ | nanowires; divergences at band edges |

In a crystal the density of states follows the band structure, and in a harmonic trap $g(\varepsilon) \propto \varepsilon^2$ in 3D ([[Bloch's Theorem and Band Structure]]).

**The Bose gas.** For bosons $\mu$ rises toward the lowest energy as the gas cools; once $n\lambda_\text{dB}^3 = 2.612$ in a uniform 3D gas it cannot rise further, and the extra particles go into the ground state: Bose–Einstein condensation ([[Bose-Einstein Condensation]]).

**Spin and statistics.** Particles with half-integer spin are fermions and those with integer spin are bosons. A composite particle is a boson if it contains an even number of fermions: $^{87}$Rb and $^{23}$Na atoms are bosons; $^{6}$Li and $^{40}$K atoms are fermions. Two fermions bound into a pair behave as a boson on scales larger than the pair, which is how fermions become superfluid ([[Superconductivity]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| electronic heat capacity linear in $T$ at low temperature | a degenerate Fermi gas; the slope gives the density of states at $E_F$ |
| momentum distribution of a released atomic gas | Gaussian for a classical gas, a rounded step for a degenerate Fermi gas, a narrow peak for a condensate |
| suppressed light scattering from a degenerate Fermi gas | Pauli blocking of final momentum states |
| photoemission spectra near $E_F$ | the Fermi edge, broadened by temperature to a width of a few $k_BT$ |

> [!question]- Why do metal electrons contribute almost nothing to the heat capacity at room temperature, even though there is about one free electron per atom?
> Heating by $k_BT$ can only move an electron into an empty state, and below the Fermi energy every state is full. Only the fraction of electrons within about $k_BT$ of $E_F$, roughly $T/T_F \sim 0.4\%$ at room temperature for copper, can absorb energy, so the electronic heat capacity is smaller than the classical $\tfrac32 Nk_B$ by that factor. Lattice vibrations dominate until very low temperatures, where the electrons' linear-in-$T$ term overtakes the phonons' $T^3$.

# Connections

- [[Thermal States]] — the thermal density matrix these occupations come from
- [[Bose-Einstein Condensation]] — the bosonic limit of the same statistics
- [[Electronic Transport]] — conduction by electrons near the Fermi surface
- [[Bloch's Theorem and Band Structure]] — the density of states in a crystal
- [[Semiconductors and Junctions]] — the Fermi level and carrier statistics in semiconductors
- [[Phonons]] — bosons with $\mu = 0$, and the lattice heat capacity
- [[Superconductivity]] — fermions paired into bosons
- [[Hubbard Models and Mott Insulators]] — fermions and bosons on a lattice with interactions
- [[Second Quantization (Atlas)]] — occupation-number states and the operators that change them

---
Source: N. W. Ashcroft & N. D. Mermin, *Solid State Physics*, Ch. 2; F. Reif, *Fundamentals of Statistical and Thermal Physics*, Ch. 9; W. Ketterle & M. W. Zwierlein, "Making, probing and understanding ultracold Fermi gases," *Riv. Nuovo Cimento* 31, 247 (2008)
