#statistics #math

**How the variance of a noise signal is distributed over frequency** — integrate the PSD over a band and you get the mean-square fluctuation contributed by that band. The noise budget's native language.

# Reference

$$
S_x(f) = \lim_{T\to\infty}\frac{1}{T}\left\langle |\tilde{x}_T(f)|^2 \right\rangle, \qquad \sigma^2 = \int_{\text{band}} S_x(f)\, df
$$

$x(t)$ = the fluctuating quantity (V, T, Hz, rad — whatever you measure); $\tilde x_T(f)$ = its Fourier transform over a record of length $T$; $S_x$ = power spectral density in (units of $x$)²/Hz; $\sigma^2$ = mean-square fluctuation contributed by the integration band. The $1/T$ and the ensemble average are what make $S$ converge: $|\tilde x_T|^2$ alone grows with record length and fluctuates 100% shot to shot, so a *single* periodogram never converges no matter how long you measure — only averaging does ([[PSD Estimation]]).

**Units — where everyone gets burned:**
- **PSD**: $\mathrm{V^2/Hz}$ (power-like). **Amplitude spectral density**: $\sqrt{S}$ in $\mathrm{V/\sqrt{Hz}}$.
- Convert to rms: $v_{\text{rms}} = \sqrt{S \cdot B}$ for flat $S$ over bandwidth $B$ — e.g. $4\,\mathrm{nV/\sqrt{Hz}}$ over 1 MHz → 4 μV rms.
- **One- vs two-sided:** $S^{\text{1-sided}}(f) = 2\,S^{\text{2-sided}}(f)$ for $f > 0$ (fold negative frequencies onto positive). Instruments and datasheets quote one-sided; theory ($S_I = 2eI$, $S_V = 4k_BTR$ as written) is already one-sided. Mixing conventions silently costs a factor of 2 in power, $\sqrt{2}$ in amplitude.

**Common shapes:**

| Shape | $S(f)$ | Physical source |
|---|---|---|
| White | const | [[Johnson-Nyquist Noise]], shot noise |
| Flicker | $\propto 1/f$ | electronics, oscillators below the corner |
| Lorentzian | $\propto \frac{1}{1+(f/f_c)^2}$ | white noise through a 1-pole filter; exponential $R(\tau)$; two-level fluctuators |

> [!question]- A datasheet says $10\,\mathrm{nV/\sqrt{Hz}}$. What's the rms noise after a 10 kHz low-pass?
> $\sqrt{S \cdot B_{\text{eq}}}$ — with the filter's *equivalent noise bandwidth* ($\pi/2 \times f_{3\mathrm{dB}} \approx 15.7$ kHz for one pole): $10\,\mathrm{nV/\sqrt{Hz}} \times \sqrt{15.7\,\mathrm{kHz}} \approx 1.25\ \mu\mathrm{V}$ rms. (Using $B = f_{3\mathrm{dB}}$ underestimates ~11%.)

# Connections

- [[Wiener-Khinchin Theorem]] — the PSD's formal definition as FT of the autocorrelation
- [[Johnson-Nyquist Noise]] — the canonical white PSD with a number attached
- [[PSD Estimation]] — how to actually get $S(f)$ from sampled data without fooling yourself
- [[Allan Variance]] — the time-domain counterpart when drift makes $S(f)$ ill-defined near DC

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §8.1 (noise fundamentals)
