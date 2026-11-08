#AMO #quantum-info

**A Rydberg state is a hydrogen-like state of huge principal quantum number $n$; its exaggerated size makes atoms interact over microns, and the blockade — one excitation shifting its neighbors out of resonance — converts that interaction into the two-qubit gate of neutral-atom quantum computing.**

# Reference

**Everything scales as a power of $n$** (the electron orbits far outside the core, so hydrogen formulas apply with a quantum defect $\delta_\ell$: $E_n = -\mathrm{Ry}/(n-\delta_\ell)^2$):

| Property | Scaling | At $n = 70$ (Rb) |
|---|---|---|
| Orbit radius | $n^2$ | ~0.5 µm — mesoscopic |
| Radiative lifetime | $n^3$ | ~100–400 µs (vs 26 ns for 5p) |
| Polarizability | $n^7$ | enormous — Rydbergs feel every stray E-field |
| van der Waals $C_6$ | $n^{11}$ | ~700 GHz·µm⁶ (Rb $nS$) |
| Level spacing | $n^{-3}$ | tens of GHz — microwave-accessible |

Because of the $n^{11}$ scaling, interactions are tunable over ~12 orders of magnitude by choosing $n$, reaching **GHz-scale at µm distances** — while ground-state atoms at the same distance interact at the mHz level. Neutral atoms are "non-interacting until you say otherwise," which is exactly what a qubit register wants.

**The blockade mechanism.** Drive the ground→Rydberg transition with Rabi frequency $\Omega$. With one atom already Rydberg, a second excitation within range is shifted by $V(r) = C_6/r^6 \gg \hbar\Omega$: doubly-excited states are off-resonant. Inside the **blockade radius**

$$R_b = \left(\frac{C_6}{\hbar\Omega}\right)^{1/6} \sim 5\text{–}10\ \mu\text{m},$$

- $R_b$ — blockade radius (m): where the shift $V(r)=C_6/r^6$ equals the drive's linewidth $\hbar\Omega$
- $C_6$ — van der Waals coefficient (J·m⁶, often quoted in GHz·µm⁶), scaling as $n^{11}$
- $\hbar\Omega$ — energy width of the excitation drive (J), with $\Omega$ the ground→Rydberg Rabi frequency (rad/s)

**Picture:** an atom swollen to a micron across: neighbours within a few microns shift its excitation energy so much that only one atom in the region can be excited.

**Inside $R_b$ the ensemble supports at most one excitation.** Two signatures worth remembering:

- The allowed state is the *symmetric* one, $(|rg\rangle + |gr\rangle)/\sqrt 2$ — blockade **creates entanglement by forbidding a state**, not by engineering an interaction strength.
- It couples with enhanced Rabi frequency $\sqrt N\,\Omega$ ($\sqrt2$ for a pair) — the experimental fingerprint that you are blockaded.

The $1/6$ power is why the mechanism is usable at all: $R_b$ barely moves with $C_6$ or $\Omega$, so blockade tolerates distance and intensity fluctuations, and the gate needs no interferometric positioning.

**The gate.** The standard protocol is π on the control, 2π on the target, π on the control: if the control was excited, the target's 2π pulse is blockaded and returns no phase; if not, it acquires −1. Result: controlled-Z, with the entangling phase coming from *blocked dynamics* — the atoms never need to sit at a calibrated interaction strength, only inside $R_b$. The error budget, in order of typical importance:
- **Rydberg-state decay** (finite $n^3$ lifetime, so minimize time spent in the Rydberg state);
- **Doppler dephasing** of the two-photon drive (atoms are µK, not at rest, and axial position spread dominates — see [[Optical Tweezers]]);
- **stray-field sensitivity** through the $n^7$ polarizability.

Amplitude- and phase-shaped protocols attack the first by shortening Rydberg residence.

**Why the platform scales**, structurally:

- **One atom, two roles** — hyperfine clock states are the memory (long-lived, field-insensitive), the Rydberg state is the gate resource, summoned only when needed. Idle qubits do not interact at all.
- **Reconfigurable connectivity** — blockade needs only proximity, and tweezers can move atoms, so physically transporting qubits mid-circuit is a working primitive rather than an exotic one.
- **Identical qubits by construction** — atoms of a species are indistinguishable, so there is no fabrication-disorder problem of the kind that afflicts solid-state platforms.

Run with a global drive on a fixed geometry instead, and the same blockade becomes an Ising-model quantum simulator — the analog half of the literature.

**Rydberg dressing** (the perturbative variant): admix a small Rydberg fraction into the ground state with an off-resonant drive — a tunable ground-state interaction $\sim (\Omega/2\Delta)^4 V$, paid for with $(\Omega/2\Delta)^2$ of the Rydberg decay. Simulation tool more than gate tool.

> [!question]- Why do Rydberg gates run in µs while the Rydberg lifetime is only ~100 µs — isn't a 1% error floor built in?
> That's precisely the design tension. Gate error from decay ~ (time spent Rydberg)/lifetime, so protocols minimize Rydberg residence: blockade gates only virtually populate the doubly-excited state, pulse shaping keeps the population transfer brief, and higher $\Omega$ (faster gates) directly improves fidelity — until increasing $\Omega$ shrinks $R_b$ ($R_b \propto \Omega^{-1/6}$, slowly) or demands more laser power than the two-photon transition can deliver cleanly. The community's push for UV single-photon transitions and higher power is this arithmetic, not convenience.

# Connections

- [[Optical Tweezers]] — the trap architecture the register lives in
- [[Stark Effect and Light Shifts]] — the $n^7$ polarizability; also why traps must be turned off or magic-tuned during Rydberg pulses
- [[Raman Transitions]] — the two-photon excitation scheme and its Doppler sensitivity
- [[Entangling Gates]] — where blockade-CZ sits among the two-qubit gate families
- [[Dressed States]] — Rydberg dressing is this formalism applied to interactions
- [[Hyperfine Structure]] — the ground-state qubit the Rydberg gate serves
- [[Analog Quantum Simulation]] — Rydberg arrays as simulators of constrained spin models
- [[Two-Qubit Gate Mechanisms]] — the blockade gate compared with other platforms
- [[Qudits and Multi-Qubit Gates]] — blockade among three or more atoms
- [[Effective Hamiltonians and Adiabatic Elimination]] — Rydberg dressing as a fourth-order effective interaction
- [[Variational Quantum Algorithms]] — blockade-encoded maximum independent set

---
Source: Saffman, Walker & Mølmer, *Rev. Mod. Phys.* 82, 2313 (2010); Browaeys & Lahaye, *Nat. Phys.* 16, 132 (2020); Evered et al., *Nature* 622, 268 (2023) (high-fidelity gates)
