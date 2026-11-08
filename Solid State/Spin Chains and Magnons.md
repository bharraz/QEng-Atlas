#solid-state #quantum

**A chain of coupled spins — the Heisenberg model and its anisotropic relatives, XXZ, XY, and Ising — is the standard laboratory of many-body physics: two transformations turn it into free particles, its low-energy excitations are magnons, and it is exactly the Hamiltonian trapped-ion and Rydberg arrays natively produce.**

The bulk magnetism this sits inside — exchange, Curie–Weiss, ordering — is [[Magnetism in Solids]].

# Reference

**The model family.** All are $\sum_{\langle ij\rangle}$ over neighbours, differing only in which components couple:

| Model | Coupling | Note |
|---|---|---|
| **Heisenberg** | $J\,\mathbf S_i\!\cdot\!\mathbf S_j$ | isotropic; continuous $SU(2)$ symmetry |
| **XXZ** | $J(S^x_iS^x_j + S^y_iS^y_j) + J_z S^z_iS^z_j$ | anisotropy $\Delta = J_z/J$ interpolates XY ↔ Heisenberg ↔ Ising |
| **XY** | $J(S^x_iS^x_j + S^y_iS^y_j)$ | free fermions after Jordan–Wigner |
| **Transverse-field Ising** | $J S^z_iS^z_j + h\sum_i S^x_i$ | the canonical quantum phase transition |

**Picture:** a line of small compass needles coupled to their neighbours: tipping one sends a spin wave (a magnon) along the chain.

$J>0$ or $<0$ sets ferromagnetic vs antiferromagnetic ordering, as in the bulk case.

## Two standard transformations

**Holstein–Primakoff: spins → bosons.** Expand about a fully ordered state, treating deviations as bosonic quanta:
$$S^z_i = S - a^\dagger_i a_i, \qquad S^+_i = \sqrt{2S - a^\dagger_ia_i}\;a_i \;\approx\; \sqrt{2S}\,a_i$$

The approximation is $\langle a^\dagger a\rangle \ll 2S$ — few excitations, i.e. low temperature. Keeping quadratic terms gives **free magnons**; the neglected quartic terms are magnon–magnon interactions. This is the same move as linearizing any oscillator problem, and the resulting algebra is the ladder-operator one ([[Ladder Operators]]).

**Jordan–Wigner: spin-1/2 → spinless fermions.** In 1D,
$$S^+_j = c^\dagger_j \exp\!\Big(i\pi\!\!\sum_{k<j} c^\dagger_kc_k\Big)$$

The exponential **string** enforces the right statistics — spins on different sites commute, fermions anticommute. Its use: the XY and transverse-field Ising chains become *quadratic* in fermions, hence **exactly solvable by diagonalizing a $2\times2$ Bogoliubov problem per momentum** ([[Symplectic Group]]). The Heisenberg chain does not become quadratic — the $S^zS^z$ term is a fermion interaction — which is why it needs Bethe ansatz instead.

## Magnons

The quantized spin waves, and the dispersion differs qualitatively between the two orderings:

| | Ferromagnet | Antiferromagnet |
|---|---|---|
| Dispersion | $\omega = 4JS(1-\cos ka) \approx 2JSa^2k^2$ — **quadratic** | $\omega \propto \lvert\sin ka\rvert \approx vk$ — **linear** |
| Ground state | the fully aligned state, exactly | *not* the Néel state — quantum fluctuations reduce the moment |
| Heat capacity (3D) | $\propto T^{3/2}$ | $\propto T^3$, like phonons |
| Magnetization | Bloch $T^{3/2}$ law, from counting thermal magnons | — |

Both are **Goldstone modes** of the broken spin-rotation symmetry, gapless at $k=0$; anisotropy or an applied field opens a gap and removes the low-$T$ power laws. The linear AFM dispersion is why an antiferromagnet's magnon thermodynamics mimics [[Phonons]] — same $\omega = vk$ counting, same $T^3$.

**Magnons are bosons with no conserved number**, exactly like phonons, so they carry zero chemical potential and their occupation is Bose–Einstein ([[Thermal States]]).

## What is special about one dimension

- **Mermin–Wagner:** continuous symmetry cannot break spontaneously at $T>0$ in 1D or 2D with short-range interactions. Chains have no true long-range order at finite temperature — only correlations with a finite length.
- **Exact solvability.** The Heisenberg chain is integrable by **Bethe ansatz**, one of the few interacting many-body models solved exactly.
- **Fractional excitations.** The spin-1/2 antiferromagnetic chain's excitations are **spinons** carrying $S = 1/2$, not magnons carrying $S=1$ — a single spin flip fractionalizes into two, and the observed spectrum is a two-spinon continuum rather than a sharp mode.
- **Haldane gap.** Integer-spin Heisenberg chains are gapped; half-integer-spin chains are gapless. The spin quantum number, not the coupling, decides — a genuinely topological distinction.
- **Quantum phase transition.** The transverse-field Ising chain orders at $h/J = 1$ **at zero temperature**, driven by quantum rather than thermal fluctuations; the gap closes at the critical point.

## Where these Hamiltonians are realized directly

Quantum simulators do not approximate these models — they *are* them:

| Platform | Realizes |
|---|---|
| **Trapped ions** | $H = \sum_{ij} J_{ij}\sigma^x_i\sigma^x_j + B\sum_i\sigma^z_i$ with tunable $J_{ij}\sim 1/r^\alpha$ — a long-range transverse-field Ising chain, produced by the same spin-dependent force as the [[Molmer-Sorensen Gate]] |
| **Rydberg arrays** | blockade gives an Ising interaction with the geometry set by tweezer placement ([[Rydberg Atoms and Blockade]]) |
| **Superconducting** | tunable couplers give XY and Ising terms directly |
| **Neutral-atom lattices** | superexchange in a Mott insulator gives Heisenberg |

Two consequences worth carrying: the "spin chain" literature is directly readable as a description of your apparatus, and **quantum annealing runs on exactly the transverse-field Ising Hamiltonian** ([[Adiabatic Ramps and Shortcuts]]).

> [!question]- Why is the antiferromagnet's Néel state not its ground state, when the ferromagnet's aligned state is?
> The aligned state is an exact eigenstate: $S^z_iS^z_j$ is diagonal on it and the flip-flop terms annihilate it. The Néel state is not — $S^+_iS^-_j$ acting on antialigned neighbours produces a different configuration, so quantum fluctuations mix in other states and reduce the sublattice moment below its classical value. In 1D spin-1/2 they destroy long-range order entirely.

# Connections

- [[Magnetism in Solids]] — exchange, ordering, and the bulk thermodynamics this refines
- [[Phonons]] — the same bosonic-quantum machinery; AFM magnons share the linear dispersion and $T^3$
- [[Ladder Operators]] — what Holstein–Primakoff maps the spins onto
- [[Symplectic Group]] — the Bogoliubov diagonalization after Jordan–Wigner
- [[Molmer-Sorensen Gate]] — the spin-dependent force that makes an ion chain an Ising chain
- [[Rydberg Atoms and Blockade]] — blockade as an Ising interaction on a programmable geometry
- [[Adiabatic Ramps and Shortcuts]] — annealing on the transverse-field Ising model
- [[Tensor Networks and MPS]] — how these chains are simulated classically
- [[Angular Momentum in QM]] — the spin algebra underneath
- [[Symmetry in Quantum Mechanics]] — Goldstone modes from broken spin-rotation symmetry
- [[Exchange Interactions]] — where the couplings $J$ come from, and the sign conventions in use
- [[Out-of-Time-Order Correlators (OTOC)]] — how information spreads through these chains (scrambling)
- [[Quench Dynamics and Thermalization]] — what happens when these Hamiltonians are switched on suddenly
- [[Analog Quantum Simulation]] — the experiments that realize these models
- [[Topological Phases of Matter]] — the Haldane chain as a symmetry-protected topological phase
- [[Hubbard Models and Mott Insulators]] — the electron model these spin chains come from
- [[Phase Transitions and Critical Phenomena]] — quantum phase transitions in spin chains
- [[Variational Quantum Algorithms]] — Ising cost and transverse-field mixer in QAOA

---
Source: Auerbach, *Interacting Electrons and Quantum Magnetism*, Ch. 2–7; Sachdev, *Quantum Phase Transitions*, Ch. 1–5
