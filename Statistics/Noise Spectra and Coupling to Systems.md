#statistics #noise

**Noise is characterized by its power spectral density $S(\omega)$; the spectrum's shape identifies the physical mechanism generating it, and how a given system samples that spectrum — at DC, at a resonance frequency, or through a filter — determines what the noise does: drift, dephasing, or heating.** The three-step chain (mechanism → spectrum → coupling) is the template for analyzing any noise problem.

# Reference

## The mathematical objects

A noise process $x(t)$, assumed stationary (statistics independent of time origin), is characterized by its autocorrelation and its power spectral density, which are a Fourier pair (Wiener–Khinchin, [[Wiener-Khinchin Theorem]]):

$$R(\tau) = \langle x(t)\, x(t + \tau)\rangle, \qquad S(\omega) = \int_{-\infty}^{\infty} R(\tau)\, e^{-i\omega\tau}\, d\tau.$$

The correlation time (decay scale of $R$) and the spectral width are reciprocal. Total variance is the integral of the spectrum, $\sigma^2 = \frac{1}{2\pi}\int S(\omega)\, d\omega$ — a variance is always an integrated spectrum, and quoting one without stating the bandwidth is meaningless. Conventions to fix before any calculation: one-sided $S(f)$ vs two-sided $S(\omega)$ differ by a factor of 2 and a $2\pi$ ([[PSD Estimation]]); amplitude spectral density is $\sqrt{S}$, in units of $x/\sqrt{\mathrm{Hz}}$.

Two independent attributes beyond the spectrum: **Gaussianity** (a Gaussian process is fully specified by $S(\omega)$; non-Gaussian noise such as random telegraph noise is not — see below) and **stationarity** (drift is non-stationary noise; $1/f$ noise sits at the boundary, with divergent low-frequency weight).

## The colors and their origins

$S(\omega) \propto 1/\omega^{\alpha}$ over the band of interest:

| $\alpha$ | Name | $R(\tau)$ | Generating mechanism |
|---|---|---|---|
| 0 | white | $\propto \delta(\tau)$ | uncorrelated events: [[Shot Noise]] (Poisson arrivals), [[Johnson-Nyquist Noise]] (thermal), measurement/projection noise |
| 1 | pink, $1/f$ | logarithmic | broad distribution of activation rates (see below); [[Flicker Noise]] |
| 2 | Brownian / random walk | grows with $\tau$ | integrated white noise: $\dot{y} = x_{\text{white}}$; free-running oscillator phase, diffusion |
| $0 < \alpha < 2$, non-integer | $1/f^\alpha$ | power-law | partially integrated or distributed-rate processes; the empirically common case |

Two constructions generate most observed spectra:

**Lorentzian from a single fluctuator.** A two-state system switching at total rate $\gamma$ (a charge trap, an adsorbate reorienting, a bistable defect) has exponential correlations $R(\tau) \propto e^{-\gamma|\tau|}$ and therefore a Lorentzian spectrum:

$$S(\omega) \propto \frac{\gamma}{\gamma^2 + \omega^2}$$

— white below its knee at $\gamma$, $1/\omega^2$ above. A *single* strong fluctuator is also the canonical non-Gaussian case (random telegraph noise): visible as discrete jumps in the time trace and non-exponential decoherence.

**$1/f$ from an ensemble of fluctuators.** Superpose many Lorentzians with rates distributed as $p(\gamma) \propto 1/\gamma$ — the natural result of thermally activated processes with a flat distribution of barrier heights, $\gamma \propto e^{-E_b/k_BT}$ — and the knees smear into

$$S(\omega) = \int p(\gamma)\, \frac{\gamma}{\gamma^2 + \omega^2}\, d\gamma \;\propto\; \frac{1}{\omega}$$

over the band where fluctuators exist. Deviations from $\alpha = 1$ encode the barrier distribution: $p(\gamma) \propto \gamma^{-\beta}$ gives $\alpha = 2 - \beta$. This is why measured exponents are material- and surface-dependent and rarely exactly 1, and why a temperature dependence of $\alpha$ points to the activation spectrum. Integration also shifts exponents: a system responding to the *integral* of a noise multiplies $\alpha$ by adding 2 (frequency noise $\to$ phase noise).

**Divergences and their regularization.** $1/f^{\alpha \geq 1}$ diverges at low frequency: the variance depends on the observation time, growing as measurements lengthen. Standard deviation vs averaging time is then the honest statistic — the [[Allan Variance]], whose slopes map one-to-one onto $\alpha$ (white frequency noise: $\sigma_y \propto \tau^{-1/2}$; flicker: constant; random walk: $\tau^{+1/2}$) and which converges where the naive variance does not.

## How noise couples into a system

The system samples the spectrum; where it samples is set by the coupling mechanism.

**1. Linear, through a transfer function.** For noise entering an LTI system ([[Impulse and Frequency Response]]):

$$S_{\text{out}}(\omega) = |H(\omega)|^2\, S_{\text{in}}(\omega).$$

All filtering, servo suppression ($|H| = |S_{\text{loop}}|$ inside a lock's bandwidth — [[Control Beyond PID]]), and noise shaping is this single equation.

**2. Longitudinal coupling (frequency/phase noise → dephasing).** Noise $\delta\omega(t)$ in a transition frequency dephases a superposition; the accumulated phase variance under a pulse sequence with filter function $F$ is

$$\langle \Delta\phi^2 \rangle = \int \frac{d\omega}{\pi}\, S_{\delta\omega}(\omega)\, \frac{F(\omega T)}{\omega^2}$$

([[Noise Spectroscopy and Filter Functions]]). The spectrum's shape determines the decay law: quasi-static noise (weight at DC) gives Gaussian decay and a $T_2^*$ that depends on total averaging time; white noise gives exponential decay with $1/T_2 = \tfrac12 S_{\delta\omega}(0)$ (one-sided); fast noise beyond the correlation-time limit is motionally narrowed, $1/T_2 \approx \sigma^2 \tau_c$ — increasing the noise *rate* at fixed variance reduces dephasing. Echo and DD move the sampling frequency off DC, which is why they defeat $1/f$ specifically.

**3. Resonant (transverse) coupling → transitions and heating.** A perturbation $\delta V(t)$ coupling two levels drives transitions at a rate proportional to the noise density *at the transition frequency* (Fermi golden rule with the delta function broadened onto the noise spectrum — [[Fermi's Golden Rule]]):

$$\Gamma_{i \to f} = \frac{1}{\hbar^2}\, |\langle f|\hat{c}|i\rangle|^2\, S_V(\omega_{if}).$$

$T_1$ processes sample $S$ at the qubit frequency; only that single point of the spectrum matters. The trapped-ion instance: electric-field noise at the trap frequency drives the ion up the motional ladder at

$$\dot{\bar{n}} = \frac{e^2}{4 m \hbar \omega_t}\, S_E(\omega_t),$$

so the heating rate is a *single-frequency* measurement of $S_E$. Measured heating rates scale as $S_E \propto 1/\omega_t^{\alpha}$ with $\alpha \approx 0.5$–1.5 and as $d^{-4}$ in ion–electrode distance: the noise sampled at $\omega_t \sim$ MHz is not white, and both scalings implicate a dense ensemble of surface fluctuators (patch potentials, adsorbates — [[Surface Preparation and Cleaning]]) rather than Johnson noise from the electrodes, which would be flat in $\omega$ and scale as $d^{-2}$. Reading mechanism from the exponents $(\alpha, $ distance power, temperature dependence$)$ is precisely how the anomalous-heating literature proceeds.

**4. Parametric coupling → noise at harmonics of the motion.** Noise in a *parameter* of a Hamiltonian rather than an additive force samples at characteristic multiples: trap-frequency (spring-constant) fluctuations heat at $2\omega_t$ with rate $\propto \omega_t^2\, S_{\delta\omega_t/\omega_t}(2\omega_t)$ — the parametric-heating mechanism behind intensity-noise requirements in [[Optical Tweezers]] — while pointing noise enters at $\omega_t$ like a force. Identifying *which frequency a noise source must have* to matter is the fastest way to triage a suspected coupling.

**Diagnostic summary.** Measure the spectrum (directly, or through the system: heating rate vs $\omega_t$, DD noise spectroscopy, Allan deviation vs $\tau$); read $\alpha$ and the knees to identify the mechanism class; check the coupling type to know which spectral region matters; then either suppress the source, filter the path ($|H|^2$), or move the sampling frequency away from the noise (stiffer trap, DD, higher IF).

> [!question]- An ion trap's heating rate improves 100× on cooling the electrodes from 300 K to 4 K, but a Johnson-noise estimate predicts only ~75× from the resistance change. What does the discrepancy pattern actually establish?
> The near-agreement in magnitude is coincidental and the framing is inverted: Johnson noise is excluded not by the size of the temperature dependence but by the other exponents — the measured $S_E \propto 1/\omega^{\alpha}$ (Johnson noise from an electrode is flat at MHz frequencies) and the $d^{-4}$ distance scaling (Johnson fields fall as $d^{-2}$; a dense sheet of *uncorrelated microscopic* dipole-like sources gives $d^{-4}$). The strong temperature dependence then identifies thermally activated surface fluctuators, and its detailed form (often Arrhenius-like, sometimes with plateaus) constrains the activation-energy distribution — the same $p(E_b)$ that sets $\alpha$ in the $1/f^\alpha$ construction. Consistency between the temperature and frequency exponents is the test of the fluctuator model, not any single number.

# Connections

- [[Power Spectral Density]] / [[PSD Estimation]] — the central object and its measurement conventions
- [[Wiener-Khinchin Theorem]] — autocorrelation ↔ spectrum
- [[Flicker Noise]] — the $1/f$ case in depth
- [[Johnson-Nyquist Noise]] / [[Shot Noise]] — the two fundamental white floors
- [[Allan Variance]] — the statistic that survives divergent low-frequency noise
- [[Noise Spectroscopy and Filter Functions]] — dephasing as spectral overlap; measuring $S$ with a qubit
- [[Fermi's Golden Rule]] — transition rates sampling $S$ at the transition frequency
- [[Noise Coupling Mechanisms]] — the circuit-level entry paths (conducted, capacitive, inductive, radiated)
- [[Paul Traps]] — anomalous heating as the working example
- [[Lindblad Master Equation]] — the Markovian limit: valid when $S$ is flat across the system's linewidth

---
Source: Clerk et al., "Introduction to quantum noise, measurement, and amplification," *Rev. Mod. Phys.* 82, 1155 (2010); Brownnutt et al., "Ion-trap measurements of electric-field noise near surfaces," *Rev. Mod. Phys.* 87, 1419 (2015); Dutta & Horn, *Rev. Mod. Phys.* 53, 497 (1981) ($1/f$ from activated processes)
