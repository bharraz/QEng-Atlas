#quantum

**Couple a discrete state to a continuum and coherent oscillation becomes irreversible exponential decay at a constant rate: coupling squared times the density of final states.** This is where every decay rate, scattering rate, and linewidth comes from.

# Reference

$$
\Gamma_{i\to f} = \frac{2\pi}{\hbar}\,\left|\langle f|V|i\rangle\right|^2\,\rho(E_f)\Big|_{E_f = E_i}
$$

$\Gamma$ = transition rate (s⁻¹); $\langle f|V|i\rangle$ = coupling matrix element (J), squared because rates go as probability not amplitude; $\rho(E_f)$ = density of final states (states per J) evaluated at the conserved energy — for a monochromatic drive, at $E_i \pm \hbar\omega$. Units check: J² × (1/J) / (J·s) = 1/s.

The whole formula is coupling² × availability, and the two factors are independently engineerable: change the matrix element (dipole strength, polarization, Franck–Condon overlap) or change the density of states (cavity, photonic bandgap, dimensionality). Everything from Purcell enhancement to phonon-bottleneck effects is one or the other.

**Why a rate and not Rabi flopping:** to a single final state, first-order TDPT gives $P(t) \propto \sin^2$-oscillation. Summed over a continuum, the $\mathrm{sinc}^2(\omega_{fi}t/2)$ lineshape narrows as $1/t$ while its peak grows as $t^2$ — the integral over final states grows *linearly* in $t$, and the sinc² collapses onto $2\pi t\,\delta(E_f - E_i)$. Constant $dP/dt = \Gamma$. Amplitudes leaking into a continuum never rephase and return: that's the irreversibility.

**Fine print (all three needed):**
- genuine continuum (or quasi-continuum denser than $\hbar\Gamma$)
- weak coupling: $P \ll 1$ over the memory time
- intermediate times: $t$ long enough to resolve energy conservation, short before depletion. Violate the continuum condition (cavity!) and you get reversible vacuum Rabi oscillations back — the Purcell regime boundary.

Canonical outputs: spontaneous emission $\Gamma = \omega^3 d^2/3\pi\varepsilon_0\hbar c^3$ (vacuum-mode density × dipole element), photoionization rates, scattering cross-sections, off-resonant photon scattering in Raman gates.

> [!question]- Same atom, same dipole matrix element — why does putting it in a cavity change its decay rate?
> $\Gamma \propto \rho(E)$: the cavity restructures the density of photon modes at the transition frequency — enhanced on resonance (Purcell), suppressed off. The matrix element is untouched; the *continuum* is what you engineered.

# Connections

- [[Spontaneous Emission and Linewidth]] — FGR fed with vacuum-mode density
- [[Time-Dependent Perturbation Theory]] — the first-order amplitude this integrates over
- [[Dirac Delta]] — the $\delta(E_f - E_i)$ enforcing energy conservation in the continuum limit
- [[Purcell Effect]] — engineering $\rho(E)$ deliberately
- [[Density Matrix]] — where the resulting irreversible rates live as Lindblad terms

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §5.7
