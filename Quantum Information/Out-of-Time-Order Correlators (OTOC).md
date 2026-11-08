#quantum-info #quantum

**Poke a many-body system at one site with an operator $V$, let it evolve for a time $t$, and ask whether a measurement $W$ at a distant site can tell the poke happened: the squared commutator $C(t) = \langle |[W(t), V]|^2\rangle$ measures exactly that, and its growth is how information spreads — scrambles — through a system.** Expanding the square gives a correlator whose operators are not in time order, $\langle W^\dagger(t)\,V^\dagger\,W(t)\,V\rangle$, hence the name *out-of-time-order correlator* (OTOC), and the reason no ordinary response measurement can read it: you have to run time backwards.

# Reference

$$
F(t) = \langle W^\dagger(t)\, V^\dagger\, W(t)\, V\rangle, \qquad C(t) = \big\langle [W(t),V]^\dagger [W(t),V] \big\rangle = 2\big(1 - \mathrm{Re}\,F(t)\big)
$$

- $W(t) = e^{iHt/\hbar}\,W\,e^{-iHt/\hbar}$ — the probe operator in the [[Heisenberg and Schrodinger Pictures|Heisenberg picture]]
- $V$ — the perturbation, applied at $t = 0$ on a different site from $W$
- $\langle\cdot\rangle$ — expectation value in the initial state, often thermal or infinite temperature
- $F$ — the OTOC itself
- $C$ — the squared [[Commutators and Anticommutators|commutator]]: the second equality needs unitary $W$, $V$ (e.g. Paulis)

**Picture:** operator growth — at $t = 0$, $W$ and $V$ sit on different sites and commute, so $C = 0$ and $F = 1$. Under evolution $W(t) = W + \tfrac{it}{\hbar}[H, W] + \cdots$ picks up nested commutators with $H$, and each one extends its support to more sites ([[Conjugation]]). When the support of $W(t)$ reaches the site of $V$, the two stop commuting: $C$ rises and $F$ decays. The OTOC measures how big the evolved operator has become.

**What its time dependence reveals:**

| Behaviour | Signature | Meaning |
|---|---|---|
| a front arriving at distance $x$ after $t \approx x/v_B$ | $C$ stays at zero, then rises | butterfly velocity $v_B$: the speed of operator spreading, at most the Lieb–Robinson velocity |
| early exponential growth $C \sim \epsilon\, e^{\lambda_L t}$ | in semiclassical or large-$N$ chaotic systems | quantum Lyapunov exponent, bounded by $\lambda_L \le 2\pi k_B T/\hbar$ |
| $\mathrm{Re}\,F \to 0$ at late times for every pair of local operators | scrambling | local information has spread into many-body correlations: not destroyed, but invisible to any local measurement |
| slow, partial, or reviving decay | integrable or many-body-localized dynamics | weak or no scrambling |

**Scrambling vs decoherence:** under unitary dynamics scrambled information is recoverable in principle, by reversing $H$. Coupling to an uncontrolled environment, or imperfect reversal, also makes $F$ decay, and that is the main experimental confound. The standard checks are running the same protocol with the interaction off (which should give no decay at all) and teleportation-based verification, which succeeds only if the information was scrambled rather than lost.

**How it is measured:** because $F$ contains $W(t)$ twice with $V$ between, the protocol evolves forward, applies $W$, evolves *backward*, applies $V$, and repeats, so it needs the sign of $H$ to be flipped on demand. That is why trapped ions and Rydberg arrays are natural platforms: their engineered spin–spin couplings change sign with a drive detuning or a laser phase (as in the [[Molmer-Sorensen Gate]]). A Loschmidt echo — evolve forward, perturb, evolve back, measure the return probability — is a special case.

> [!question]- Your measured OTOC decays even with the many-body interaction switched off. What does that tell you?
> With $H = 0$, $W(t) = W$ commutes with $V$ forever, so $C$ must stay zero and $F$ at 1. Any decay is decoherence or imperfect time reversal (control errors), not scrambling. That interaction-off run is the calibration of the decay floor, and only decay beyond it, ideally confirmed by a teleportation-fidelity test, counts as scrambling.

# Connections

- [[Heisenberg and Schrodinger Pictures]] — $W(t)$ is a Heisenberg-picture operator
- [[Commutators and Anticommutators]] — $C(t)$ is the norm of a commutator
- [[Conjugation]] — $e^{iHt}We^{-iHt}$ and its nested-commutator series are the operator growth
- [[Spin Chains and Magnons]] — the model systems where butterfly velocities and scrambling are studied
- [[Molmer-Sorensen Gate]] — the spin–spin interaction whose sign can be reversed for the backward evolution
- [[Spin Echo and Dynamical Decoupling]] — echoes reverse single-spin dephasing; OTOC protocols reverse many-body dynamics
- [[Quantum Teleportation]] — the basis of the verification test for scrambling
- [[Entanglement Measures]] — scrambled information lives in multi-party correlations
- [[Quench Dynamics and Thermalization]] — thermalization, light cones, and the exceptions

---
Source: B. Swingle, "Unscrambling the physics of out-of-time-order correlators," *Nat. Phys.* 14, 988 (2018); Maldacena, Shenker & Stanford, "A bound on chaos," *JHEP* 2016(8), 106; Gärttner et al., *Nat. Phys.* 13, 781 (2017); Landsman et al., *Nature* 567, 61 (2019)
