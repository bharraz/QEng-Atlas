#quantum

**A system steered through a changing Hamiltonian stays in its instantaneous eigenstate if every part of the change is slow compared with the gap at that point; the fastest schedule that achieves this slows down where the gap is small and speeds up where it is large, and when even that is too slow, an added counterterm can cancel the transitions directly.**

The adiabatic condition itself is on [[Adiabatic Theorem]].

# Reference

**Global vs. local adiabaticity.** The naive reading of the adiabatic condition is "sweep slowly," which for a linear ramp means slow *everywhere* — including the long stretches where the gap is wide and nothing can go wrong. The condition is local:

$$\left|\frac{d\lambda}{dt}\right| \;\le\; \varepsilon\,\frac{\Delta(\lambda)^2}{\left|\langle m|\partial_\lambda H|n\rangle\right|}$$

with $\lambda$ the control parameter and $\Delta$ the instantaneous gap. **Saturating this pointwise gives the optimal schedule**: $\dot\lambda \propto \Delta^2$, so the ramp slows quadratically as the gap narrows and speeds up again after. For a problem whose gap dips once, almost all the time is spent in the neighbourhood of $\Delta_{\min}$, and the total time scales as
$$T \;\sim\; \frac{1}{\Delta_{\min}^{2}}$$
rather than the far worse figure a uniform ramp would need. **The gap profile is the schedule** — measure or estimate $\Delta(\lambda)$ first, then integrate.

**Picture:** driving through a valley with a speed limit set by its narrowest point: slow down where the gap is small and go fast elsewhere.

## Ramp shape matters as much as ramp rate

A linear ramp is discontinuous in $\dot\lambda$ at its endpoints, and those kinks are themselves a broadband excitation. **Boundary cancellation:** if the schedule's first $k$ derivatives vanish at both ends, the residual excitation falls off as $1/T^{k+1}$ instead of $1/T$ — and for a schedule smooth to all orders the error can fall *exponentially* in $T$. Smoothing the turn-on and turn-off is usually cheaper than lengthening the ramp.

| Schedule | $\dot\lambda$ at ends | Error scaling | Use |
|---|---|---|---|
| Linear | finite (kinked) | $\sim 1/T$ | never, unless the gap is flat and huge |
| $\sin^2$ / raised cosine | zero | $\sim 1/T^3$ | the default smooth ramp |
| Blackman, Gaussian-smoothed | zero to higher order | steeper | pulse turn-on/off, gate envelopes |
| $\tanh$ | asymptotically zero | exponential in width | avoided crossings; RAP chirps |
| Gap-following ($\dot\lambda \propto \Delta^2$) | set by $\Delta$ | optimal for fixed $T$ | when $\Delta(\lambda)$ is known |

This is the same argument as window functions in spectral estimation — a hard edge in time is broad in frequency, and the ramp's spectral content at the gap frequency is exactly what drives the unwanted transition ([[Window Functions and Apodization]], [[Noise Spectroscopy and Filter Functions]]).

## Shortcuts to adiabaticity

When even the optimal schedule is too slow, stop trying to be adiabatic and instead cancel the transitions:

**Counterdiabatic (transitionless) driving.** Add
$$H_{\text{CD}} = i\hbar\sum_n\Big(|\partial_t n\rangle\langle n| - \langle n|\partial_t n\rangle\,|n\rangle\langle n|\Big)$$
and the system follows the instantaneous eigenstates **exactly, at any speed**. The limitation is practical, not conceptual: constructing $H_{\text{CD}}$ requires knowing the eigenstates, and it generically demands couplings the apparatus does not have — non-local terms, or operators outside the available control set ([[Dynamical Lie Algebras and Closure]] decides whether it is reachable at all). Local approximations to $H_{\text{CD}}$ are the working compromise.

**Invariant-based inverse engineering.** Choose the trajectory first, then solve backwards for the Hamiltonian that produces it, using a Lewis–Riesenfeld invariant. Standard for moving and expanding traps — ion transport and tweezer motion — because there the exact invariant is known.

| Approach | Needs | Gives |
|---|---|---|
| Optimal schedule | the gap profile $\Delta(\lambda)$ | best use of a fixed total time |
| Boundary smoothing | nothing | large error reduction, free |
| Counterdiabatic | eigenstates + extra couplings | exact transfer at any speed |
| Invariant-based | an exactly known invariant | designed trajectory, realizable controls |

## Adiabatic quantum computing

Encode the answer in the ground state of $H_{\text{final}}$, start in the easy ground state of $H_{\text{init}}$, and interpolate:
$$H(s) = (1-s)\,H_{\text{init}} + s\,H_{\text{final}}, \qquad s = t/T$$

- **Runtime is set entirely by $\Delta_{\min}$** along the path. This is the central issue: for hard instances the gap can close *exponentially* in problem size, and then $T \sim 1/\Delta_{\min}^2$ is exponential too.
- Adiabatic quantum computation with a general $H$ is **polynomially equivalent to the circuit model** — a different way to implement computation, not more power.
- **Quantum annealing** is the finite-temperature, restricted-Hamiltonian variant (typically transverse-field Ising, [[Spin Chains and Magnons]]), and it is a heuristic — no gap guarantee. QAOA is the gate-based version: a Trotterized sweep whose step angles are optimized rather than prescribed ([[Variational Quantum Algorithms]]).

## Where ramps appear in the lab

Rapid adiabatic passage chirps and STIRAP pulse ordering ([[EIT and STIRAP]]); ion transport and shuttling between trap zones; tweezer moves during atom rearrangement ([[Optical Tweezers]]); trap-frequency and evaporation ramps; gate envelope turn-on and turn-off, where the smoothness argument above is the reason pulses are shaped rather than square ([[Magnus Expansion]]).

> [!question]- Your transfer fidelity is limited by non-adiabatic loss. Would you rather double the ramp time or smooth its endpoints?
> Smooth the endpoints, almost always. A linear ramp's error is dominated by the kinks in $\dot\lambda$ at the start and end, falling only as $1/T$ — doubling $T$ gains a factor of two. Making the first derivatives vanish changes the scaling to $1/T^3$ or better at no extra time cost. Lengthen the ramp only after the schedule is smooth and gap-weighted.

# Connections

- [[Adiabatic Theorem]] — the condition a ramp schedule must satisfy
- [[Landau-Zener Transitions]] — the exact two-level answer at a single avoided crossing
- [[Berry Phase and Geometric Phases]] — the phase accumulated along the path, independent of rate
- [[Spin Chains and Magnons]] — transverse-field Ising as the standard annealing Hamiltonian
- [[Dynamical Lie Algebras and Closure]] — whether the counterdiabatic terms are reachable with your controls
- [[EIT and STIRAP]] — adiabatic passage through a dark state
- [[Optical Tweezers]] — moving traps without heating, the invariant-engineering case
- [[Window Functions and Apodization]] — the same hard-edge/spectral-leakage argument
- [[Objective Functions and Constraints]] — schedule optimization as a constrained problem
- [[Pulse Shaping and Optimal Control]] — numerical and analytic pulse design
- [[Variational Quantum Algorithms]] — QAOA, a discretized adiabatic sweep with optimized angles

---
Source: Albash & Lidar, "Adiabatic quantum computation," *Rev. Mod. Phys.* 90, 015002 (2018); Guéry-Odelin et al., "Shortcuts to adiabaticity," *Rev. Mod. Phys.* 91, 045001 (2019)
