#circuits #electronics

**At RF, voltage and current lose meaning on a line but waves don't — S-parameters describe a network by how it scatters incident waves: S11 = what reflects, S21 = what gets through.**

# Reference

With incident waves $a_j$ and outgoing waves $b_i$, ports referenced to $Z_0 = 50\ \Omega$:
$$
S_{ij} = \frac{b_i}{a_j}\bigg|_{\text{other ports matched}}
$$

$a_j$ = complex amplitude of the wave going *into* port $j$, $b_i$ = wave coming *out* of port $i$, both normalized so that $|a|^2$ is power in watts — which is why $S$ is dimensionless and $|S|^2$ reads directly as a power fraction. The subscript order is destination-then-source ($S_{21}$ = out of port 2, in at port 1). $Z_0 = 50\ \Omega$ is the reference impedance defining the wave decomposition; quote it, since $S$ changes if the reference does.

$S_{11}$ = input reflection (equals Γ when port 2 is matched); $S_{21}$ = forward transmission (gain or insertion loss); $S_{12}$ = reverse isolation; $S_{22}$ = output match. In dB: $20\log_{10}|S|$ because $S$ is an amplitude ratio, so $-20$ dB means 10% of the amplitude and 1% of the power.

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
