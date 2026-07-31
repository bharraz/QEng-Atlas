#quantum #AMO

**A $\pi$ pulse at the midpoint time-reverses phase accumulation: whatever detuning was static over the sequence cancels exactly.** Dephasing from *slow* noise isn't decoherence, it's just bookkeeping you can undo — echoes are the undo.

# Reference

Hahn echo: $\tfrac{\pi}{2}$ — $\tau$ — $\pi$ — $\tau$ — $\tfrac{\pi}{2}$. A static offset $\delta$ winds $+\delta\tau$ before the $\pi$ and $-\delta\tau$ after (the flip negates accumulated phase): net zero, *independent of $\delta$*. Shot-to-shot field drift, thermal Doppler offsets, spatial inhomogeneity across a chain — all refocused.

**This is the $T_2^*$ vs $T_2$ distinction:** Ramsey decays at $T_2^*$ (includes quasi-static spread); echo removes the static part and decays at the true $T_2$, set by noise that *fluctuates within* the sequence. $T_2/T_2^*$ ratios of 10–100 are routine in field-noise-limited traps.

**Dynamical decoupling** = more $\pi$ pulses. **Filter-function picture** — the clean way to think about all of them: the pulse train defines a modulation $y(t) = \pm1$ (sign flipping at each $\pi$), the sequence multiplies the noise PSD by $|F(\omega)|^2 = |\mathcal{F}\{y\}|^2$, and coherence survives if that passband sits where $S(\omega)$ is quiet. Ramsey is a low-pass (DC-sensitive), echo blocks DC with a band-pass near $1/2\tau$, and CPMG-$N$ pushes the passband to $\sim N/2\tau$. This is why DD is devastating against $1/f$-type noise and useless against white noise, which has nowhere quiet to move to.

**$y(t)$ is a window and $F(\omega)$ is its transform** ([[Window Functions and Apodization]]), so sequence design is window design and inherits the same trade: pushing the passband higher (more pulses) narrows what you reject, while shaping the *spacing* is exactly what a taper does for a spectral window.

| Sequence | Structure | Passband | Buys | Costs |
|---|---|---|---|---|
| Hahn echo | single $\pi$ at $T/2$ | $\sim 1/2\tau$ | removes quasi-static noise | one filter notch only |
| CPMG | $N$ equally spaced $\pi$'s | $\sim N/2\tau$, odd harmonics | $T_2 \propto N^{2/3}$ for $1/f$ | pulse errors accumulate; only protects one axis |
| XY-4 / XY-8 | phase-alternated $\pi_x, \pi_y$ | same as CPMG | protects both transverse axes; cancels pulse errors to first order | longer, more pulses |
| UDD | non-uniform spacing $t_j \propto \sin^2\!\big(\tfrac{\pi j}{2N+2}\big)$ | sharp high-frequency cutoff | optimal against a hard spectral edge | worse than CPMG for soft $1/f$ spectra |
| KDD | composite $\pi$ pulses | as CPMG | robust to amplitude *and* detuning error | substantially more pulse area |

Choosing between them is a spectral question, not a preference: CPMG for smoothly falling $1/f$-like noise, UDD when the bath has a sharp cutoff above which there is nothing, XY-8/KDD whenever pulse imperfection rather than bath noise is the limiting error.

**Costs:** each $\pi$ pulse contributes its own error, so accumulated pulse infidelity caps useful $N$ (the optimum is where per-pulse error equals the coherence gained). DD also filters out any *signal* at DC — sensing sequences turn this around and place the signal *at* the passband instead ([[Noise Spectroscopy and Filter Functions]]).

> [!question]- Echo extends coherence 50× over Ramsey in your trap. What does that tell you about the noise spectrum?
> The dephasing is dominated by noise slow compared to the sequence — quasi-static field drift or line-synchronous pickup — which echo's DC-blocking filter removes. The remaining $T_2$ is set by spectral weight near $1/2\tau$; if bumping to CPMG keeps helping, the spectrum keeps falling with frequency ($1/f$-like).

# Connections

- [[Ramsey Interferometry]] — the base sequence being protected; echo = Ramsey + one $\pi$
- [[T1 and T2]] — echo is the operational definition of $T_2$ as opposed to $T_2^*$
- [[Flicker Noise]] — the $1/f$ spectra DD is built to defeat
- [[Rabi Oscillations]] — pulse fidelity limits how many $\pi$'s you can afford
- [[Reference Atlas/Math/Magnus Expansion]] — the design theory: sequences engineered so $\bar{H}^{(0)}$ (and, if time-symmetric, all odd orders) vanish
- [[Window Functions and Apodization]] — $y(t)$ as a window; the same main-lobe/sidelobe trade as spectral analysis
- [[Noise Spectroscopy and Filter Functions]] — running the filter picture backwards to measure $S(\omega)$

---
Source: Hahn, *Phys. Rev.* 80, 580 (1950)
