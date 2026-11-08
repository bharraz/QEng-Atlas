#quantum-info #quantum

**Build a controllable system whose Hamiltonian matches a model too hard to solve — atoms hopping in an optical lattice for the Hubbard model, trapped ions pushed by spin-dependent forces for long-range Ising magnets, Rydberg atom arrays for constrained spin models — let it evolve, and measure it: the hardware computes the model's behaviour by being an instance of it.**

# Reference

**Analog, digital, and in between:**

| Approach | How the model is run | Strength | Weakness |
|---|---|---|---|
| analog | the native Hamiltonian evolves continuously | large systems, long evolution | errors are not corrected and hard to quantify |
| digital | gates approximate $e^{-iHt}$ ([[Trotterization (Atlas)]]) | any Hamiltonian; errors quantifiable | gate errors limit depth |
| digital–analog | native interactions interleaved with single-qubit gates | more Hamiltonians than analog, fewer gates than digital | inherits both error types |
| variational | a parametrized circuit is optimized against a cost ([[Variational Quantum Algorithms]]) | short circuits | optimization difficulty; no guarantee of accuracy |

**The Hubbard model** — the central target of lattice simulators:

$$
H = -t\sum_{\langle ij\rangle,\sigma}\left(c^\dagger_{i\sigma}c_{j\sigma} + \text{h.c.}\right) + U\sum_i n_{i\uparrow}n_{i\downarrow}
$$

- $t$ — tunnelling energy between neighbouring sites (J, quoted in Hz): set by lattice depth
- $U$ — interaction energy of two particles on one site (J, quoted in Hz)
- $c_{i\sigma}$ — removes a fermion of spin $\sigma$ from site $i$
- $n_{i\sigma}$ — number of spin-$\sigma$ fermions on site $i$

The ratio $U/t$ decides the physics: small $U/t$ gives a metal; at one particle per site and $U \gg t$ the particles stop moving (a Mott insulator) and their spins order antiferromagnetically through the superexchange $J = 4t^2/U$ ([[Exchange Interactions]]). The bosonic version (Bose–Hubbard) has a quantum phase transition from a superfluid to a Mott insulator as $U/t$ grows.

**Picture:** an analog simulator is a wind tunnel for quantum matter — the model is built instead of computed.

**Models and the hardware that runs them:**

| Model | Hamiltonian form | Realized with |
|---|---|---|
| Fermi–Hubbard | hopping $t$, on-site $U$ | fermionic atoms in optical lattices; quantum-dot arrays ([[Quantum Dots]]) |
| Bose–Hubbard | hopping, on-site repulsion | bosonic atoms in lattices; arrays of transmons, with microwave photons as the bosons |
| long-range Ising | $\sum_{ij} J_{ij}\sigma^x_i\sigma^x_j + B\sum_i\sigma^z_i$, $J_{ij}\propto 1/r^\alpha$ | trapped ions, through the force behind the [[Molmer-Sorensen Gate]] |
| Rydberg (blockade) model | $\tfrac\Omega2\sum_i\sigma^x_i - \Delta\sum_i n_i + \sum_{i<j}V_{ij}n_in_j$ | Rydberg tweezer arrays ([[Rydberg Atoms and Blockade]]) |
| XY / hard-core bosons | $J\sum(\sigma^+_i\sigma^-_j + \text{h.c.})$ | superconducting arrays, dipolar Rydberg pairs, ions |
| Heisenberg | $J\sum\mathbf S_i\cdot\mathbf S_j$ | superexchange in atomic Mott insulators |
| lattice gauge theories, synthetic magnetic fields | hopping with complex phases | laser-assisted tunnelling, periodic driving; encodings on ions and superconducting qubits |

**Engineering tools:**

| Tool | What it sets |
|---|---|
| optical lattice (standing waves of light, period $\lambda/2$) | the sites, and $t$ through the lattice depth ([[Stark Effect and Light Shifts]]) |
| magnetic Feshbach resonance | the interaction $U$, including its sign |
| tweezer arrays | arbitrary geometries, site by site ([[Optical Tweezers]]) |
| periodic driving (Floquet engineering) | effective Hamiltonians with modified or complex hopping ([[Magnus Expansion]]) |
| spin-dependent forces, tunable couplers | spin–spin couplings and their range |

**Preparing the state.** Ground states are reached by adiabatic ramps from an easy starting Hamiltonian, slowed where the gap closes ([[Adiabatic Ramps and Shortcuts]]); dynamics by quenches from product states ([[Quench Dynamics and Thermalization]]). Lattice gases are loaded from a cooled cloud, so their entropy per particle, fixed at loading, sets how cold the simulated system can be.

**Reading it out:**

| Measurement | What it gives | Platforms |
|---|---|---|
| site-resolved imaging (quantum gas microscope, tweezer imaging) | a snapshot of every site's occupation or spin, in one basis per run | lattices, tweezer arrays |
| correlation functions computed from snapshots | ordering and correlation length, $\langle \sigma_i\sigma_j\rangle - \langle\sigma_i\rangle\langle\sigma_j\rangle$ | all |
| string (non-local parity) correlators | order invisible to two-point correlators, as in Mott insulators and Haldane chains | lattices |
| full distribution of a quantity across snapshots | fluctuations and higher moments, not only means | all |
| randomized measurements | Rényi entropies and fidelities between devices ([[Benchmarking and Characterization]]) | ions, superconducting qubits, atoms |
| spectroscopy (modulation, Ramsey, quench spectroscopy) | gaps and excitation energies | all |
| time-of-flight images | momentum distribution: sharp peaks indicate phase coherence | lattice gases |

**Is the result right?** Analog errors are not corrected and accumulate with time. Results are checked against exact numerics for small sizes and tensor-network numerics for low entanglement ([[Exact Diagonalization and Sparse Methods]], [[Tensor Networks and MPS]]), against known limits, by running the evolution backwards (a Loschmidt echo) to measure accumulated error, and by comparing different platforms. Whether a simulator outperforms classical methods is decided in the regimes those numerics cannot reach — high entanglement, two dimensions, long times — which is where verification is also hardest.

> [!question]- In an optical-lattice simulation of the Hubbard model, why is entropy per particle, rather than coherence time, usually the limiting figure?
> The antiferromagnetic order of interest appears only at temperatures below the superexchange scale $J = 4t^2/U$, a small energy. The atoms are loaded from a cooled gas, and slow loading conserves entropy, so the achievable temperature in units of $J$ is set by the entropy per particle at loading. Coherence times are long compared with tunnelling times, so they rarely limit; reaching low enough entropy does.

# Connections

- [[Spin Chains and Magnons]] — the spin models and their solvable limits
- [[Quench Dynamics and Thermalization]] — what dynamical experiments look for
- [[Exchange Interactions]] — superexchange and engineered spin–spin couplings
- [[Rydberg Atoms and Blockade]] — the blockade model on tweezer arrays
- [[Optical Tweezers]] — site-by-site geometries and imaging
- [[Molmer-Sorensen Gate]] — the spin-dependent force behind ion Ising models
- [[Trotterization (Atlas)]] — the digital alternative
- [[Adiabatic Ramps and Shortcuts]] — preparing ground states by slow ramps
- [[Tensor Networks and MPS]] — the classical benchmark simulators are checked against
- [[Magnus Expansion]] — effective Hamiltonians from periodic driving
- [[Topological Phases of Matter]] — the invariants and edge states simulators measure
- [[Hubbard Models and Mott Insulators]] — the lattice models most simulators target
- [[Phase Transitions and Critical Phenomena]] — critical points and Kibble–Zurek scaling

---
Source: I. M. Georgescu, S. Ashhab & F. Nori, *Rev. Mod. Phys.* 86, 153 (2014); I. Bloch, J. Dalibard & S. Nascimbène, *Nature Phys.* 8, 267 (2012); C. Gross & I. Bloch, *Science* 357, 995 (2017); C. Monroe et al., *Rev. Mod. Phys.* 93, 025001 (2021)
