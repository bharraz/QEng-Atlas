#circuits #electronics

**A resistor in series and a capacitor to ground, driven by a sine, form a voltage divider whose lower arm loses impedance as the frequency rises: low frequencies pass, high ones are shorted to ground, and the crossover sits where the two impedance magnitudes are equal.** Swapping the two parts makes a high-pass, and an inductor in place of the capacitor makes the mirror-image pair. Each is a single pole, rolling off at 20 dB per decade.

# Reference

$$
H_\text{LP} = \frac{1}{1 + jf/f_c}, \qquad H_\text{HP} = \frac{jf/f_c}{1 + jf/f_c}, \qquad f_c = \frac{1}{2\pi RC}\ \ (\text{RC}), \qquad f_c = \frac{R}{2\pi L}\ \ (\text{RL})
$$

- $H$ — output voltage over input voltage (complex, dimensionless): gain and phase
- $f$ — drive frequency (Hz)
- $f_c$ — corner frequency (Hz): where $\lvert Z_C\rvert$ or $\lvert Z_L\rvert$ equals $R$

Both follow from the divider $Z_2/(Z_1+Z_2)$ of [[Complex Impedance]]. Anchor: 1 kΩ + 160 nF ≈ 1 kHz; scale from there.

| Circuit | Low-pass | High-pass |
|---|---|---|
| RC | series $R$, shunt $C$, output across $C$ | series $C$, shunt $R$, output across $R$ |
| RL | series $L$, shunt $R$, output across $R$ | series $R$, shunt $L$, output across $L$ |

| Frequency | Low-pass | High-pass |
|---|---|---|
| $f \ll f_c$ | 0 dB, 0° | rising at +20 dB/decade, +90° |
| $f = f_c$ | **−3 dB, −45°** | −3 dB, +45° |
| $f \gg f_c$ | falling at −20 dB/decade, −90° | 0 dB, 0° |

**Picture:** the capacitor is a reservoir that cannot fill and empty fast enough to follow quick wiggles, so they are smoothed away while slow changes pass ([[RC and RL Time Response]]).

**Asymptotic identities:** a low-pass well above $f_c$ integrates; a high-pass well below $f_c$ differentiates, so AC coupling acts as a differentiator for slow drift. These hold only in the asymptotes; near the corner the filter is neither.

**Loading by source and load,** the most common error in practice. The formulas assume a stiff source and a light load.
- The source's output impedance adds in series with $R$ and moves the corner **down**.
- A load across $C$ divides the passband and moves the corner **up**.
- Two RCs cascaded without a buffer do *not* give a clean two-pole response: the second loads the first, softening the knee and shifting the corners. For a real second-order response see [[Sallen-Key Topology]].
- Keep impedance steps of about 10× between stages, or buffer.

**−3 dB is little attenuation:** real rejection needs the corner a decade or more away from what is rejected, or more poles ([[Filter Families]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| gain and phase against a swept sine | $f_c$ at −3 dB and ±45°; a 20 dB/decade slope confirms a single pole |
| corner below the design value | resistance in series with $R$, usually the source's output impedance |
| passband below 0 dB, corner above the design value | a resistive load across the output |
| step response | $\tau = 1/2\pi f_c$, the same pole seen in time |

> [!question]- You built 1 kΩ + 160 nF for a 1 kHz corner but measure −3 dB at ~670 Hz. What did you forget?
> The source's ~500 Ω output impedance in series with the 1 kΩ: $f_c = 1/2\pi(R_s{+}R)C$. Corners are set by total impedances, not schematic values.

# Connections

- [[Complex Impedance]] — the voltage divider generating all of this
- [[RC and RL Time Response]] — the same circuits driven by steps and switched-on sines
- [[Transfer Functions and Bode Plots]] — how the pole reads on a plot
- [[Filter Families]] — when one pole isn't enough
- [[Decoupling and Bypassing]] — the same RC idea applied to power rails
- [[Filtering Power and Signal Lines]] — using these filters on real supply, bias, and signal lines
- [[Capacitors in Practice]] — why the capacitor's real value may differ from its label

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §1.7
