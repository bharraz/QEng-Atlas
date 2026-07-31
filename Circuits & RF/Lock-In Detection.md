#circuits #electronics

**Modulate what you measure, multiply the detector output by the reference, low-pass the product: the signal at $f_\text{mod}$ lands at DC while noise everywhere else averages away — a DC measurement relocated to a quiet spectral neighborhood, out of the 1/f swamp.**

# Reference

Signal $A\cos(\omega_m t + \phi)$ × reference $\cos\omega_m t$ → LPF ⇒ $\tfrac{A}{2}\cos\phi$. Dual-phase instruments multiply by 0° and 90° references: $X, Y \to R = \sqrt{X^2+Y^2},\ \theta$ — magnitude immune to phase drift.

**Why it wins:** the detection bandwidth is the output low-pass bandwidth, but *centered at* $f_\text{mod}$ rather than at DC — demodulation slides the passband up to a quiet part of the spectrum. Time constant $\tau$ (s) → equivalent noise bandwidth $\mathrm{ENBW} = 1/4\tau$ (Hz) for a one-pole filter (the 4 is the π/2 ENBW correction combined with the two-sided passband folding onto one). $\tau = 1$ s admits 0.25 Hz of noise around, say, 10 kHz, where the detector floor is white instead of 1/f. Higher-order output filters shrink ENBW toward $1/8\tau$, $1/12\tau$ — check which the instrument uses before converting a reading to a noise density.

**Choosing $f_\text{mod}$:** above the 1/f corner of detector + amplifier (kHz and up), inside the detector bandwidth, and never near n×50/60 Hz — odd frequencies like 517 Hz exist for exactly this reason.

**Gotchas:**
- Output ∝ cos φ — set the phase, or use R (but R rectifies noise: biased estimate at low SNR)
- A square-wave reference also demodulates odd harmonics of $f_\text{mod}$ (weights 1/n) — keep interference off 3f, 5f
- $\tau$ sets settling: wait ~5τ per point or the scan smears

Same mathematics as [[Mixers]], run at audio frequencies with 24-bit dynamic range.

> [!question]- Why does chopping a beam at 1 kHz make nW visible on a photodiode that shows nothing at DC — same detector, same light?
> At DC the signal hides under 1/f noise and drift; chopped, it lives at 1 kHz where the floor is white, and the lock-in's ~0.1 Hz ENBW admits orders of magnitude less noise power than any DC measurement of comparable speed.

# Connections

- [[Mixers]] — the multiplication core, RF edition
- [[Flicker Noise]] — the enemy this technique outflanks rather than fights
- [[SNR and Averaging]] — the ENBW arithmetic, and when longer averaging stops paying
- [[Pound-Drever-Hall Locking]] — the same modulate-demodulate move at optical speed

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §8.14
