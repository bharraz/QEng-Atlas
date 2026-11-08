#solid-state #quantum

**Put particles on a lattice where they can hop to neighbouring sites with amplitude $t$ and pay an energy $U$ whenever two share a site: when hopping dominates they spread into delocalized waves and conduct, and when the on-site cost dominates they lock one per site and stop moving, even though the band picture says they should conduct.** That interaction-driven insulator is a Mott insulator. The Hubbard model, with only these two terms, is the minimal model of strongly correlated electrons and the main target of quantum simulators built from atoms in optical lattices, quantum-dot arrays, and superconducting circuits.

# Reference

**The Fermi–Hubbard model**, spin-$\tfrac12$ fermions:

$$
H = -t\sum_{\langle ij\rangle,\sigma}\left(c^\dagger_{i\sigma}c_{j\sigma} + \text{h.c.}\right) + U\sum_i n_{i\uparrow}n_{i\downarrow} - \mu\sum_{i}n_i
$$

- $t$ — hopping amplitude between neighbouring sites (J): sets the bandwidth
- $U$ — on-site interaction (J): energy cost of a doubly occupied site
- $c^\dagger_{i\sigma}$ — creates a fermion with spin $\sigma$ on site $i$
- $n_{i\sigma}$ — number of spin-$\sigma$ fermions on site $i$
- $\mu$ — chemical potential (J): sets the filling
- $\langle ij\rangle$ — sum over neighbouring pairs

**The Bose–Hubbard model**, bosons:

$$
H = -J\sum_{\langle ij\rangle}\left(b^\dagger_i b_j + \text{h.c.}\right) + \frac{U}{2}\sum_i n_i(n_i - 1) - \mu\sum_i n_i
$$

- $J$ — hopping amplitude (J), written $J$ by convention for bosons
- $b^\dagger_i$ — creates a boson on site $i$
- $n_i$ — number of bosons on site $i$

**Picture:** a row of seats with a fee for sharing — when the fee is small people wander freely between seats, and when it is large each sits alone in one seat and nobody can move without paying it.

**The two limits.** With $U = 0$ the model is a tight-binding band: in 1D, $E(k) = -2t\cos ka$, bandwidth $4t$; on a 3D cubic lattice the bandwidth is $12t$ ([[Bloch's Theorem and Band Structure]]). With $t = 0$ every site is independent and the ground state has a fixed integer occupation. The physics lies in between, where neither is small.

| | Bose–Hubbard | Fermi–Hubbard |
|---|---|---|
| small $U$ | superfluid: phase coherence across the lattice | metal (a Fermi liquid), away from special fillings |
| large $U$, integer filling | Mott insulator: fixed number per site, a gap of about $U$ | Mott insulator at half filling (one fermion per site) |
| transition | superfluid–Mott, at $U/J \approx 29$ for one boson per site on a 3D cubic lattice ($\approx 5.8\,z$ in mean-field theory, $z$ neighbours) | metal–insulator; at half filling in 1D, and on the 2D square lattice at zero temperature, any $U > 0$ gives an insulator |
| spin physics at large $U$ | none (spinless) | antiferromagnetic Heisenberg coupling $J_\text{ex} = 4t^2/U$ ([[Exchange Interactions]]) |
| doped away from half filling | — | strange metals, stripes, and possibly $d$-wave superconductivity: an open problem tied to the cuprates |

The spin coupling at large $U$ is superexchange: two neighbouring opposite spins lower their energy by virtually hopping onto one site and back, which Pauli exclusion forbids for parallel spins ([[Effective Hamiltonians and Adiabatic Elimination]]).

**Realizations:**

| Platform | Hopping $t$ or $J$ | Interaction $U$ | What it adds |
|---|---|---|---|
| atoms in optical lattices | tunnelling, tuned by lattice depth | collisions, tuned by Feshbach resonances | quantum-gas microscopes image single sites ([[Analog Quantum Simulation]]) |
| semiconductor quantum-dot arrays | interdot tunnel coupling, tuned by gate voltages | charging energy | small Fermi–Hubbard systems with electrical control ([[Quantum Dots]]) |
| superconducting qubit arrays | capacitive coupling | transmon anharmonicity, which is attractive ($U < 0$) | Bose–Hubbard dynamics with photons ([[Superconducting Qubits]]) |
| correlated materials | orbital overlap | Coulomb repulsion on one atom | the original motivation: transition-metal oxides, cuprates |

**Feshbach resonances** tune $U$ in atomic gases. A magnetic field brings a bound molecular state into resonance with the colliding atoms, changing the scattering length as

$$
a(B) = a_\text{bg}\left(1 - \frac{\Delta}{B - B_0}\right)
$$

- $a_\text{bg}$ — background scattering length (m)
- $B_0$ — resonance position (T)
- $\Delta$ — resonance width (T)

and $U \propto a$, so the interaction can be made repulsive, attractive, or zero.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| interference peaks after release from the lattice | superfluid phase coherence; the peaks vanish in the Mott insulator |
| site-resolved images in a quantum-gas microscope | occupation per site (usually its parity, since pairs are lost during imaging) and spin correlations |
| response to modulating the lattice depth | an absorption peak near $U$: the Mott gap |
| fraction of doubly occupied sites | how strongly double occupancy is suppressed by $U$ |
| nearest-neighbour spin correlations | antiferromagnetic order of strength set by $4t^2/U$ and temperature |

> [!question]- A band insulator and a Mott insulator both fail to conduct. What distinguishes them?
> A band insulator has an even number of electrons per unit cell, so its bands are completely filled or empty, and it would insulate even without interactions. A Mott insulator has a half-filled band, which non-interacting electrons would conduct through. It insulates only because hopping would create a doubly occupied site costing $U$, so its gap is of order $U - (\text{bandwidth})$, and it carries localized spins that order antiferromagnetically through superexchange. Changing $U/t$ can melt a Mott insulator; it cannot make a filled band conduct.

# Connections

- [[Bloch's Theorem and Band Structure]] — the tight-binding band at $U = 0$
- [[Exchange Interactions]] — superexchange and the Heisenberg model at large $U$
- [[Effective Hamiltonians and Adiabatic Elimination]] — how $4t^2/U$ arises
- [[Analog Quantum Simulation]] — lattice experiments that realize these models
- [[Quantum Dots]] — electrically controlled Hubbard systems
- [[Spin Chains and Magnons]] — the spin models these reduce to
- [[Phase Transitions and Critical Phenomena]] — the superfluid–Mott transition as a quantum phase transition
- [[Quantum Statistics and Fermi Gases]] — the statistics of the particles being placed on the lattice
- [[Bose-Einstein Condensation]] — the superfluid side, without a lattice

---
Source: I. Bloch, J. Dalibard & W. Zwerger, "Many-body physics with ultracold gases," *Rev. Mod. Phys.* 80, 885 (2008); M. P. A. Fisher, P. B. Weichman, G. Grinstein & D. S. Fisher, *Phys. Rev. B* 40, 546 (1989); D. P. Arovas, E. Berg, S. A. Kivelson & S. Raghu, "The Hubbard model," *Annu. Rev. Condens. Matter Phys.* 13, 239 (2022)
