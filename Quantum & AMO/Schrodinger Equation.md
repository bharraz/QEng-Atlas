#quantum

**The Hamiltonian generates time translation: solve its eigenvalue problem once and every state just spins phases $e^{-iEt/\hbar}$ on the eigencomponents.** All quantum dynamics is "diagonalize, attach phases, transform back."

# Reference

**Time-dependent (TDSE):**
$$
i\hbar\,\partial_t|\psi(t)\rangle = H|\psi(t)\rangle \;\;\Rightarrow\;\; |\psi(t)\rangle = e^{-iHt/\hbar}|\psi(0)\rangle \quad (H \text{ time-independent})
$$

**Time-independent (TISE)** — the eigenvalue problem that TDSE reduces to:
$$
H|E_n\rangle = E_n|E_n\rangle \;\;\Rightarrow\;\; |\psi(t)\rangle = \sum_n c_n\, e^{-iE_n t/\hbar}|E_n\rangle, \quad c_n = \langle E_n|\psi(0)\rangle
$$

**Stationary states:** a single $|E_n\rangle$ only acquires global phase — all observables frozen. **Dynamics lives in superpositions:** two levels split by $\Delta E$ beat at $\omega = \Delta E/\hbar$; relative phases are what move. That beat note *is* Ramsey fringes, Rabi flopping in the dressed basis, wavepacket motion.

For time-dependent $H(t)$: no simple exponential (the $H(t_1), H(t_2)$ generally don't commute) — you get the time-ordered exponential, handled perturbatively in the [[Interaction Picture]] or by transforming to a [[Rotating Frame Transformation]] where $H$ becomes static.

> [!question]- Why does an energy eigenstate show no dynamics, while a superposition does?
> Global phase is unphysical, so $e^{-iE_nt/\hbar}|E_n\rangle$ is the same state. A superposition carries *relative* phases $e^{-i(E_m-E_n)t/\hbar}$, which rotate expectation values of any operator connecting the levels at the Bohr frequencies $(E_m - E_n)/\hbar$.

# Connections

- [[Heisenberg and Schrodinger Pictures]] — same physics with time moved onto operators
- [[Quantum Harmonic Oscillator]] — the canonical TISE solve
- [[Matrix Exponential]] — $e^{-iHt/\hbar}$ is where all its machinery gets used
- [[Interaction Picture]] — how to proceed when $H = H_0 + V(t)$
- [[Spectral Theorem]] — why "diagonalize then phase" works at all

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §2.1
