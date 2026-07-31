#circuits #electronics

**Model any amplifier as noiseless plus two input generators — voltage $e_n$ in series, current $i_n$ in parallel — and total noise depends on your source impedance: $e_n$ dominates low-Z, $i_nR_s$ dominates high-Z.** Choosing an amplifier is matching this pair to $R_s$.

# Reference

$$
e_\text{total}^2 = e_n^2 + (i_n R_s)^2 + 4kTR_s \qquad (\text{units } \mathrm{V^2/Hz})
$$

$e_n$ = amplifier input voltage-noise density (V/√Hz), independent of source; $i_n$ = input current-noise density (A/√Hz), which becomes a *voltage* only after flowing through the source, hence the $i_nR_s$ product; $R_s$ = source resistance (Ω); $4kTR_s$ = the source's own [[Johnson-Nyquist Noise|Johnson noise]], the irreducible floor. Powers add in quadrature because the three are uncorrelated.

The $R_s$ dependence is the whole story: the amp's voltage term is flat, the current term grows as $R_s$, and the Johnson floor grows as $\sqrt{R_s}$ — so current noise wins at high impedance and always eventually dominates. Benchmark: 1 kΩ at 300 K = 4.1 nV/√Hz, so a 1 nV/√Hz amp is quieter than 60 Ω of resistance.

**Optimal source impedance** (amp contributions equal): $R_\text{opt} = e_n/i_n$.
- Bipolar input: low $e_n$ (~1 nV/√Hz), high $i_n$ (~pA/√Hz) → happiest near ~kΩ
- JFET/CMOS: modest $e_n$ (~5 nV/√Hz), tiny $i_n$ (~fA/√Hz) → the choice for MΩ sources

Don't add series resistance to "reach" $R_\text{opt}$ — it brings its own Johnson noise; change amplifiers instead.

**Friis / first-stage rule:** referred to input, each stage's noise is divided by the gain ahead of it:
$$
F = F_1 + \frac{F_2-1}{G_1} + \frac{F_3 - 1}{G_1 G_2} + \cdots
$$

$F_k$ = noise factor of stage $k$ (linear, not dB: the factor by which that stage degrades SNR; $\mathrm{NF} = 10\log_{10}F$); $G_k$ = available power gain of stage $k$ (linear). Each stage's penalty is divided by all the gain *ahead* of it, so 20 dB of low-noise gain up front suppresses everything downstream by 100×.
**Put low-noise gain first and nothing downstream matters** — also why you amplify *before* the long cable, not after.

Noise figure = dB of SNR degradation relative to the source's own Johnson noise; beware, NF quoted at 50 Ω says nothing about your 10 MΩ source. And check the **1/f corner** — $e_n$ specs are white-region numbers; below the corner (1–100 Hz typical) noise climbs.

> [!question]- The same 1 nV/√Hz bipolar amp is superb on a 50 Ω line and terrible on a 1 MΩ piezo. Why?
> At 1 MΩ the current-noise term rules: even 1 pA/√Hz gives $i_nR_s = 1$ µV/√Hz — three orders above $e_n$. High-Z sources need FET inputs (high $R_\text{opt} = e_n/i_n$), not the lowest $e_n$.

# Connections

- [[Johnson-Nyquist Noise]] — the $4kTR_s$ floor and the 4 nV/√Hz benchmark
- [[Op-Amp Golden Rules and Real Limits]] — where $e_n$ and $i_n$ live in the datasheet
- [[Flicker Noise]] — the 1/f corner that invalidates the white-noise math at low frequency
- [[Lock-In Detection]] — the standard escape: move the measurement above the corner
- [[Shot Noise]] — the source-side floor you're trying not to bury

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., Ch. 8
