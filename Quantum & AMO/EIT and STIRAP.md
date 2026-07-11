#AMO #quantum

**The Λ system holds a dark state — a superposition of the two ground states that the light cannot excite because the two excitation amplitudes interfere destructively. Park in it and the medium turns transparent (EIT); rotate it slowly by ramping the two lasers and population moves between ground states without ever touching the lossy excited state (STIRAP).** One piece of interference, two workhorse techniques.

# Reference

**The dark state.** Λ system as in [[Raman Transitions]]: $|1\rangle, |2\rangle$ coupled to $|e\rangle$ by $\Omega_P$ (probe/pump) and $\Omega_S$ (Stokes/control), on two-photon resonance. One superposition decouples exactly:

$$|D\rangle = \frac{\Omega_S|1\rangle - \Omega_P|2\rangle}{\sqrt{\Omega_P^2 + \Omega_S^2}}, \qquad \langle e|H|D\rangle = 0$$

— the two paths to $|e\rangle$ cancel. Its orthogonal partner $|B\rangle$ (bright state) carries all the coupling. The dark state contains no $|e\rangle$: **no spontaneous emission from a state that is never excited** — the resource both techniques spend. Its composition is steered by the *ratio* $\Omega_P/\Omega_S$: all-$|1\rangle$ when $\Omega_S \gg \Omega_P$, all-$|2\rangle$ in the opposite limit.

**EIT — electromagnetically induced transparency.** Shine a strong control $\Omega_S$ on an absorbing medium and scan the weak probe: exactly on two-photon resonance, atoms pump into $|D\rangle$ and absorption vanishes — a narrow transparency window of width $\sim \Omega_S^2/\Gamma$ (power-broadened but *not* limited by $\Gamma$; ultimately limited by the ground-state coherence time) carved into a natural linewidth. Kramers–Kronig ([[Kramers-Kronig Relations]]) forces steep dispersion across the narrow window → group velocities down to m/s (**slow light**), and ramping $\Omega_S \to 0$ maps the probe pulse onto the ground-state coherence (**stored light** — the atomic quantum-memory protocol). The same narrow dark resonance without the "transparency" framing is **CPT**, the basis of chip-scale atomic clocks; Rydberg-EIT makes the probe photons inherit blockade interactions (photon-photon gates) and doubles as the standard non-destructive probe of Rydberg states.

**STIRAP — stimulated Raman adiabatic passage.** To transfer $|1\rangle \to |2\rangle$: apply the pulses in the **counterintuitive order** — Stokes ($\Omega_S$, coupling the *empty* states) first, then probe, overlapping. At early times $|D\rangle = |1\rangle$ (where the population already is); as the ratio sweeps, $|D\rangle$ rotates continuously into $|2\rangle$, dragging the population with it. Adiabaticity requires the rotation slower than the gap to the bright states:

$$\Omega_{\text{eff}}\, \tau_{\text{overlap}} \gg 1 \quad (\text{pulse area} \gtrsim 10 \text{ in practice}),$$

and delivers the defining robustness: transfer efficiency insensitive to pulse *area*, shape, and timing details — compare a Raman π-pulse, which needs $\Omega t = \pi$ calibrated and stable. Costs: slow (adiabatic), needs two-photon resonance held (that *is* sensitive), and imperfect adiabaticity leaks through $|B\rangle$ → scattering. Used wherever a calibrated π-pulse is fragile: molecule state transfer (STIRAP built ground-state ultracold molecules), Rydberg excitation, NV/solid-state defects with inhomogeneous $\Omega$, shortcut-to-adiabaticity variants when speed matters.

**The unifying picture** — three uses of one dark state: *sit in it* (EIT/CPT: spectroscopy, memory), *rotate it* (STIRAP: transfer), *let light and dark-state coherence hybridize* (dark-state polaritons: slow/stored light). And the failure channel is always the same: anything that distinguishes the two ground states (Zeeman shifts, differential light shifts, ground-state decoherence) breaks the destructive interference and grays the dark state — ground-state coherence is the budget line.

> [!question]- Why does STIRAP fire the Stokes laser — coupling two *empty* states — first? Intuition says drive the populated transition.
> The Stokes pulse's job isn't to move population; it's to *define the dark state correctly before anything happens*. With $\Omega_S$ on and $\Omega_P$ off, $|D\rangle = |1\rangle$ exactly — the populated state IS dark from the outset, and the system starts perfectly protected. Fire the probe first and $|1\rangle$ is a 50/50 mix of dark and bright: half the population couples to $|e\rangle$ and scatters. The counterintuitive ordering is just "initialize the protection before touching the system" — intuitive after all.

# Connections

- [[Raman Transitions]] — the same Λ system driven diabatically with pulse areas
- [[Dressed States]] — dark/bright states are the dressed basis of the driven Λ system
- [[Adiabatic Theorem]] / [[Landau-Zener Transitions]] — the adiabaticity condition and its breakdown
- [[Optical Pumping]] — CPT is optical pumping into a coherence rather than a level
- [[Kramers-Kronig Relations]] — transparency window → steep dispersion → slow light
- [[Rydberg Atoms and Blockade]] — Rydberg-EIT: photon interactions and state detection

---
Source: Fleischhauer, Imamoğlu & Marangos, "EIT: optics in coherent media," *Rev. Mod. Phys.* 77, 633 (2005); Vitanov et al., "STIRAP," *Rev. Mod. Phys.* 89, 015006 (2017)
