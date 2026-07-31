#reference #units

**Most wrong answers in this field are not conceptual — they are a factor of 2, 2π, or √2 imported from a source using a different convention.** This page collects every such trap in the vault, each with the disambiguating question to ask before trusting a number.

# Reference

## Frequency: ω or f

$\omega = 2\pi f$. Rabi frequencies, detunings, linewidths, and trap frequencies are all quoted both ways.

- **The tell:** a quantity written $\Omega$ is usually angular (rad/s); the same quantity written $\Omega/2\pi$ is in Hz. Papers write "$\Omega/2\pi = 1$ MHz" precisely to disambiguate — read the $/2\pi$ as part of the name.
- π-pulse time is $\pi/\Omega$, *not* $1/2f$: with $\Omega/2\pi = 1$ MHz, $t_\pi = 0.5$ µs.
- An error of ~6× means one missing $2\pi$; ~40× means two.
- **Ask:** does this formula's exponential read $e^{i\omega t}$ or $e^{i2\pi f t}$?

## Amplitude or power

The single most common source of factor-2 errors, appearing in five disguises:

| Context | Amplitude quantity | Power quantity | Relation |
|---|---|---|---|
| Decibels | $20\log_{10}$ | $10\log_{10}$ | dB value identical, definition differs |
| Cavity/resonator decay | field decays at $\kappa/2$ | energy decays at $\kappa$ | $\tau_{\text{field}} = 2\tau_E$ |
| Damped oscillator | $e^{-\gamma t/2}$ | $e^{-\gamma t}$ | $Q = \omega_0/\gamma$ uses *energy* |
| Qubit coherence | $T_2$ (coherence amplitude) | $T_1$ (population) | $1/T_2 = 1/2T_1 + \gamma_\varphi$ |
| Input-output | $\sqrt{\kappa}\,a$ | $\kappa\, a^\dagger a$ | $\sqrt\kappa$ converts number to flux |

**Ask:** is the decaying thing a field/coherence/amplitude, or an energy/population/intensity? Quoting "a ringdown of $\tau$" without saying which is the classic way to be wrong by 2×.

## Linewidths and widths

- **FWHM vs HWHM vs $1/e$ vs $1/e^2$ vs RMS.** Gaussian: FWHM $= 2\sqrt{2\ln 2}\,\sigma = 2.355\sigma$. Beam waists $w$ are $1/e^2$ *intensity* radii ($= 2\sigma$ of the field's Gaussian). Lorentzian FWHM $= \Gamma$ in angular units, $\Gamma/2\pi$ in Hz.
- **Natural linewidth**: $\Gamma$ is a rate (s⁻¹); the observable linewidth is $\Gamma/2\pi$ (Hz). "Γ/2π = 21.6 MHz" for Ca⁺ means $\Gamma = 1.36\times10^8$ s⁻¹.
- **Bandwidth definitions** — 3-dB, null-to-null, RMS, and ENBW all differ; see [[Bandwidth]] for the table. Never carry one into a formula expecting another.

## Noise densities

- **One-sided vs two-sided PSD:** $S^{\text{1-sided}}(f) = 2S^{\text{2-sided}}(f)$ for $f > 0$. Instruments and datasheets are one-sided; theory papers are often two-sided. $S_V = 4k_BTR$ and $S_I = 2eI$ as normally written are already one-sided.
- **Per Hz or per rad/s:** $S(\omega) = S(f)/2\pi$. A spectral density quoted against angular frequency is smaller by $2\pi$.
- **Density vs integrated:** V/√Hz is a *density* and means nothing until multiplied by $\sqrt{B}$. The $B$ must be the **equivalent noise bandwidth**, not the 3-dB point: ENBW $= (\pi/2)f_{3\text{dB}}$ for one pole (i.e. $1/4\tau$), approaching $f_{3\text{dB}}$ for steep filters.
- **Ask:** one- or two-sided; per Hz or per rad/s; amplitude ($\sqrt{S}$) or power ($S$).

## Quantum-optics and AMO specifics

- **Quadrature normalization:** $X = (a + a^\dagger)/2$ gives vacuum $\Delta X = 1/2$; $X = (a+a^\dagger)/\sqrt2$ gives $\Delta X = 1/\sqrt2$; some texts set vacuum variance to 1. Squeezing in dB is unambiguous ($-10\log_{10}$ of the variance ratio); absolute variances are not.
- **Lindblad operators carry $\sqrt{\text{rate}}$:** $L = \sqrt{\Gamma}\,\sigma_-$, so $L^\dagger L$ is a rate. Writing $L = \Gamma\sigma_-$ squares the error.
- **Cooperativity** $C = g^2/\kappa\Gamma$ appears with 2 and 4 in the denominator across papers; $F_P = 2C$ only in the convention used here.
- **Saturation parameter** $s_0 = 2\Omega^2/\Gamma^2 = I/I_{\text{sat}}$ — some texts define $s$ including the detuning, others not.
- **Clebsch–Gordan / Wigner–Eckart:** the reduced matrix element is defined with or without a $\sqrt{2j'+1}$ depending on the text ([[Wigner-Eckart Theorem]]); Condon–Shortley phase makes the coefficients real but sign conventions still differ.
- **Landau–Zener:** $P_{LZ}$ may be quoted for the diabatic *or* adiabatic outcome, and $\hbar\Omega$ may be the full gap or half of it.

## Electrical

- **dBm into what:** 0 dBm = 1 mW, but the corresponding voltage (224 mV rms) assumes 50 Ω. Into 1 MΩ the same dBm means something else entirely.
- **Vpp, Vrms, Vamplitude:** sine wave $V_{\text{rms}} = V_{\text{pp}}/2\sqrt2 = 0.354\,V_{\text{pp}}$. Function generators usually display Vpp *into 50 Ω* and deliver twice that into an open circuit.
- **Reflection:** $\Gamma$ is an amplitude ratio; return loss $= -20\log|\Gamma|$; reflected *power* is $|\Gamma|^2$.
- **Q loaded vs unloaded:** a measured $Q$ includes coupling; $1/Q_L = 1/Q_0 + 1/Q_{\text{ext}}$ ([[Resonance and Q Factor]]).

## Solid state and fab

- **Lattice constants:** conventional cubic cell vs primitive cell — "the lattice constant of silicon is 5.43 Å" is the conventional cube, not the nearest-neighbour distance (2.35 Å).
- **Scherrer $\beta$ must be in radians**, with instrumental broadening subtracted; $K = 0.9$ is itself shape-dependent.
- **Etch selectivity** may be quoted film-vs-mask or film-vs-underlayer — different numbers, same word.
- **Sound velocity in AO devices:** longitudinal vs slow-shear mode differ by ~7× in the same crystal ([[Acousto-Optic Modulator]]).

## Statistics

- **Reduced χ² divides by $\nu = N - p$**, not $N$.
- **Standard error vs standard deviation:** $\sigma/\sqrt N$ vs $\sigma$.
- **Allan deviation is a curve**, and its $\tfrac12$ prefactor exists so it matches the variance of the mean for white noise ([[Allan Variance]]).
- **Confidence level:** $z = 1$ is 68%, not 95% — and near $p = 0$ or $1$ the Gaussian interval is simply wrong ([[Binomial Errors in State Detection]]).

> [!question]- A paper reports a cavity with "linewidth 1 MHz" and you need the field decay rate for a simulation. What do you need to resolve first?
> Three things, each a factor: (1) is 1 MHz the FWHM in Hz or an angular rate — if FWHM, then $\kappa = 2\pi\times10^6$ s⁻¹; (2) is their $\kappa$ the energy decay rate or the field decay rate — the field amplitude decays at $\kappa/2$; (3) for a two-sided cavity, is this the total loss or one mirror's contribution. Getting all three wrong is a factor of 8. The safe move is to find a *time* in the paper (ringdown, photon lifetime) and check consistency against the stated linewidth.

# Connections

- [[Units and Dimensional Analysis]] — the conversion sheet these conventions decorate
- [[Bandwidth]] — the full table of bandwidth definitions
- [[Power Spectral Density]] / [[PSD Estimation]] — noise density conventions in depth
- [[dB Conventions]] — the logarithmic bookkeeping
- [[Resonance and Q Factor]] — energy vs amplitude decay, loaded vs unloaded
- [[Fourier Transform]] — where the $2\pi$ choices originate

---
Source: assembled from the conventions noted across this vault; Heinzel et al., "Spectrum and spectral density estimation by the DFT" for the noise-scaling conventions
