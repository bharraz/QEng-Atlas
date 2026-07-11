#circuits #electronics

**One R and one C (or L) make a single pole: a gentle 20 dB/decade filter whose corner sits where the two impedance magnitudes are equal.**

# Reference

$$
f_c = \frac{1}{2\pi RC}\ \ (\text{RC}), \qquad f_c = \frac{R}{2\pi L}\ \ (\text{RL})
$$

Low-pass (series R, shunt C): $H = 1/(1+jf/f_c)$. **At $f_c$: −3 dB and −45°**; asymptotically −20 dB/dec and −90°. High-pass mirrors it. Anchor: 1 kΩ + 160 nF ≈ 1 kHz; scale from there.

**Asymptotic identities:** a low-pass well above $f_c$ integrates; a high-pass well below $f_c$ differentiates (AC coupling = differentiator for drift). Only in the asymptotes — near the corner it's neither.

**Loading — the classic gotcha:** the formulas assume a stiff source and light load. The source's output impedance adds in series with R (corner moves **down**); a load across C divides the passband and moves the corner **up**. Two RCs cascaded unbuffered do *not* give a clean two-pole response — the second loads the first (soft knee, shifted corners; for real 2nd order see [[Sallen-Key Topology]]). Keep ~10× impedance steps between stages, or buffer.

And remember −3 dB is barely attenuation: for real rejection the corner must sit a decade or more away, or you need more poles.

> [!question]- You built 1 kΩ + 160 nF for a 1 kHz corner but measure −3 dB at ~670 Hz. What did you forget?
> The source's ~500 Ω output impedance in series with the 1 kΩ: $f_c = 1/2\pi(R_s{+}R)C$. Corners are set by total impedances, not schematic values.

# Connections

- [[Complex Impedance]] — the voltage divider generating all of this
- [[Transfer Functions and Bode Plots]] — how the pole reads on a plot
- [[Filter Families]] — when one pole isn't enough
- [[Decoupling and Bypassing]] — the same RC idea applied to power rails

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §1.7
