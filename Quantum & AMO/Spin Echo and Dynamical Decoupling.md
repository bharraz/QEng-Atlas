#quantum #AMO

**A $\pi$ pulse at the midpoint time-reverses phase accumulation: whatever detuning was static over the sequence cancels exactly.** Dephasing from *slow* noise isn't decoherence, it's just bookkeeping you can undo — echoes are the undo.

# Reference

Hahn echo: $\tfrac{\pi}{2}$ — $\tau$ — $\pi$ — $\tau$ — $\tfrac{\pi}{2}$. A static offset $\delta$ winds $+\delta\tau$ before the $\pi$ and $-\delta\tau$ after (the flip negates accumulated phase): net zero, *independent of $\delta$*. Shot-to-shot field drift, thermal Doppler offsets, spatial inhomogeneity across a chain — all refocused.

**This is the $T_2^*$ vs $T_2$ distinction:** Ramsey decays at $T_2^*$ (includes quasi-static spread); echo removes the static part and decays at the true $T_2$, set by noise that *fluctuates within* the sequence. $T_2/T_2^*$ ratios of 10–100 are routine in field-noise-limited traps.

**Dynamical decoupling** = more $\pi$ pulses: CPMG ($N$ equally spaced $\pi$'s), XY-8 (phase-alternated, robust to pulse errors), UDD (optimized spacings). **Filter-function picture** — the clean way to think about all of them: a sequence multiplies the noise PSD by a filter $|F(\omega)|^2$; Ramsey is a low-pass (DC-sensitive), echo is a band-pass centered near $1/2\tau$ with DC blocked, CPMG-$N$ pushes the passband up to $\sim N/2\tau$. Coherence survives if the passband sits where $S(\omega)$ is quiet — which is why DD is devastating against $1/f$-type noise and useless against white noise.

**Costs:** each $\pi$ pulse contributes its own error (pulse-error accumulation caps useful $N$); DD also filters out any *signal* at DC — sensing sequences deliberately put the signal at the filter's passband instead.

> [!question]- Echo extends coherence 50× over Ramsey in your trap. What does that tell you about the noise spectrum?
> The dephasing is dominated by noise slow compared to the sequence — quasi-static field drift or line-synchronous pickup — which echo's DC-blocking filter removes. The remaining $T_2$ is set by spectral weight near $1/2\tau$; if bumping to CPMG keeps helping, the spectrum keeps falling with frequency ($1/f$-like).

# Connections

- [[Ramsey Interferometry]] — the base sequence being protected; echo = Ramsey + one $\pi$
- [[T1 and T2]] — echo is the operational definition of $T_2$ as opposed to $T_2^*$
- [[Flicker Noise]] — the $1/f$ spectra DD is built to defeat
- [[Rabi Oscillations]] — pulse fidelity limits how many $\pi$'s you can afford
- [[Reference Atlas/Math/Magnus Expansion]] — the design theory: sequences engineered so $\bar{H}^{(0)}$ (and, if time-symmetric, all odd orders) vanish

---
Source: Hahn, *Phys. Rev.* 80, 580 (1950)
