#circuits #electronics

**At RF, voltage and current lose meaning on a line but waves don't — S-parameters describe a network by how it scatters incident waves: S11 = what reflects, S21 = what gets through.**

# Reference

With incident waves $a_j$ and outgoing waves $b_i$, ports referenced to $Z_0 = 50\ \Omega$:
$$
S_{ij} = \frac{b_i}{a_j}\bigg|_{\text{other ports matched}}
$$

$S_{11}$ = input reflection (equals Γ when port 2 is matched); $S_{21}$ = forward transmission (gain or insertion loss); $S_{12}$ = reverse isolation; $S_{22}$ = output match. In dB: $20\log|S|$; power fractions are $|S|^2$.

| $S_{11}$ | reflected power | verdict |
|---|---|---|
| −10 dB | 10% | fine for most lab work |
| −20 dB | 1% | good match |
| −30 dB | 0.1% | precision |

**Why waves instead of V/I:** on a line, V and I depend on where you stand (standing waves), while wave amplitudes are defined everywhere — and matched 50 Ω terminations are realizable at GHz where the open/short "test conditions" of Z-parameters are not.

**VNA notes:** it measures calibrated ratios — the cal standards move the reference plane to your connector, so calibrate at the end of the cable, not the front panel. Passive reciprocal: $S_{21} = S_{12}$; lossless: $|S_{11}|^2 + |S_{21}|^2 = 1$.

> [!question]- A filter shows S21 = −3 dB and S11 = −20 dB at the same frequency. Where did the power go?
> 1% reflected, 50% transmitted → ~49% dissipated inside. Loss, not mismatch — good match and good transmission are independent ways to fail.

# Connections

- [[Characteristic Impedance and Reflection]] — S11 is Γ measured with proper terminations
- [[Smith Chart]] — how S11 is displayed and interpreted
- [[dB Conventions]] — the 20-log vs 10-log bookkeeping used above
- [[Transmission Lines]] — why V/I fail and waves win

---
Source: Pozar, *Microwave Engineering* 4th ed., §4.3
