#solid-state #quantum

**Two electrons repel by Coulomb's law however their spins point, yet their energy depends on the spins: Pauli exclusion ties the spin state to the symmetry of the spatial wavefunction (singlet ↔ symmetric, triplet ↔ antisymmetric), and the two spatial shapes keep the electrons apart by different amounts, so a spin-independent force produces an effective spin–spin coupling $J\,\mathbf S_1\cdot\mathbf S_2$.** That coupling, and engineered look-alikes in atoms, ions, and circuits, is how magnets order and how many qubits are entangled.

# Reference

$$
H_\text{ex} = J\,\mathbf S_1\cdot\mathbf S_2, \qquad E_\text{triplet} - E_\text{singlet} = J
$$

- $J$ — exchange energy (J, or $J/h$ in Hz): the singlet–triplet splitting
- $\mathbf S_1, \mathbf S_2$ — spin operators (units of $\hbar$): $\mathbf S_1\cdot\mathbf S_2 = -\tfrac34$ singlet, $+\tfrac14$ triplet

In this convention $J > 0$ puts the singlet lowest (antiparallel, antiferromagnetic) and $J < 0$ the triplet (parallel, ferromagnetic).

**Picture:** exchange is Coulomb and kinetic energy with spin as a label. The triplet's antisymmetric spatial wavefunction vanishes when the electrons coincide, so it keeps them apart and pays less Coulomb repulsion; the singlet's symmetric one lets them share a site, so they can delocalize and pay less kinetic energy. Whichever saving is larger decides the sign of $J$, and the spin state follows.

**Sign conventions disagree — check before comparing:**

| Written as | Ferromagnetic when | Singlet–triplet splitting | Used on |
|---|---|---|---|
| $+J\,\mathbf S_1\cdot\mathbf S_2$ | $J < 0$ | $J$ | the formula above, [[Spin Chains and Magnons]], [[Quantum Dots]] |
| $-J\,\mathbf S_1\cdot\mathbf S_2$ | $J > 0$ | $J$ | [[Magnetism in Solids]] |
| $-2J\,\mathbf S_1\cdot\mathbf S_2$ | $J > 0$ | $2J$ | older magnetism texts |

On a lattice, also check whether $\sum_{ij}$ counts each pair once or twice ([[Conventions and Factor-of-Two Traps]]).

**Where $J$ comes from:**

| Mechanism | Route | Sign | Scale | Where |
|---|---|---|---|---|
| **Direct (potential) exchange** | overlapping orbitals: the triplet's spatial antisymmetry lowers the Coulomb energy | ferromagnetic | grows with orbital overlap | Hund's first rule within an atom; some metals |
| **Kinetic exchange** (superexchange when it runs through an intermediate ion) | virtual hopping onto a neighbour's site, which Pauli allows only for the singlet | antiferromagnetic | $J = 4t^2/U$ ($t$ hopping, $U$ on-site repulsion) — second-order perturbation theory | Mott insulators, double quantum dots, atoms in optical lattices |
| **RKKY** | local moments polarize the conduction electrons, which carry the polarization to other moments | oscillates with distance, period $\sim \pi/k_F$, decaying as $1/r^3$ in 3D | | magnetic impurities in metals |
| **Double exchange** | an itinerant electron hops more easily between parallel core spins | ferromagnetic | | mixed-valence oxides (manganites) |
| **Dzyaloshinskii–Moriya** | spin–orbit coupling in a lattice without inversion symmetry; $\mathbf D\cdot(\mathbf S_1\times\mathbf S_2)$ | favours canted spins | small fraction of $J$ | weak ferromagnets, skyrmions |

**As a two-qubit gate:** $\mathbf S_1\cdot\mathbf S_2 = \tfrac12\,\mathrm{SWAP} - \tfrac14$, so letting exchange act for a time $t$ is, up to a global phase, a power of SWAP: $Jt/\hbar = \pi$ swaps the two spins and $Jt/\hbar = \pi/2$ gives $\sqrt{\mathrm{SWAP}}$, which is [[Entangling Gates|entangling]]. Pulsing $J$ on and off is the native two-qubit gate of spin qubits.

**Anisotropic versions:** dropping some components gives the XXZ, XY ("flip-flop"), and Ising models of [[Spin Chains and Magnons]]. The flip-flop form $J(S_1^xS_2^x + S_1^yS_2^y) = \tfrac{J}{2}(S_1^+S_2^- + S_1^-S_2^+)$ moves one excitation between the spins without changing the total $S^z$.

**Engineered spin–spin couplings in quantum platforms:**

| Platform | Form | Origin |
|---|---|---|
| gate-defined [[Quantum Dots]] | Heisenberg $J\,\mathbf S_1\cdot\mathbf S_2$, $J = 4t_c^2/U$ | kinetic exchange, tuned by the barrier gate between the dots |
| atoms in an optical lattice | Heisenberg, $J = 4t^2/U$ | superexchange in a Mott insulator |
| [[Rydberg Atoms and Blockade\|Rydberg]] pair $nS$–$nP$ | flip-flop (XY), $\propto C_3/r^3$ | resonant dipole–dipole exchange of the excitation |
| Rydberg pair $nS$–$nS$ | Ising ($n_i n_j$), $C_6/r^6$ | van der Waals energy shift — no excitation is exchanged |
| [[Superconducting Qubits\|transmons]] via a bus resonator or tunable coupler | flip-flop, $J \approx g_1g_2/\Delta$ | virtual photon exchange through the bus |
| trapped ions | Ising $J_{ij}\,\sigma_i^x\sigma_j^x$, range tunable roughly as $1/r^\alpha$ with $0 < \alpha < 3$ | virtual phonons from a spin-dependent force: each [[Normal Modes of Ion Chains\|normal mode]] contributes in proportion to the two ions' participations, weighted by how close the drive is to that mode ([[Molmer-Sorensen Gate]]) |

> [!question]- Two transmons coupled through a bus show a flip-flop interaction with no $\sigma_z\sigma_z$ term at leading order, while two electron spins in a double dot show the full Heisenberg $\mathbf S_1\cdot\mathbf S_2$. Why the difference?
> The transmon coupling is virtual exchange of a photon: it moves an excitation from one qubit to the other and conserves the total number, so it generates $\sigma^+\sigma^- + \text{h.c.}$ — the XY form. The dot coupling comes from Pauli exclusion acting on identical electrons, which depends only on the total spin symmetry, a rotational scalar, so it is isotropic. A $\sigma_z\sigma_z$ term does appear for transmons at higher order, through their third levels.

# Connections

- [[Magnetism in Solids]] — what exchange does in bulk: ordering, Curie–Weiss, magnons
- [[Spin Chains and Magnons]] — the Heisenberg, XXZ, and Ising models built from it
- [[Quantum Dots]] — exchange as the two-qubit gate of spin qubits
- [[Rydberg Atoms and Blockade]] — dipolar flip-flop vs van der Waals interactions
- [[Superconducting Qubits]] — bus- and coupler-mediated flip-flop couplings
- [[Molmer-Sorensen Gate]] — phonon-mediated Ising coupling between ions
- [[Time-Independent Perturbation Theory]] — $4t^2/U$ is a second-order energy shift
- [[Spin-1-2]] — the spin algebra behind $\mathbf S_1\cdot\mathbf S_2$
- [[Analog Quantum Simulation]] — superexchange in lattice simulations of the Hubbard model
- [[Two-Qubit Gate Mechanisms]] — the gates each of these couplings produces
- [[Effective Hamiltonians and Adiabatic Elimination]] — superexchange as a second-order virtual process
- [[Hubbard Models and Mott Insulators]] — the model whose large-$U$ limit gives superexchange

---
Source: Ashcroft & Mermin, *Solid State Physics*, Ch. 32; Blundell, *Magnetism in Condensed Matter*, Ch. 4; Hanson et al., "Spins in few-electron quantum dots," *Rev. Mod. Phys.* 79, 1217 (2007)
