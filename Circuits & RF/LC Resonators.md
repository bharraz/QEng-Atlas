#circuits #electronics

**An L and a C swap energy back and forth at $\omega_0 = 1/\sqrt{LC}$; resistance decides how many swings (Q) before it's gone.**

# Reference

$$
\omega_0 = \frac{1}{\sqrt{LC}}, \qquad Q = \frac{\omega_0 L}{R} = \frac{1}{\omega_0 RC}\ (\text{series }R), \qquad \Delta f_{-3\text{dB}} = \frac{f_0}{Q}
$$

**Series LC:** impedance dips to $R$ at resonance (looks like a short) — notch/trap, or a low-Z way to drive a resonant load.
**Parallel (tank):** impedance peaks to $\approx Q\omega_0 L = L/RC$ (looks open) — frequency-selective load, oscillator tank.

Resonator characteristic impedance $Z_0 = \sqrt{L/C}$: at resonance both $|Z_L|$ and $|Z_C|$ equal this, and internal voltages/currents are **Q× the drive** — component stress, step-up, and pickup all scale with Q.

Numbers: 1 µH + 100 pF → 15.9 MHz, $Z_0 = 100\ \Omega$. Air-core/ceramic Q ~ 50–200; quartz crystal ~ $10^4$–$10^6$ (why oscillators use crystals). Helical resonators feeding ion-trap electrodes are exactly this: kV of trap RF from watts, step-up ≈ Q.

> [!question]- Drive a series LC at resonance with 1 Vpp. What's across the capacitor, and what does that imply about probing it?
> $Q\times 1$ Vpp — voltage magnification. It also means a scope probe's ~10 pF across the cap detunes and de-Qs the resonator; probe loosely (sniffer loop, tap point) or you change what you measure.

# Connections

- [[Resonance and Q Factor]] — the universal Q language this instantiates
- [[Driven Damped Harmonic Oscillator]] — same equation, mechanical costume
- [[Impedance Matching]] — L-networks are LC resonators run for impedance transformation
- [[Paul Traps]] — the helical-resonator RF drive is a high-Q tank in the lab

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §1.7
