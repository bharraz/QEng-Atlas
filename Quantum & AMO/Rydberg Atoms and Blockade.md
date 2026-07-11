#AMO #quantum-info

**A Rydberg state is a hydrogen-like state of huge principal quantum number $n$; its exaggerated size makes atoms interact over microns, and the blockade — one excitation shifting its neighbors out of resonance — converts that interaction into the two-qubit gate of neutral-atom quantum computing.** This is the page that turns tweezer arrays from a trapping story into a computing platform.

# Reference

**Everything scales as a power of $n$** (the electron orbits far outside the core, so hydrogen formulas apply with a quantum defect $\delta_\ell$: $E_n = -\mathrm{Ry}/(n-\delta_\ell)^2$):

| Property | Scaling | At $n = 70$ (Rb) |
|---|---|---|
| Orbit radius | $n^2$ | ~0.5 µm — mesoscopic |
| Radiative lifetime | $n^3$ | ~100–400 µs (vs 26 ns for 5p) |
| Polarizability | $n^7$ | enormous — Rydbergs feel every stray E-field |
| van der Waals $C_6$ | $n^{11}$ | ~GHz·µm⁶ |
| Level spacing | $n^{-3}$ | tens of GHz — microwave-accessible |

The $n^{11}$ is the punchline: interactions tunable over ~12 orders of magnitude by choosing $n$, reaching **GHz-scale at µm distances** — while ground-state atoms at the same distance interact at the mHz level. Neutral atoms are "non-interacting until you say otherwise," which is exactly what a qubit register wants.

**The blockade mechanism.** Drive the ground→Rydberg transition with Rabi frequency $\Omega$. With one atom already Rydberg, a second excitation within range is shifted by $V(r) = C_6/r^6 \gg \hbar\Omega$: doubly-excited states are simply off-resonant. Inside the **blockade radius**

$$R_b = \left(\frac{C_6}{\hbar\Omega}\right)^{1/6} \sim 5\text{–}10\ \mu\text{m},$$

the ensemble supports at most one excitation. Two signatures worth remembering: the allowed state is the *symmetric* one, $(|rg\rangle + |gr\rangle)/\sqrt 2$ — blockade **creates entanglement by forbidding a state** — and it couples with enhanced Rabi frequency $\sqrt{N}\,\Omega$ ($\sqrt 2$ for a pair), the experimental fingerprint of being blockaded. The $1/6$ power means $R_b$ is insensitive to everything — blockade is robust to distance and intensity fluctuations, which is *why* the gate works without interferometric positioning.

**The gate.** Canonical protocol (π on control, 2π on target, π on control): if the control was excited, the target's 2π pulse is blockaded and returns no phase; if not, it acquires −1. Result: controlled-Z, with the entangling phase coming from *blocked dynamics* — the atoms never need to sit at a calibrated interaction strength, only inside $R_b$. Modern variants (two-pulse, amplitude/phase-shaped) reach fidelities ~99.5%; the error budget is Rydberg-state decay (finite $n^3$ lifetime — you want to spend as little time Rydberg as possible), Doppler dephasing of the two-photon drive (atoms are ~µK, not at rest), and stray-field sensitivity ($n^7$).

**Why the platform scales:** the same atom is qubit (hyperfine clock states, seconds of coherence), and gate resource (Rydberg, on demand); tweezers rearrange to arbitrary geometries; blockade needs only proximity, so connectivity is reconfigurable — physically moving qubits mid-circuit is a working primitive. Current arrays: hundreds to ~1000 atoms, logical-qubit demonstrations. The same blockade physics run in "analog mode" (global drive, fixed geometry) makes the arrays quantum simulators of Ising models — the second half of the literature.

**Rydberg dressing** (the perturbative cousin): admix a small Rydberg fraction into the ground state with an off-resonant drive — a tunable ground-state interaction $\sim (\Omega/2\Delta)^4 V$, paid for with $(\Omega/2\Delta)^2$ of the Rydberg decay. Simulation tool more than gate tool.

> [!question]- Why do Rydberg gates run in µs while the Rydberg lifetime is only ~100 µs — isn't a 1% error floor built in?
> That's precisely the design tension. Gate error from decay ~ (time spent Rydberg)/lifetime, so protocols minimize Rydberg residence: blockade gates only virtually populate the doubly-excited state, pulse shaping keeps the population transfer brief, and higher $\Omega$ (faster gates) directly buys fidelity — until increasing $\Omega$ shrinks $R_b$ ($R_b \propto \Omega^{-1/6}$, slowly) or demands more laser power than the two-photon transition can deliver cleanly. The community's push for UV single-photon transitions and higher power is this arithmetic, not convenience.

# Connections

- [[Optical Tweezers]] — the trap architecture the register lives in
- [[Stark Effect and Light Shifts]] — the $n^7$ polarizability; also why traps must be turned off or magic-tuned during Rydberg pulses
- [[Raman Transitions]] — the two-photon excitation scheme and its Doppler sensitivity
- [[Entangling Gates]] — where blockade-CZ sits among the two-qubit gate families
- [[Dressed States]] — Rydberg dressing is this formalism applied to interactions
- [[Hyperfine Structure]] — the ground-state qubit the Rydberg gate serves

---
Source: Saffman, Walker & Mølmer, *Rev. Mod. Phys.* 82, 2313 (2010); Browaeys & Lahaye, *Nat. Phys.* 16, 132 (2020); Evered et al., *Nature* 622, 268 (2023) (high-fidelity gates)
