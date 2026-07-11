#circuits #electronics

**dB is 10·log of a power ratio — voltage gets 20·log only because P ∝ V² — and dBm is absolute power referenced to 1 mW, which in the RF world implicitly means "into 50 Ω."**

# Reference

$$
\text{dB} = 10\log_{10}\frac{P}{P_0} = 20\log_{10}\frac{V}{V_0}\ (\text{equal impedances!}), \qquad P\,[\text{dBm}] = 10\log_{10}\frac{P}{1\ \text{mW}}
$$

dBc = dB relative to the carrier (spurs, sidebands, phase noise).

**Mental arithmetic:** +3 dB = ×2 power; +10 dB = ×10 power; +6 dB = ×2 voltage; +20 dB = ×10 voltage. Gains in dB add; dBm + dB = dBm; never add two dBm values (that multiplies watts).

**dBm ↔ voltage at 50 Ω** ($V_\text{rms} = \sqrt{50\,P}$, $V_{pp} = 2\sqrt2\,V_\text{rms}$, sine):

| dBm | P | $V_\text{rms}$ | $V_{pp}$ |
|---|---|---|---|
| +20 | 100 mW | 2.24 V | 6.32 V |
| +10 | 10 mW | 707 mV | 2.00 V |
| +7 | 5 mW | 500 mV | 1.41 V |
| 0 | 1 mW | 224 mV | 632 mV |
| −10 | 100 µW | 70.7 mV | 200 mV |
| −20 | 10 µW | 22.4 mV | 63.2 mV |
| −30 | 1 µW | 7.07 mV | 20 mV |

Anchors: **0 dBm = 632 mVpp**, +10 dBm = 2 Vpp, +7 dBm = a typical mixer LO drive.

**Gotcha:** a high-Z scope shows *twice* the voltage the same signal has when terminated in 50 Ω (−6 dB difference). Know which one you're quoting before comparing to the spectrum analyzer.

> [!question]- The spectrum analyzer reads −40 dBm. What's that in volts on the 50 Ω line?
> −40 dBm = 100 nW → $V_\text{rms} = \sqrt{10^{-7}\cdot 50} \approx 2.2$ mV ≈ 6.3 mVpp. (Shortcut: 0 dBm = 224 mVrms; −40 dB = ÷100 in voltage.)

# Connections

- [[S-Parameters]] — quoted in dB; the 10-vs-20 rule matters there
- [[Power Spectral Density]] — dBm/Hz and the V²/Hz vs V/√Hz cousin confusion
- [[Mixers]] — LO levels and conversion loss all speak dBm
- [[Characteristic Impedance and Reflection]] — the 50 Ω convention underneath dBm

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §1.3.2
