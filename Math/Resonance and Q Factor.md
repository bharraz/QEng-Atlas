#math

**Q counts how many radians of oscillation you get before the energy is gone — equivalently, how narrow the resonance is compared to its center frequency.** Linewidth, ringdown time, and stored-vs-dissipated energy are three measurements of the same number.

# Reference

$$
Q = \frac{\omega_0}{\Delta\omega_{\mathrm{FWHM}}} = \omega_0\tau_E = 2\pi\,\frac{\text{energy stored}}{\text{energy dissipated per cycle}}
$$

where $\tau_E$ is the *energy* $1/e$ decay time. For the damped oscillator $\ddot x + \gamma\dot x + \omega_0^2 x$: $Q = \omega_0/\gamma$, energy rings down as $e^{-\gamma t}$, amplitude as $e^{-\gamma t/2}$ — factor-of-2 gotcha between field and power decay times.

**Lineshape:** the driven response power is Lorentzian, FWHM $\gamma = \omega_0/Q$. Narrow line ↔ long ringdown is just the Fourier pair; measure whichever is experimentally easier (ringdown wins for high Q, where the line is too narrow to scan).

**The many faces:**

| System | $Q$ | loss mechanism | typical values |
|---|---|---|---|
| Mechanical | $\omega_0/\gamma$ | friction, clamping | $10^3$–$10^8$ (Si resonators) |
| Series RLC | $\omega_0 L/R = \frac{1}{R}\sqrt{L/C}$ | resistance | 10–100 (lumped), $10^4$ (cavity) |
| Optical cavity | $\omega/\kappa = 2\pi\nu\,\tau_E$ | mirror transmission/loss | $10^6$–$10^{10}$ |
| Atomic transition | $\omega/\Gamma$ | spontaneous emission | $10^7$ (dipole), $10^{15}$+ (clock) |

For cavities, finesse $\mathcal{F} = \mathrm{FSR}/\Delta\nu$ is the per-round-trip version; $Q = \mathcal{F}\cdot\nu/\mathrm{FSR}$ — finesse rates the mirrors, Q rates the resonance.

> [!question]- A cavity's field ringdown time constant is $\tau$. What is Q, and where does the factor of 2 hide?
> Energy decays twice as fast as field: $\tau_E = \tau/2$, so $Q = \omega_0\tau/2$. Quoting a ringdown without saying field-or-power is the classic way to be wrong by 2× — same trap as one-sided vs two-sided PSDs.

# Connections

- [[Driven Damped Harmonic Oscillator]] — the equation Q parameterizes; Lorentzian response derived there
- [[Fabry-Perot Cavity]] — finesse vs Q, FSR, and buildup in the optical incarnation
- [[LC Resonators]] — the circuit face: bandwidth $f_0/Q$, tank impedance transformation
- [[Spontaneous Emission and Linewidth]] — an atom is a Q~$10^7$ oscillator; natural linewidth is its $\omega_0/Q$
- [[Bandwidth]]
---
Source: Feynman Lectures I, Ch. 23–24 (Resonance; Transients)
