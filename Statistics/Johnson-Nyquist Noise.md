#statistics #math

**Every resistor is a noise generator: thermal agitation of carriers gives a white voltage noise set only by $T$ and $R$** — dissipation and fluctuation are two faces of the same coupling to the thermal bath, so you cannot have resistance without noise.

# Reference

One-sided PSD and rms over bandwidth $B$:

$$
S_V = 4k_B T R \qquad \Rightarrow \qquad v_{\text{rms}} = \sqrt{4k_B T R B}
$$

$S_V$ = one-sided voltage noise power spectral density (V²/Hz — a *density*, so it must be multiplied by a bandwidth before it means anything); $k_B T$ = thermal energy (J; 25.9 meV at 300 K); $R$ = the **real** part of the impedance (Ω) — only dissipation generates noise, so a pure L or C contributes none; $B$ = the equivalent noise bandwidth of the measurement (Hz).

Three proportionalities: noise voltage $\propto \sqrt{R}$ (10× the resistance costs only 3.2× the noise), $\propto \sqrt{T}$ (cooling 300 K → 3 K buys 10×, which is why cryogenic preamps exist), and $\propto \sqrt{B}$ (halving bandwidth = 1.4× less noise, the universal averaging lever). The factor 4 is a convention of the one-sided density; two-sided versions carry $2k_BTR$.

**The anchor number: $1\ \mathrm{k\Omega}$ at 300 K → $\sqrt{4k_BTR} \approx 4.07\ \mathrm{nV/\sqrt{Hz}}$.** Scale by $\sqrt{R}$:

| $R$ | $e_n$ @ 300 K |
|---|---|
| 50 Ω | 0.9 nV/√Hz |
| 1 kΩ | 4 nV/√Hz |
| 100 kΩ | 41 nV/√Hz |
| 1 MΩ | 129 nV/√Hz |

Current form (Norton): $i_n = \sqrt{4k_BT/R}$ (A/√Hz) — the same source seen as a current generator, so big resistors are quiet in current and small ones quiet in voltage; which form matters depends on whether your amplifier's input is voltage- or current-sensing ([[Amplifier Noise]]).

Maximum *available* noise power into a matched load is $P = k_BT B$ — $R$ cancels, because a bigger resistor makes more voltage but delivers it through a bigger source impedance. Hence a universal floor of $-174$ dBm/Hz at 290 K, the reference every RF noise figure is quoted against.

**Practical reads:** it's white and Gaussian (flat to ~THz at 300 K); cooling helps only as $\sqrt{T}$; the feedback resistor of a transimpedance amp injects $\sqrt{4k_BT/R_f}$ current noise — one reason bigger $R_f$ wins until bandwidth says no. Reactances don't produce noise; only the dissipative (real) part does.

> [!question]- Your amplifier has $e_n = 1\,\mathrm{nV/\sqrt{Hz}}$. What source impedance makes the source, not the amp, set the noise floor?
> Johnson noise exceeds $1\,\mathrm{nV/\sqrt{Hz}}$ for $R \gtrsim 60\ \Omega$ at 300 K (since 1 kΩ gives 4 nV/√Hz and $e_n \propto \sqrt{R}$). Above that the amp is "free"; far below it, the amp dominates and you need a better front end or a matching transformer.

# Connections

- [[Power Spectral Density]] — $4k_BTR$ is the canonical one-sided, V²/Hz example
- [[Amplifier Noise]] — the $e_n$–$i_n$ budget where Johnson noise of the source sets the reference
- [[Shot Noise]] — the other fundamental white floor; crossover at $V \approx 50$ mV
- [[Vacuum Fluctuations]] — the fluctuation-dissipation theorem's quantum end ($\hbar\omega/2$ replaces $k_BT$)
- [[Noise Spectra and Coupling to Systems]] — the white-noise entry of the general taxonomy

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §8.1.1
