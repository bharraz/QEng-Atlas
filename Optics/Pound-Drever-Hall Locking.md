#optics

**PDH measures the phase of the light reflected from a cavity — phase-modulation sidebands act as a phase ruler, and demodulating the reflected beat yields a steep, antisymmetric error signal centered on resonance.** It's a phase measurement, not an intensity measurement, which is why it's both fast and immune to power fluctuations.

# Reference

**The scheme:** EOM puts sidebands at $\pm\Omega$ (with $\Omega \gg$ cavity linewidth, so they reflect fully); photodiode watches the *reflected* port; mix the photocurrent with the drive at $\Omega$; low-pass. The error signal is
$$
\epsilon \propto -2\sqrt{P_c P_s}\; \mathrm{Im}\{F(\omega)F^*(\omega+\Omega) - F^*(\omega)F(\omega-\Omega)\}
$$
with $F$ the cavity reflection coefficient.

**The shape:** steep linear zero-crossing at resonance with slope $\propto 1/\delta\nu$ (finesse buys slope), flat wings, and smaller inverted zero-crossings out at $\pm\Omega$ — the sideband resonances. The sign of $\epsilon$ tells you *which way* you're detuned; the wide capture range comes from the wings holding sign all the way to the sidebands.

**Why it's fast:** off resonance the carrier reflects promptly, while the leakage field from the stored intracavity light keeps the *old* frequency — the beat between them senses laser phase excursions immediately, not after the cavity storage time. Above the cavity linewidth the cavity acts as a frequency-to-phase integrator (error signal rolls off as $1/f$ but doesn't die), so servo bandwidth is *not* limited to the cavity linewidth — MHz-bandwidth locks to kHz-linewidth cavities are routine.

**Why intensity-insensitive:** on resonance $\epsilon = 0$ regardless of laser power — demodulation at $\Omega$ rejects DC intensity noise, and the lock point is a phase condition, not a power level. Residual sensitivity comes back through RAM on the EOM (drifting offset — the real-world limit; temperature-stabilize the EOM, align its polarization).

Choose $\beta \approx 1.08$ for maximum error-signal slope; demod phase must be set (slide it until the trace is antisymmetric, not derivative-of-a-blob).

> [!question]- Why can the PDH servo bandwidth exceed the cavity linewidth?
> The error signal compares the promptly reflected carrier against the cavity's stored field, which acts as a flywheel phase reference. Fast laser phase noise shows up in the beat instantly; the cavity's slowness is what *makes* it a good reference, not a lag in the sensor. The response rolls off only as $1/f$ above the cavity pole — a fixable, well-behaved transfer function.

# Connections

- [[Electro-Optic Modulator]] — the sideband generator; its $J_n(\beta)$ spectrum and its RAM gotcha are the input budget
- [[Fabry-Perot Cavity]] — the frequency reference; finesse sets error-signal slope
- [[Mixers]] — the demodulation step is a phase detector at $\Omega$
- [[PID Control]] — the error signal is only half the lock; the loop shape is the other half
- [[Laser Linewidth]] — the point of it all: pushing technical noise toward the cavity's stability

---
Source: E. Black, "An introduction to Pound–Drever–Hall laser frequency stabilization," Am. J. Phys. 69, 79 (2001)
