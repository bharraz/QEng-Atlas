#optics

**Two mirrors make a comb of transmission resonances spaced by the free spectral range and narrowed by the finesse** — multi-pass interference means transmission only when the round trip phase is a multiple of 2π, and huge intracavity buildup when it is.

# Reference

$$
\mathrm{FSR} = \frac{c}{2L}, \qquad \mathcal{F} = \frac{\pi\sqrt{R}}{1-R} = \frac{\mathrm{FSR}}{\delta\nu}
$$

- $\mathrm{FSR}$ — free spectral range (Hz): spacing between resonances, the inverse round-trip time
- $L$ — mirror separation (m)
- $R$ — mirror power reflectivity (dimensionless): equal mirrors assumed
- $\mathcal{F}$ — finesse (dimensionless): resolvable linewidths in one FSR
- $\delta\nu$ — resonance FWHM (Hz)

The finesse is equivalently $2\pi\times$ the number of round trips a photon survives.

**Picture:** a hall of mirrors: light bounces back and forth, and only when each round trip returns in phase do all the bounces add up and the light passes through.

The two knobs are independent: $\mathcal{F}$ depends only on mirror loss ($\mathcal{F} \approx \pi/(1-R)$ for $R \to 1$, so $R = 0.99 \to 313$ and $R = 0.9999 \to 3.1\times10^4$), while $\delta\nu = \mathrm{FSR}/\mathcal{F} \propto 1/L\mathcal{F}$ — narrow lines need good mirrors *and* a long cavity. Numbers: $L = 10$ cm → FSR = 1.5 GHz; $R = 0.99$ → $\mathcal{F} \approx 313$ → $\delta\nu \approx 4.8$ MHz. ULE reference cavities: $\mathcal{F} \sim 10^5$–$10^6$, kHz linewidths.

**Transmission (Airy function):**
$$
T(\nu) = \frac{1}{1 + (2\mathcal{F}/\pi)^2 \sin^2(\pi\nu/\mathrm{FSR})}
$$

**Buildup:** on resonance the intracavity power is $\sim \mathcal{F}/\pi$ times the incident power (impedance-matched case) — why cavities enhance nonlinear processes (SHG) and why cavity mirrors burn first.

**Photon lifetime:** $\tau = 1/2\pi\delta\nu$; the cavity is a low-pass filter for intensity/frequency fluctuations at $f > \delta\nu/2$ — a high-finesse cavity's *transmission* is a quiet but slow reference (the reason PDH works in reflection instead).

**Scanning FP as optical spectrum analyzer:** piezo-sweep $L$ over one FSR while photodetecting transmission — reads out laser mode structure directly. Resolution $\delta\nu$; but beware: features separated by $n \cdot$FSR alias on top of each other. Confocal geometry is the standard because alignment is forgiving (degenerate transverse modes; effective FSR = $c/4L$).

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| misalignment or mode mismatch | input light couples into transverse modes | extra peaks in the transmission scan ([[Higher-Order Beam Modes]], [[Mode Matching]]) |
| mirror contamination or coating degradation | added loss per round trip lowers the finesse | finesse falling over time; measure the ring-down |
| piezo nonlinearity and hysteresis | the length does not change linearly with voltage, and differs between up and down sweeps | a distorted frequency axis; calibrate with the FSR or with known modulation sidebands |
| thermal drift | the spacer expands with temperature | resonances drift (hence ULE spacers and temperature control) |
| vibration | acoustic and mechanical noise changes the length | a jittering transmission signal |
| polarization splitting | coating stress makes the mirrors weakly birefringent | each resonance doubled into two polarization peaks |
| absorption at high circulating power | heating changes the length during the scan | triangular, sawtooth-shaped resonances whose shape depends on scan direction |

> [!question]- Why is the intracavity buildup $\sim\mathcal{F}/\pi$, physically?
> A resonant photon makes $\sim \mathcal{F}/2\pi$ round trips before escaping (finesse *is* $2\pi \times$ storage time in round-trip units), so the circulating field is the coherent sum of that many injected contributions — power builds until leakage matches input.

# Connections

- [[Optical Cavity Stability]] — whether a transverse mode exists at all, and its waist, from $g_1g_2$
- [[Resonance and Q Factor]] — the FP is the optical row of the universal-resonator table; $Q = \nu/\delta\nu$
- [[Pound-Drever-Hall Locking]] — how a laser is held on one of these fringes
- [[Higher-Order Beam Modes]] — the extra peaks in a scan, from Gouy-phase mode splitting
- [[Cavity Modes]] — same boundary-condition physics from microwave to optical

---
Source: Siegman, *Lasers*, Ch. 11
