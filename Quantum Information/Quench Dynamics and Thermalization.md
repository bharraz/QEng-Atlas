#quantum-info #quantum

**Prepare many interacting particles in a simple state — every spin up, or one atom on every other site — then suddenly change the Hamiltonian and let the system evolve with no contact to the outside: local quantities usually relax to the values a thermal state would give, because each small region becomes entangled with the rest of the system, which acts as its heat bath.** The exceptions, collected in the table below, are what quench experiments look for.

# Reference

**The setup.** An isolated system starts in $|\psi_0\rangle$ (usually a product state), evolves under a new Hamiltonian $H$, and is measured on small subsystems at later times. The global state stays pure; only local observables can look thermal, with the rest of the system as their bath.

**Why most systems thermalize — the eigenstate thermalization hypothesis (ETH):**

$$
\langle E_m|\,O\,|E_n\rangle = O(E)\,\delta_{mn} + e^{-S(E)/2} f_O(E,\omega)\,R_{mn}
$$

- $\lvert E_n\rangle$ — energy eigenstates of the many-body Hamiltonian
- $O$ — a local observable, such as one spin's magnetization
- $O(E)$ — smooth function of energy: the thermal value at energy $E$
- $S(E)$ — thermodynamic entropy at energy $E$
- $f_O(E, \omega)$ — smooth function of mean energy and energy difference $\omega$
- $R_{mn}$ — erratic numbers of order one

The diagonal term says every eigenstate already gives thermal values for local observables, so the long-time average after a quench is thermal; the off-diagonal term is exponentially small in system size, so fluctuations about that average are small.

**Picture:** a closed system is its own bath — a small region exchanges energy and entanglement with the rest the way a cup of coffee equilibrates with the room.

**Ways an isolated system fails to thermalize, or takes very long to:**

| Behaviour | Mechanism | Signature | Where studied |
|---|---|---|---|
| integrable dynamics | many conserved quantities restrict where the state can go; it relaxes to a generalized Gibbs ensemble instead of a thermal one | a steady state that is not thermal | 1D Bose gases; free-fermion spin chains ([[Spin Chains and Magnons]]) |
| many-body localization | strong disorder creates local conserved quantities | memory of the initial pattern persists; entanglement grows only logarithmically in time | atoms in quasi-random lattices, ion chains with random fields, superconducting arrays; stability in very large systems is still debated |
| quantum many-body scars | a few special non-thermal eigenstates inside an otherwise thermal spectrum | persistent revivals from particular initial states, ordinary thermalization from others | Rydberg arrays under blockade ([[Rydberg Atoms and Blockade]]) |
| Hilbert-space fragmentation | kinetic constraints split the state space into disconnected sectors | memory of the initial state in constrained dynamics | tilted lattices with dipole conservation |
| prethermalization | weak breaking of a conservation law, or a fast periodic drive | fast relaxation to a long-lived plateau, true thermalization much later | Floquet-driven systems, where heating is exponentially slow in the ratio of drive frequency to the local energy scale |
| discrete time crystal | a periodic drive with localization or prethermal protection | oscillation at a multiple of the drive period that stays locked despite imperfect drive pulses | ions, NV ensembles, superconducting qubits |

**How fast correlations spread.** For short-range interactions, signals and correlations travel no faster than a finite velocity: the Lieb–Robinson bound,

$$
\lVert [A(t), B] \rVert \le c\, e^{(v t - r)/\xi}
$$

- $A, B$ — local operators separated by distance $r$
- $v$ — the Lieb–Robinson velocity (sites per unit time): speed of the light cone
- $\xi, c$ — constants set by the interactions

Outside the light cone $r > vt$ commutators, and therefore correlations created by the quench, are exponentially small. Long-range interactions ($\propto 1/r^\alpha$, as in trapped ions) bend or remove the light cone when $\alpha$ is small enough. Operator spreading inside the cone is measured by [[Out-of-Time-Order Correlators (OTOC)]].

**Entanglement growth.** After a quench the entanglement entropy of a subsystem grows linearly in time in a thermalizing system and saturates at a value proportional to the subsystem's volume; under many-body localization it grows logarithmically; in non-interacting localized systems it saturates quickly ([[Quantum Entropies and Information]]).

**Slow ramps through a transition — Kibble–Zurek.** Ramping a parameter across a quantum critical point over a time $\tau_Q$, the system follows adiabatically until the closing gap makes it too slow, and the leftover excitations (domain walls, defects) have density

$$
n_\text{def} \propto \tau_Q^{-d\nu/(1+z\nu)}
$$

- $\tau_Q$ — ramp time across the transition (s)
- $d$ — spatial dimension
- $\nu, z$ — correlation-length and dynamical critical exponents

so measuring defect density against ramp speed measures critical exponents ([[Adiabatic Ramps and Shortcuts]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| a local magnetization or density against time | relaxation, and whether its final value is the thermal one |
| imbalance between initially occupied and empty sites | memory of the initial state, the standard localization signal |
| connected correlations against distance and time | light-cone spreading and its velocity |
| Rényi entropy of subsystems, from randomized measurements or interference of two copies | entanglement growth: linear, logarithmic, or saturating |
| return probability to the initial state | revivals, the signature of scars |
| response at a fraction of the drive frequency | time-crystalline order |
| defect density against ramp time | Kibble–Zurek scaling and critical exponents |

> [!question]- After a quench, a local magnetization settles to a steady value that does not match the thermal prediction for the initial state's energy. What could cause this?
> Extra conserved quantities (an integrable model relaxing to a generalized Gibbs ensemble), disorder strong enough to localize, or a prethermal plateau that would still evolve given more time. Varying the disorder strength, adding a perturbation that breaks integrability, and extending the evolution time separate these. Decoherence and finite size can also produce apparent steady states, so the same check against system size and coupling to the environment is needed.

# Connections

- [[Spin Chains and Magnons]] — the models most quench experiments run
- [[Analog Quantum Simulation]] — the platforms that perform these experiments
- [[Out-of-Time-Order Correlators (OTOC)]] — operator spreading and scrambling inside the light cone
- [[Quantum Entropies and Information]] — entanglement entropy and its measurement
- [[Thermal States]] — the states local observables relax toward
- [[Tensor Networks and MPS]] — classical simulation, limited by the entanglement growth described here
- [[Exact Diagonalization and Sparse Methods]] — checking small systems against ETH
- [[Magnus Expansion]] — the effective Hamiltonian of a periodic drive, behind prethermal plateaus
- [[Adiabatic Ramps and Shortcuts]] — the slow-ramp limit that Kibble–Zurek departs from
- [[Rydberg Atoms and Blockade]] — the platform where scars were found
- [[Phase Transitions and Critical Phenomena]] — ramps through critical points

---
Source: L. D'Alessio, Y. Kafri, A. Polkovnikov & M. Rigol, *Adv. Phys.* 65, 239 (2016); D. A. Abanin, E. Altman, I. Bloch & M. Serbyn, *Rev. Mod. Phys.* 91, 021001 (2019); M. Serbyn, D. A. Abanin & Z. Papić, *Nature Phys.* 17, 675 (2021); D. V. Else, C. Monroe, C. Nayak & N. Y. Yao, *Annu. Rev. Condens. Matter Phys.* 11, 467 (2020)
