#quantum

**Same physics, different bookkeeping: Schrödinger puts the time evolution on states, Heisenberg puts it on operators.** Only matrix elements $\langle\psi|O|\psi\rangle$ are measurable, so you can slide the $U$'s to whichever side is convenient.

# Reference

With $U(t) = e^{-iHt/\hbar}$:

| | Schrödinger | Heisenberg |
|---|---|---|
| States | $\|\psi(t)\rangle = U\|\psi(0)\rangle$ | frozen |
| Operators | frozen | $O_H(t) = U^\dagger O\, U$ |
| Equation of motion | $i\hbar\,\partial_t\|\psi\rangle = H\|\psi\rangle$ | $\dfrac{dO_H}{dt} = \dfrac{i}{\hbar}[H, O_H] + \left(\partial_t O\right)_H$ |

**Heisenberg EOM is the quantum–classical bridge:** $[H,\cdot]/i\hbar$ plays the role of the Poisson bracket, so operators obey classical-looking equations. For the oscillator: $\dot{x} = p/m$, $\dot{p} = -m\omega^2 x$ — exactly Newton, now for operators (Ehrenfest).

**When each wins:**
- Schrödinger: wavefunction problems, numerics (evolve one vector, not $d^2$ operator entries).
- Heisenberg: few operators with closed EOMs — oscillators, linear optics, input-output theory, anything Gaussian. Also the natural home of $[H,O] = \lambda O$ ladder structure.
- Constants of motion are transparent: $[H,O]=0 \Rightarrow O_H(t) = O$ forever.

Ordering gotcha: $O_H(t_1)$ and $O_H(t_2)$ generally don't commute even if the Schrödinger operators did — that's where two-time correlation functions get their structure.

> [!question]- In the Heisenberg picture, what immediately identifies a conserved quantity?
> $[H, O] = 0$ (with no explicit time dependence): the EOM gives $dO_H/dt = 0$, so $O$ is a constant of motion and its eigenvalues are good quantum numbers.

# Connections

- [[Interaction Picture]] — the hybrid: $H_0$ moves operators, $V$ moves states
- [[Commutators and Anticommutators]] — the algebra driving the Heisenberg EOM
- [[Schrodinger Equation]] — the state-side dynamics this rearranges
- [[Ladder Operators]] — $[H,a] = -\hbar\omega a$ gives $a_H(t) = a\,e^{-i\omega t}$, the cleanest Heisenberg solve

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §2.2
