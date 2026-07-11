#quantum-optics

**The cavity field you care about lives inside; the field you measure leaks out the mirror — input-output theory is the dictionary between them.** Everything you ever learn about intracavity dynamics arrives imprinted on the output field.

# Reference

Heisenberg-Langevin equation for a cavity mode coupled to the outside through one mirror at rate $\kappa$:

$$
\dot{a} = -\frac{i}{\hbar}[a, H_\mathrm{sys}] - \frac{\kappa}{2}a - \sqrt{\kappa}\, a_\mathrm{in}, \qquad a_\mathrm{out} = a_\mathrm{in} + \sqrt{\kappa}\, a
$$

**The output is the interference of the promptly-reflected input with the field leaking from inside.** (Sign conventions vary between texts — the physics is this interference; check signs before porting formulas.)

**Worked case — empty one-sided cavity, drive detuned by $\Delta$:** steady state gives the reflection coefficient

$$
r(\Delta) = -\frac{\kappa/2 + i\Delta}{\kappa/2 - i\Delta}
$$

— unit modulus (lossless), but the phase swings through $2\pi$ across the linewidth. That dispersive phase is exactly what [[Pound-Drever-Hall Locking]] demodulates into an error signal. Add internal loss or a second mirror and $|r|<1$: a dip appears.

**The noise term is not optional.** Damping alone ($-\kappa a/2$) would shrink $[a, a^\dagger]$ below 1 over time — unphysical. The vacuum entering through the same port ($a_\mathrm{in}$, with $[a_\mathrm{in}(t), a_\mathrm{in}^\dagger(t')] = \delta(t-t')$) restores the commutator: fluctuation-dissipation, operator edition. Same structure as the [[Lindblad Master Equation]], just in the Heisenberg picture with the environment kept explicit.

**Why it matters in practice:** [[Homodyne Detection]] of $a_\mathrm{out}$ measures intracavity quadratures filtered through the cavity response — this is how you read out squeezing, optomechanical motion, or a qubit dispersively coupled to the mode.

> [!question]- Why does an undriven, empty cavity still need the $a_\mathrm{in}$ term?
> Without it, $\dot{a} = -\kappa a/2$ decays the operator itself and $[a,a^\dagger] \to 0$ — commutation relations die. Vacuum fluctuations entering the lossy port at exactly the rate coherence leaks out preserve $[a,a^\dagger]=1$. Every loss channel is also an input channel.

# Connections

- [[Cavity QED]] — supplies the $H_\mathrm{sys}$ whose dynamics get imprinted on $a_\mathrm{out}$
- [[Homodyne Detection]] — the measurement that turns $a_\mathrm{out}$ into data
- [[Pound-Drever-Hall Locking]] — the reflection phase $r(\Delta)$ put to work
- [[Lindblad Master Equation]] — same open-system physics, Schrödinger-picture version
- [[Vacuum Fluctuations]] — what flows in through every open port

---
Source: Walls & Milburn, *Quantum Optics*, 2nd ed., Ch. 7
