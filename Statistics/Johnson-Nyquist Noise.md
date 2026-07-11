#statistics #math

**Every resistor is a noise generator: thermal agitation of carriers gives a white voltage noise set only by $T$ and $R$** — dissipation and fluctuation are two faces of the same coupling to the thermal bath, so you cannot have resistance without noise.

# Reference

One-sided PSD and rms over bandwidth $B$:

$$
S_V = 4k_B T R \qquad \Rightarrow \qquad v_{\text{rms}} = \sqrt{4k_B T R B}
$$

**The anchor number: $1\ \mathrm{k\Omega}$ at 300 K → $\sqrt{4k_BTR} \approx 4.07\ \mathrm{nV/\sqrt{Hz}}$.** Scale by $\sqrt{R}$:

| $R$ | $e_n$ @ 300 K |
|---|---|
| 50 Ω | 0.9 nV/√Hz |
| 1 kΩ | 4 nV/√Hz |
| 100 kΩ | 41 nV/√Hz |
| 1 MΩ | 129 nV/√Hz |

Current form (Norton): $i_n = \sqrt{4k_BT/R}$ — big resistors are quiet in current, small ones in voltage. Maximum *available* noise power into a matched load is $k_BT B$, independent of $R$: $-174$ dBm/Hz at 290 K, the RF noise-floor reference.

**Practical reads:** it's white and Gaussian (flat to ~THz at 300 K); cooling helps only as $\sqrt{T}$; the feedback resistor of a transimpedance amp injects $\sqrt{4k_BT/R_f}$ current noise — one reason bigger $R_f$ wins until bandwidth says no. Reactances don't produce noise; only the dissipative (real) part does.

> [!question]- Your amplifier has $e_n = 1\,\mathrm{nV/\sqrt{Hz}}$. What source impedance makes the source, not the amp, set the noise floor?
> Johnson noise exceeds $1\,\mathrm{nV/\sqrt{Hz}}$ for $R \gtrsim 60\ \Omega$ at 300 K (since 1 kΩ gives 4 nV/√Hz and $e_n \propto \sqrt{R}$). Above that the amp is "free"; far below it, the amp dominates and you need a better front end or a matching transformer.

# Connections

- [[Power Spectral Density]] — $4k_BTR$ is the canonical one-sided, V²/Hz example
- [[Amplifier Noise]] — the $e_n$–$i_n$ budget where Johnson noise of the source sets the reference
- [[Shot Noise]] — the other fundamental white floor; crossover at $V \approx 50$ mV
- [[Vacuum Fluctuations]] — the fluctuation-dissipation theorem's quantum end ($\hbar\omega/2$ replaces $k_BT$)

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §8.1.1
