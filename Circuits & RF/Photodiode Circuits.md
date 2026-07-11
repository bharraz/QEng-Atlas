#circuits #electronics

**A photodiode is a current source: $I = \mathcal{R}P$, linear over ~9 decades — keep it looking into a low-impedance (transimpedance) input and it stays that way.**

# Reference

Responsivity $\mathcal{R} = \eta e\lambda/hc$ — quantum efficiency times one electron per photon:

| Detector | λ range | $\mathcal{R}$ |
|---|---|---|
| Si | 400–1000 nm | ~0.4–0.6 A/W (peak near 900 nm) |
| InGaAs | 900–1700 nm | ~0.9–1.0 A/W at 1550 nm |

Call it **~0.5 mA per mW**: 1 µW is still 0.5 µA — comfortably measurable without heroics.

**Bias choices:**
- **Photovoltaic (0 V):** no dark current, lowest noise — precision and low light, but slow
- **Reverse biased:** junction capacitance drops severalfold → faster response and a stabler transimpedance amp; cost is dark current and its shot noise

**Shot-noise-limited condition:** photocurrent shot noise beats the feedback resistor's Johnson noise when
$$
2eI_\text{ph} > \frac{4kT}{R_f} \iff I_\text{ph}R_f > \frac{2kT}{e} \approx 52\ \text{mV}
$$
— i.e. **more than ~52 mV of signal across the transimpedance**. Trivial at mA, the entire game at nA.

Speed: limited by $RC_j$ or carrier transit; $C_j$ ~ pF–tens of pF and scales with area — small and biased = fast. Watch for room light (DC + 100/120 Hz flicker) and for back-reflections into the laser, which show up as *laser* noise.

> [!question]- At 10 µA photocurrent with $R_f$ = 10 kΩ the noise floor sits 10 dB above shot noise. Is the 52 mV rule violated?
> No — $I R_f = 0.1$ V > 52 mV, so the resistor is cleared. Look elsewhere: amplifier $e_n$ gain-peaked by diode capacitance, or technical intensity noise the measurement doesn't cancel. The rule only guarantees Johnson noise loses.

# Connections

- [[Transimpedance Amplifier]] — the right readout, and its stability tax
- [[Shot Noise]] — the $2eI$ floor and when you've actually reached it
- [[Photodetection and Shot Noise]] — the quantum-optics side of the same floor
- [[Amplifier Noise]] — what usually stands between you and $2eI$

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §8.11
