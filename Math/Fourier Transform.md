#math

**The Fourier transform is the inner product of a signal with complex exponentials of every frequency: it maps a function of time to its frequency content.** Most transforms encountered in practice can be written down by inspection, because every signal decomposes into a small set of standard pairs combined through a small set of operations. The Laplace and Z-transforms below are the same construction with a generalized basis function.

# Reference

**Relation to the Fourier series.** A $T_p$-periodic signal expands on harmonics of $F_0 = 1/T_p$:

$$x(t) = \sum_{k=-\infty}^{\infty} c_k\, e^{i2\pi k F_0 t}, \qquad c_k = \frac{1}{T_p}\int_{T_p} x(t)\, e^{-i2\pi k F_0 t}\, dt.$$

For an aperiodic signal, take $T_p \to \infty$: the harmonic spacing $F_0 \to 0$, the coefficients become a density $c_k \to X(f)\,df$, and the sum becomes an integral:

$$X(f) = \int_{-\infty}^{\infty} x(t)\, e^{-i2\pi f t}\, dt, \qquad x(t) = \int_{-\infty}^{\infty} X(f)\, e^{i2\pi f t}\, df.$$

Series for periodic signals (discrete spectrum at the harmonics); transform for aperiodic signals (continuous spectrum).

**Conventions.** The $f$-form above is symmetric. In angular frequency: $\tilde f(\omega) = \int f e^{-i\omega t} dt$ with $\frac{1}{2\pi}$ on the inverse, or $1/\sqrt{2\pi}$ on each. Spatial convention uses the opposite sign, $e^{+i\mathbf k \cdot \mathbf r - i\omega t}$, so that this phase describes a forward-propagating wave. State the convention in any calculation; mismatched $2\pi$'s are the most common error.

**Existence (Dirichlet conditions):** finitely many finite discontinuities, finitely many extrema, absolutely integrable. Signals violating the last condition (pure tones, periodic signals) are handled distributionally via delta functions.

**Interpretation.** $X(f)$ is complex: $X = |X|\,e^{i\angle X}$. The magnitude $|X(f)|$ is the amplitude density at frequency $f$ (units of signal amplitude per Hz); the phase $\angle X(f)$ is the phase of that component relative to $t = 0$ — substituting the polar form into the inverse transform shows each sinusoid entering with exactly this offset. Magnitude and phase carry independent information: a transform-limited pulse and broadband noise can have the same $|X|$; they differ in the phase spectrum.

## Standard pairs

| $x(t)$ | $X(\omega)$ | Notes |
|---|---|---|
| $e^{-t^2/2\sigma^2}$ | $\propto e^{-\sigma^2\omega^2/2}$ | Gaussian ↔ Gaussian; widths reciprocal |
| $e^{-t/\tau}\,\Theta(t)$ | $\dfrac{\tau}{1 + i\omega\tau}$ | one-sided exponential ↔ Lorentzian; FWHM of $\|X\|^2$ is $2/\tau$ |
| $\mathrm{rect}(t/T)$ | $T\,\mathrm{sinc}(\omega T/2)$ | rectangular pulse ↔ sinc; zeros at $\omega = 2\pi n/T$ |
| $\delta(t)$ | $1$ | impulse ↔ flat spectrum |
| $e^{i\omega_0 t}$ | $2\pi\,\delta(\omega - \omega_0)$ | pure tone ↔ single line |
| $\sum_n \delta(t - n t_0)$ | $\frac{2\pi}{t_0}\sum_k \delta\big(\omega - \frac{2\pi k}{t_0}\big)$ | impulse train ↔ impulse train (self-dual) |

General regularity correspondence: smoothness in one domain ↔ rapid decay in the other. Discontinuities produce $1/\omega$ tails (sinc sidelobes); a discontinuous derivative produces $1/\omega^2$; a Gaussian, smooth at every order, decays faster than any power.

## Properties

| Time domain | Frequency domain |
|---|---|
| $x(t - t_0)$ | $e^{-i\omega t_0}\, X(\omega)$ |
| $e^{i\omega_0 t}\, x(t)$ | $X(\omega - \omega_0)$ |
| $x(t)\, y(t)$ | $\frac{1}{2\pi}\,(X * Y)(\omega)$ |
| $(x * y)(t)$ | $X(\omega)\, Y(\omega)$ |
| $\dot{x}(t)$ | $i\omega\, X(\omega)$ |
| $x(at)$ | $\frac{1}{\|a\|}\, X(\omega/a)$ |
| $x(t)$ real | $X(-\omega) = X^*(\omega)$ |

Physical identifications: time shift = linear phase (delay leaves $|X|$ unchanged); multiplication by a tone = spectral shift (mixing, modulation sidebands — [[Mixers]], [[Sideband Spectrum of Modulated Light]]); convolution ↔ multiplication is the basis of filtering and of every LTI system ([[Impulse and Frequency Response]], [[Convolution]]); the derivative property is why differentiation amplifies high frequencies and integration suppresses them.

## Computing transforms by inspection

Decompose the signal as products and convolutions of standard pairs, then apply the tables term by term:

- **Decaying oscillation** $e^{i\omega_0 t}\,e^{-t/\tau}\Theta(t)$: tone × exponential decay → line convolved with Lorentzian = Lorentzian centered at $\omega_0$, FWHM $2/\tau$. This is the natural-linewidth mechanism ([[Laser Linewidth]], [[Spontaneous Emission and Linewidth]]).
- **Finite pulse of carrier** (tone × rectangular envelope): line convolved with sinc = sinc centered at the carrier, main lobe width $\sim 1/T$, sidelobes decaying as $1/\Delta\omega$ (first sidelobe −13 dB). The excitation profile of a square pulse; replacing the rectangular envelope with a Gaussian removes the sidelobes because the Gaussian pair has no power-law tails — the basis of pulse shaping for off-resonant crosstalk suppression.
- **Finite observation window**: any signal measured for duration $T$ is (signal) × (rect), so the measured spectrum is the true spectrum convolved with a sinc of width $\sim 1/T$ — the origin of the Fourier resolution limit and of spectral leakage ([[FFT in Practice]]).
- **Amplitude modulation** $x(t)(1 + m\cos\omega_m t)$: the spectrum acquires copies at $\pm\omega_m$ (sidebands).

**Pulse trains and frequency combs.** A train of identical pulses spaced by $t_0$ is (single pulse) ∗ (impulse train), so the spectrum is (single-pulse envelope) × (impulse train in frequency):

$$X_{\text{tot}}(\omega) = X_{\text{pulse}}(\omega)\sum_n e^{-in\omega t_0} \;\longrightarrow\; X_{\text{pulse}}(\omega)\,\frac{2\pi}{t_0}\sum_k \delta\!\left(\omega - \frac{2\pi k}{t_0}\right).$$

The phase sum cancels except where all pulses add in phase ($\omega t_0 = 2\pi k$), leaving discrete lines spaced by the repetition rate $2\pi/t_0$ under the single-pulse envelope. For a finite train of $N$ pulses each line has width $\sim 1/(N t_0)$ — the total observation time, consistent with the windowing rule above. See [[Frequency Combs]]. Pairs of comb lines separated by $m$ repetition rates provide difference frequencies for driving transitions (e.g. a hyperfine qubit via stimulated [[Raman Transitions]]); the remaining non-resonant line pairs contribute AC Stark shifts.

**Parseval / Plancherel.** Energy is preserved between domains:

$$\int_{-\infty}^{\infty} |x(t)|^2\, dt = \int_{-\infty}^{\infty} |X(f)|^2\, df; \qquad \text{periodic case: } \frac{1}{T_p}\int_{T_p}|x|^2\,dt = \sum_k |c_k|^2.$$

(Periodic signals have finite power, not finite energy; the series version is stated in power.) Practical consequence: the PSD integrates to the variance ([[Power Spectral Density]]).

**Time–bandwidth inequality:** $\Delta t\, \Delta\omega \geq \tfrac12$ (RMS widths; Gaussian saturates it). All resolution limits of the form "a measurement of duration $T$ cannot resolve features narrower than $1/T$" are instances; shape-dependent constants and the full set of bandwidth definitions are in [[Bandwidth]].

## Laplace and Z-transforms

**Laplace transform** — replace the pure oscillation with a general complex exponential, $s = \sigma + i\omega$:

$$X(s) = \int_0^\infty x(t)\, e^{-st}\, dt.$$

The Fourier transform is the restriction to $s = i\omega$. The additional real part gives convergence for signals that are not absolutely integrable (steps, ramps, growing transients), incorporates initial conditions in the one-sided form ($\dot x \to sX - x(0)$), and introduces the pole structure: a pole at $s = p$ corresponds to a mode $e^{pt}$ in the system. Poles in the left half-plane are decaying (stable), right half-plane growing (unstable); the real part is the decay rate and the imaginary part the oscillation frequency. Stability analysis of circuits and control loops is pole placement in the $s$-plane ([[Laplace Transform]], [[Transfer Functions and Bode Plots]], [[Stability and Phase Margin]]). The Fourier transform, confined to the imaginary axis, cannot represent transient growth or decay of modes.

**Z-transform** — the discrete-time counterpart. For a sampled sequence $x[n]$ with sample period $T_s$:

$$X(z) = \sum_n x[n]\, z^{-n}, \qquad z = e^{sT_s}.$$

The map $z = e^{sT_s}$ takes the imaginary axis of the $s$-plane to the unit circle: evaluating $X(z)$ on the unit circle gives the discrete-time Fourier transform, periodic in the sampling frequency (aliasing corresponds to the map being many-to-one — [[Sampling and Aliasing]]). Stability: poles inside the unit circle. A unit delay is $z^{-1}$ ($x[n-1] \leftrightarrow z^{-1}X$), so any difference equation becomes a rational function of $z$; digital filter design is pole and zero placement inside the unit circle ([[Digital Filters]]), and discrete-time loop delay enters servo analysis as a factor $z^{-k}$ ([[Control Beyond PID]]).

Summary of the three: the Fourier transform gives the frequency content of a signal; the Laplace transform gives the exponential modes of a continuous-time system, with stability as pole location relative to the imaginary axis; the Z-transform does the same for sampled systems, with stability as pole location relative to the unit circle.

> [!question]- By inspection: what is the spectrum of a 10 µs rectangular pulse of a 100 MHz carrier, and how does it change with a Gaussian envelope of the same duration?
> Tone × rect → line ∗ sinc: a sinc centered at 100 MHz with main lobe ~200 kHz wide (null-to-null $2/T$) and sidelobes decaying as $1/\Delta\omega$, the first at −13 dB — significant off-resonant excitation hundreds of kHz from the carrier. With a Gaussian envelope: line ∗ Gaussian — comparable width near the center, but the tails fall as a Gaussian and the sidelobes are absent. The difference between the two envelope entries in the standard-pairs table is the entire content of pulse shaping for crosstalk suppression.

# Connections

- [[Fourier Series]] — the periodic case; the transform is its continuum limit
- [[Convolution]] — the multiplication–convolution duality in full
- [[Laplace Transform]] — the $s$-plane: transients, initial conditions, pole analysis
- [[Digital Filters]] / [[Sampling and Aliasing]] — the Z-transform in use
- [[Impulse and Frequency Response]] — LTI systems and the convolution theorem
- [[Power Spectral Density]] — $|X|^2$ per unit time, the measured quantity
- [[Bandwidth]] — the time–bandwidth inequality across domains
- [[FFT in Practice]] — the discrete numerical version; leakage and windowing
- [[Frequency Combs]] — the pulse-train pair as an instrument
- [[Dirac Delta]] — the distributional pairs

---
Source: Bracewell, *The Fourier Transform and Its Applications*, Ch. 4–6; Oppenheim & Willsky, *Signals and Systems*, Ch. 4, 9–10; Proakis & Manolakis, *Digital Signal Processing*, Ch. 3–4
