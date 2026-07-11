#statistics #math

**Averaging $N$ independent shots grows SNR as $\sqrt{N}$ — signal adds coherently, white noise adds in quadrature.** The catch is the word *independent*: 1/f noise and drift break it, and then more averaging buys nothing.

# Reference

For stationary white noise, $\sigma_{\text{mean}} = \sigma/\sqrt{N}$, so

$$
\mathrm{SNR}(N) = \sqrt{N}\,\cdot \mathrm{SNR}(1)
$$

Equivalent frequency-domain view: averaging time $T$ narrows the noise bandwidth as $1/T$; noise amplitude in-band falls as $\sqrt{1/T}$. Same $\sqrt{\phantom{x}}$, two languages. Every factor of 10 in SNR costs **100×** the data — averaging is a tax, not a strategy.

**When $\sqrt{N}$ fails:**
- **1/f noise:** once $1/T$ drops below the flicker corner, the noise entering your band stops thinning — SNR plateaus at the flicker floor ([[Flicker Noise]]).
- **Drift:** slow systematics grow with $T$; SNR eventually *degrades*. The [[Allan Variance]] curve is precisely the plot of where averaging stops paying and starts costing.
- **Correlated samples:** spacing closer than the correlation time gives $\sqrt{N_{\text{eff}}}$, not $\sqrt{N}$.

**The fixes are structural, not statistical:** move the measurement above the 1/f corner by modulation ([[Lock-In Detection]]), chop/interleave against a reference so drift becomes common-mode, and only then average. **Matched filtering one-liner:** weight the record by (template/noise PSD) — the optimal linear SNR for a known signal shape; simple averaging is the special case of a flat template in white noise.

> [!question]- Signal at DC, amplifier 1/f corner at 10 Hz. Averaging 1 s → 100 s gains you almost nothing. What's the 100× cheaper move?
> Modulate the signal at $\gtrsim$ a few × 10 Hz (chop the beam, dither the field) and demodulate with a lock-in: the measurement now happens in the white region, where $\sqrt{N}$ works again. Escaping 1/f beats fighting it with statistics.

# Connections

- [[Central Limit Theorem]] — the origin and fine print of the $\sqrt{N}$ law
- [[Allan Variance]] — the quantitative answer to "how long should I average"
- [[Lock-In Detection]] — the modulation escape from 1/f
- [[Flicker Noise]] — the noise that breaks the scaling
- [[Autocorrelation]] — $N_{\text{eff}}$ when samples aren't independent

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., Ch. 8 (low-noise techniques)
