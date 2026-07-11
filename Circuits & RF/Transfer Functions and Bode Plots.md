#circuits #electronics

**H(ω) = output/input as a complex function of frequency; the Bode plot is its log-frequency magnitude (dB) and phase, where poles and zeros become straight-line slopes you can read by eye.**

# Reference

$$
H(s) = K\,\frac{\prod_i (s-z_i)}{\prod_j (s-p_j)}, \qquad s = j\omega
$$

**Slope rules:** each pole past its corner adds **−20 dB/decade and −90° of phase**; each zero, +20 dB/dec and +90°. Magnitude changes are local (−3 dB at the corner); phase is smeared over ~2 decades centered there (−45° at the corner itself) — phase arrives *before* the magnitude drop, which is exactly what bites feedback loops.

**Reading a plot:** find the flat in-band gain, then count slope changes: −20 dB/dec → one pole, −40 → two; each corner sits at the −3 dB point of its pole.

Cascade = multiply $H$'s = **add dB and add phases** — valid only if stages don't load each other (buffer or keep ~10× impedance steps).

**Why phase matters more than it looks:** stability of any feedback loop is decided by the phase where loop gain crosses unity, not by magnitude — see [[Stability and Phase Margin]].

> [!question]- A Bode magnitude falls at −40 dB/dec above 1 kHz. What is the asymptotic phase, and name a circuit that does this.
> Two poles → −180° asymptotically. Any second-order low-pass: Sallen-Key, series LC into a load, two buffered RCs.

# Connections

- [[Laplace Transform]] — $H(s)$ lives there; poles = natural response, $s=j\omega$ = steady state
- [[Stability and Phase Margin]] — loop-gain Bode plots are how you check feedback won't sing
- [[RC and RL Filters]] — the single-pole prototype whose corner you read off
- [[Filter Families]] — engineered pole placements compared

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., Ch. 6
