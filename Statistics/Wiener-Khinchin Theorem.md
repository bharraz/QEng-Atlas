#statistics #math

**The power spectral density is the Fourier transform of the autocorrelation function** — a random signal has no well-defined Fourier transform of its own, but its *correlations* do, and that's what a spectrum measures.

# Reference

For a wide-sense stationary process:

$$
S(f) = \int_{-\infty}^{\infty} R(\tau)\, e^{-i 2\pi f \tau}\, d\tau, \qquad R(\tau) = \int_{-\infty}^{\infty} S(f)\, e^{i 2\pi f \tau}\, df
$$

Immediate corollaries: $R(0) = \sigma^2 = \int S\,df$ (total power = variance), and short memory ↔ broad spectrum — $\tau_c$ and bandwidth are Fourier-reciprocal.

| $R(\tau)$ | $S(f)$ |
|---|---|
| $\delta(\tau)$ | white (flat) |
| $e^{-\|\tau\|/\tau_c}$ | Lorentzian, knee at $1/2\pi\tau_c$ |
| slow power-law decay | $1/f$-like |

**Stationarity is the fine print:** the theorem needs statistics that don't drift during the measurement. A drifting or aging signal has no honest $S(f)$ — this is exactly the regime where you switch to [[Allan Variance]].

**Why spectrum analyzers work:** the magnitude-squared FT of a finite record, $|{\tilde x}_T(f)|^2/T$ (the periodogram), converges *in expectation* to $S(f)$ — so averaging periodograms of successive records estimates the PSD. That's the entire license behind FFT-based noise measurement.

> [!question]- Why can't you just Fourier transform the noise signal directly and call it the spectrum?
> A stationary random signal doesn't decay, so its FT doesn't exist (doesn't converge), and any single finite-record periodogram has 100% variance — it never smooths with longer records. The stable, well-defined object is the FT of $\langle x(t)x(t+\tau)\rangle$; estimating it requires averaging.

# Connections

- [[Power Spectral Density]] — the object this theorem defines and legitimizes
- [[Autocorrelation]] — the time-domain half of the Fourier pair
- [[Fourier Transform]] — supplies the pair table (exponential ↔ Lorentzian etc.)
- [[PSD Estimation]] — Welch averaging is this theorem turned into practice

---
Source: Papoulis & Pillai, *Probability, Random Variables and Stochastic Processes* 4th ed., Ch. 10
