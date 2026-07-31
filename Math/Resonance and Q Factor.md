#math

**Q counts how many radians of oscillation you get before the energy is gone — equivalently, how narrow the resonance is compared to its center frequency.** Linewidth, ringdown time, and stored-vs-dissipated energy are three measurements of the same number.

# Reference

$$
Q = \frac{\omega_0}{\Delta\omega_{\mathrm{FWHM}}} = \omega_0\tau_E = 2\pi\,\frac{\text{energy stored}}{\text{energy dissipated per cycle}}
$$

$Q$ = dimensionless; $\omega_0$ = resonance frequency (rad/s); $\Delta\omega_{\text{FWHM}}$ = full width at half maximum of the *power* response (rad/s); $\tau_E$ = *energy* $1/e$ decay time (s); $\gamma$ = damping rate (s⁻¹). For $\ddot x + \gamma\dot x + \omega_0^2 x$: $Q = \omega_0/\gamma$, energy rings down as $e^{-\gamma t}$, amplitude as $e^{-\gamma t/2}$ — the factor-of-2 trap between field and power decay times.

All three expressions say the same thing because $Q$ is fundamentally *cycles of coherence*: multiply the middle form by $2\pi$ and it reads "radians of oscillation per $1/e$ of energy loss." Everything follows — a high-$Q$ resonator is simultaneously narrow, slow to respond, and efficient at storing energy, and you cannot have one without the others.

**Loaded vs unloaded:** $Q_0$ (unloaded) counts only the resonator's internal loss; $Q_L$ (loaded) includes power leaving through the coupling to your source/detector, $1/Q_L = 1/Q_0 + 1/Q_{\text{ext}}$. What a network analyzer or ringdown measures is $Q_L$; what the material can do is $Q_0$. Critical coupling ($Q_{\text{ext}} = Q_0$) halves the measured $Q$ and is often what you want for maximum power transfer — so a "degraded $Q$" after installing a probe may be correct coupling, not a worse resonator.

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
