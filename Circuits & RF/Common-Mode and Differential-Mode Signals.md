#circuits #electronics

**Split any two-wire signal into the part the wires share (common mode) and the part between them (differential mode): your signal is differential, and interference — pickup, ground offsets — arrives mostly common-mode.** Reject CM and you reject the noise without touching the signal.

# Reference

$$
V_\text{dm} = V_+ - V_-, \qquad V_\text{cm} = \frac{V_+ + V_-}{2}, \qquad \text{CMRR} = 20\log_{10}\frac{A_\text{dm}}{A_\text{cm}}\ \text{dB}
$$

100 dB CMRR: 1 V of common-mode hum → 10 µV of apparent signal. Instrumentation amps do 100–120 dB at DC, but **CMRR falls with frequency** (typically −20 dB/dec above a few kHz) — check the curve, not the headline number.

**The sneaky mechanism — CM→DM conversion:** rejection assumes both lines are treated identically; any **impedance imbalance** converts:
$$
V_\text{dm} \approx V_\text{cm}\left(\frac{Z_1}{Z_1+Z_{s1}} - \frac{Z_2}{Z_2+Z_{s2}}\right)
$$
— mismatched source resistances, one wire's stray C to a heatsink, a filter cap on only one line. Once converted, no amplifier CMRR can remove it. **System CMRR is usually set by cabling imbalance, not by the amp.**

**Debugging move:** short the two inputs together at the far end (pure CM drive). Whatever appears at the output is CM leakage plus conversion — if it's large, hunt the asymmetry; don't swap amplifiers.

> [!question]- Your in-amp claims 120 dB CMRR but 1 V of 60 Hz common-mode produces 1 mV at the output (60 dB). Where did the other 60 dB go?
> CM→DM conversion upstream: an impedance imbalance between the two lines (unequal source R, asymmetric stray C or filtering) converted CM into DM before the amplifier — which then amplified it faithfully as "signal."

# Connections

- [[Instrumentation Amplifier]] — the hardware that implements the rejection
- [[Differential Signaling]] — engineering signals so pickup lands common-mode by symmetry
- [[Ground Loops]] — the lab's main generator of common-mode voltage
- [[Ferrites and Common-Mode Chokes]] — impedance that acts on CM only, by flux cancellation

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Ch. 4
