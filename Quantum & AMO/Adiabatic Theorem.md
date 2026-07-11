#quantum

**Change the Hamiltonian slowly compared to the gap and the system stays in the instantaneous eigenstate — the state follows the moving eigenbasis instead of jumping.** Slowness is measured against the *gap*, not against any absolute clock.

# Reference

For $H(t)$ with instantaneous eigenstates $H(t)|n(t)\rangle = E_n(t)|n(t)\rangle$, population stays in $|n\rangle$ when
$$
\frac{\hbar\,|\langle m|\dot H|n\rangle|}{(E_m - E_n)^2} \ll 1 \quad \text{for all } m \neq n
$$
**The gap enters squared** — halve the minimum gap and you must sweep four times slower. The danger zone is always the avoided-crossing bottleneck where $E_m - E_n$ is smallest; quantitative failure there is [[Landau-Zener Transitions]] ($P_{\text{jump}} = e^{-2\pi\Gamma}$).

**Adiabatic passage — the workhorse application:** chirp a drive from far below to far above resonance. The dressed eigenstate rotates continuously from $|g\rangle$ to $|e\rangle$, dragging the population with it. Result: **complete inversion robust to Rabi-frequency and pulse-area errors** — unlike a $\pi$ pulse, you don't need to hit $\Omega t = \pi$ exactly, just sweep slow enough ($|\dot\Delta| \ll \Omega^2$). This is rapid adiabatic passage (RAP); STIRAP is the three-level sibling riding a dark state.

Phases still accumulate along the way: dynamical $-\frac{1}{\hbar}\int E_n\,dt$ plus the geometric (Berry) phase depending only on the path in parameter space.

> [!question]- Why is adiabatic passage robust where a $\pi$ pulse is fragile?
> A $\pi$ pulse needs an exact pulse area — a 5% $\Omega$ error is a 5% rotation error. Passage only needs the sweep to *start* far below, *end* far above, and satisfy $|\dot\Delta| \ll \Omega^2$ in between; the transfer probability approaches 1 exponentially in the adiabaticity parameter rather than oscillating around it.

# Connections

- [[Landau-Zener Transitions]] — the quantitative jump probability when adiabaticity fails at a crossing
- [[Dressed States]] — the instantaneous eigenstates you follow in driven problems
- [[Two-Level Systems]] — minimal setting: eigenstate rotation vs mixing angle
- [[Resolved Sideband Cooling]] — RAP on sidebands for robust motional-state transfer

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §5.6
