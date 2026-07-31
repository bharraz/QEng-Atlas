#optics

**Two mirrors make a comb of transmission resonances spaced by the free spectral range and narrowed by the finesse** — multi-pass interference means transmission only when the round trip phase is a multiple of 2π, and huge intracavity buildup when it is.

# Reference

$$
\mathrm{FSR} = \frac{c}{2L}, \qquad \mathcal{F} = \frac{\pi\sqrt{R}}{1-R} = \frac{\mathrm{FSR}}{\delta\nu}
$$

FSR = free spectral range (Hz), the spacing between resonances = inverse round-trip time, with $L$ = mirror separation (m); $R$ = mirror power reflectivity (dimensionless, equal mirrors assumed); $\mathcal{F}$ = finesse (dimensionless) — how many resolvable linewidths fit in one FSR, equivalently $2\pi\times$ the round trips a photon survives; $\delta\nu$ = resonance FWHM (Hz).

The two knobs are independent: $\mathcal{F}$ depends only on mirror loss ($\mathcal{F} \approx \pi/(1-R)$ for $R \to 1$, so $R = 0.99 \to 313$ and $R = 0.9999 \to 3.1\times10^4$), while $\delta\nu = \mathrm{FSR}/\mathcal{F} \propto 1/L\mathcal{F}$ — narrow lines need good mirrors *and* a long cavity. Numbers: $L = 10$ cm → FSR = 1.5 GHz; $R = 0.99$ → $\mathcal{F} \approx 313$ → $\delta\nu \approx 4.8$ MHz. ULE reference cavities: $\mathcal{F} \sim 10^5$–$10^6$, kHz linewidths.

**Transmission (Airy function):**
$$
T(\nu) = \frac{1}{1 + (2\mathcal{F}/\pi)^2 \sin^2(\pi\nu/\mathrm{FSR})}
$$

**Buildup:** on resonance the intracavity power is $\sim \mathcal{F}/\pi$ times the incident power (impedance-matched case) — why cavities enhance nonlinear processes (SHG) and why cavity mirrors burn first.

**Photon lifetime:** $\tau = 1/2\pi\delta\nu$; the cavity is a low-pass filter for intensity/frequency fluctuations at $f > \delta\nu/2$ — a high-finesse cavity's *transmission* is a quiet but slow reference (the reason PDH works in reflection instead).

**Scanning FP as optical spectrum analyzer:** piezo-sweep $L$ over one FSR while photodetecting transmission — reads out laser mode structure directly. Resolution $\delta\nu$; but beware: features separated by $n \cdot$FSR alias on top of each other. Confocal geometry is the standard because alignment is forgiving (degenerate transverse modes; effective FSR = $c/4L$).

> [!question]- Why is the intracavity buildup $\sim\mathcal{F}/\pi$, physically?
> A resonant photon makes $\sim \mathcal{F}/2\pi$ round trips before escaping (finesse *is* $2\pi \times$ storage time in round-trip units), so the circulating field is the coherent sum of that many injected contributions — power builds until leakage matches input.

# Connections

- [[Optical Cavity Stability]] — whether a transverse mode exists at all, and its waist, from $g_1g_2$
- [[Resonance and Q Factor]] — the FP is the optical row of the universal-resonator table; $Q = \nu/\delta\nu$
- [[Pound-Drever-Hall Locking]] — how a laser is actually held on one of these fringes
- [[Higher-Order Beam Modes]] — the extra peaks in a scan, from Gouy-phase mode splitting
- [[Cavity Modes]] — same boundary-condition physics from microwave to optical

---
Source: Siegman, *Lasers*, Ch. 11
