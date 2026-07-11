#circuits #electronics

**Golden rules — with negative feedback the output does whatever holds the two inputs equal, and the inputs draw no current — hold only while the loop has gain to spare; every "weird" op-amp problem is one of the finite specs below biting.**

# Reference

The rules give the classics instantly: follower, inverting gain $-R_f/R_\text{in}$ (virtual ground at the (−) input), non-inverting $1+R_f/R_g$, transimpedance $-R_f$.

**The reality table:**

| Spec | Typical | Bites you as |
|---|---|---|
| GBW (gain × BW ≈ const) | 1–100 MHz | gain-of-100 on a 10 MHz part → 100 kHz bandwidth |
| Slew rate | 0.5–100 V/µs | full-power BW $= \text{SR}/\pi V_{pp}$; big fast sine → triangle |
| Offset voltage $V_{os}$ | 0.01–5 mV, drifts µV/°C | × noise gain = DC error at the output |
| Input bias current | fA (FET) – µA (bipolar) | × source R = offset; integrators drift; inputs need a DC path! |
| Voltage noise $e_n$ | 1–20 nV/√Hz + 1/f corner | benchmark: 4 nV/√Hz = 1 kΩ of resistor |
| Current noise $i_n$ | fA–pA/√Hz | × source Z — what punishes high-impedance sources |
| Output current | ±10–30 mA | can't drive 50 Ω to the rails; cable capacitance loads the loop |
| Rails | input CM range, output swing | "rail-to-rail" still isn't quite; some inputs phase-invert outside CM range |

**Stability extras:** capacitive load (a few meters of coax!) erodes phase margin — isolate with 50–100 Ω series R. And decouple the supplies, or it oscillates and you'll blame everything else first.

> [!question]- A ×1000 amplifier on a 1 MHz-GBW op-amp "works" but rolls off at ~1 kHz. Broken?
> No — GBW at work: closed-loop bandwidth ≈ 1 MHz/1000 = 1 kHz. More gain than the bandwidth budget allows: cascade two ×32 stages or buy GBW.

# Connections

- [[Amplifier Noise]] — using $e_n$, $i_n$ against source impedance properly
- [[Transimpedance Amplifier]] — where GBW, source capacitance, and stability collide hardest
- [[Stability and Phase Margin]] — why the feedback that makes the rules work can oscillate
- [[Comparators and Hysteresis]] — the job op-amps look suited for but aren't

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., Chs. 4–5
