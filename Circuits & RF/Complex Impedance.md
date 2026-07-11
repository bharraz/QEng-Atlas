#circuits #electronics

**Impedance extends resistance to AC while keeping the phase: capacitors and inductors are resistors whose "resistance" is imaginary and frequency-dependent.** Once everything is a complex number, every DC trick — series/parallel, voltage dividers — works unchanged.

# Reference

$$
Z_R = R, \qquad Z_C = \frac{1}{j\omega C}, \qquad Z_L = j\omega L
$$

Series add; parallel combine as $Z_1Z_2/(Z_1+Z_2)$. $|Z|$ sets the current amplitude, $\arg Z$ the voltage–current phase (capacitor: current leads by 90°; inductor: lags by 90°).

**Generalized voltage divider — the workhorse:**
$$
\frac{V_\text{out}}{V_\text{in}} = \frac{Z_2}{Z_1+Z_2}
$$
Every passive filter is this equation with different $Z$'s plugged in.

**Quick magnitudes:** $|Z_C| = 1/\omega C$ — 100 nF is 16 Ω at 100 kHz, 1.6 Ω at 1 MHz. $|Z_L| = \omega L$ — 1 µH is 6.3 Ω at 1 MHz. Crossovers like these decide which parasitic dominates a node.

> [!question]- A 1 kΩ resistor in series with 100 nF, driven at 10 kHz — roughly what is the current's phase?
> $|Z_C| = 1/(2\pi\cdot10^4\cdot10^{-7}) \approx 160\ \Omega \ll 1\ \text{k}\Omega$: the branch is mostly resistive, current nearly in phase (leads by $\arctan(160/1000)\approx 9°$).

# Connections

- [[Complex Numbers and Phasors]] — why $e^{j\omega t}$ turns differential equations into this algebra
- [[RC and RL Filters]] — the divider above, evaluated vs frequency
- [[Transfer Functions and Bode Plots]] — impedance dividers plotted and read
- [[Capacitance and Inductance]] — where element values (and the pF/cm, nH/mm parasitics) come from

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §1.7
