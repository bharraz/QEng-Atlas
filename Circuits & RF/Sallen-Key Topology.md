#circuits #electronics

**Two poles from one op-amp and no inductors: an RC ladder whose midpoint gets a positive-feedback "bootstrap" through a capacitor from the output, propping the response up near cutoff to whatever Q you choose.**

# Reference

Unity-gain low-pass: series $R_1, R_2$ into the (+) input; $C_2$ from (+) input to ground; $C_1$ from the $R_1$–$R_2$ junction **to the output** (the bootstrap); output tied back to (−).

$$
f_0 = \frac{1}{2\pi\sqrt{R_1R_2C_1C_2}}, \qquad Q = \frac{\sqrt{R_1R_2C_1C_2}}{(R_1+R_2)C_2}
$$

With $R_1 = R_2$: $Q = \tfrac12\sqrt{C_1/C_2}$ — **set Q by the capacitor ratio**. Butterworth ($Q=0.707$): $C_1 = 2C_2$. Higher-order filters: cascade sections with staggered $f_0$, Q from the family tables.

**Why it won:** unity-gain follower = maximum bandwidth, no gain-resistor noise, gentle component sensitivities at low Q.

**Gotchas:**
- $Q \gtrsim 5$ gets component-sensitive — switch to a state-variable/biquad topology.
- Op-amp needs GBW ≫ 100·$f_0$, or the real poles shift and the response peaks.
- **The stopband comes back up:** beyond the op-amp's reach, signal sneaks through $C_1$ and the amp's rising output impedance — real SK low-passes flatten out ~40–60 dB down. Follow with a passive RC if a spectrum analyzer will ever look.

> [!question]- Your SK low-pass measures textbook out to 10× f₀, but 60 dB down the response flattens and then rises. Why?
> High-frequency feedthrough: past the op-amp's bandwidth its output impedance rises and the $C_1$ path bypasses the filter. Add a passive RC pole at the output to hold the stopband floor.

# Connections

- [[Filter Families]] — SK is the standard realization of those pole tables
- [[Op-Amp Golden Rules and Real Limits]] — the GBW and output-Z assumptions doing silent work
- [[Transfer Functions and Bode Plots]] — where the two-pole response and Q peaking show up

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §6.3
