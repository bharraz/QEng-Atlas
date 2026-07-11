#statistics #math

**Noise whose power density grows as $1/f$ toward low frequency — equal noise power per decade, and it never flattens out** — which is why every DC measurement eventually stops improving no matter how long you average.

# Reference

$$
S(f) \propto \frac{1}{f^{\alpha}}, \qquad \alpha \approx 0.8\text{–}1.2
$$

$\int S\, d f \propto \ln(f_2/f_1)$: **each decade of frequency contributes the same noise power** — the decade from 1 μHz to 10 μHz (your two-week drift) carries as much as 1 Hz to 10 Hz.

**Ubiquity, no single mechanism:** transistors, resistors, oscillator phase, magnetic fields, patch potentials on trap electrodes. The generic recipe: a broad distribution of relaxation times (many two-level fluctuators, each Lorentzian) superposes to $1/f$. It's a phenomenology, not a theory — measure it, don't derive it.

**Corner frequency** $f_c$: where $1/f$ crosses the white floor. Op-amps: ~1–100 Hz (bipolar low, CMOS high). Below $f_c$, longer averaging trades white noise for flicker and gains nothing.

**Why averaging stalls:** averaging time $T$ concentrates sensitivity on frequencies near $1/T$ — pushing $T$ up walks you *down* into rising $1/f$ noise. Variance of the mean $\to$ constant (the flicker floor in [[Allan Variance]]). **The escape is modulation:** chop or lock-in the measurement at $f_{\text{mod}} \gg f_c$, where the noise is white, then demodulate.

> [!question]- Averaging 100× longer used to shrink your error bars 10×; now it does nothing. What happened and what's the fix?
> The measurement band ($\sim 1/T$) dropped below the flicker corner — noise power per decade is constant there, so the variance of the mean plateaus. Fix: modulate the signal above $f_c$ (lock-in, chopping, interleaved reference) rather than average harder.

# Connections

- [[Allan Variance]] — the diagnostic: flicker is the flat floor, drift the upturn
- [[Amplifier Noise]] — the $1/f$ corner is a headline spec of every front end
- [[Lock-In Detection]] — the standard escape route to the white-noise region
- [[Autocorrelation]] — $1/f$ = long memory; correlations that never decay

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §8.1 (noise fundamentals)
