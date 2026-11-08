#optics

**Holding a laser on a cavity resonance needs an error signal that changes sign across the resonance; the reflected intensity is symmetric about resonance and cannot say which side you are on, but the phase of the reflected light can.** Pound–Drever–Hall (PDH) locking measures that phase: phase-modulation sidebands act as a phase ruler, and demodulating their beat with the reflected carrier yields a steep, antisymmetric error signal centered on resonance. It's a phase measurement, not an intensity measurement, which is why it's both fast and immune to power fluctuations.

# Reference

**Setup:** an [[Electro-Optic Modulator]] (EOM) driven at $\Omega$ puts sidebands at $\pm\Omega$ on the laser (with $\Omega \gg$ cavity linewidth, so they reflect fully); a photodiode watches the *reflected* port. The photocurrent contains a beat at $\Omega$ between the reflected carrier and the sidebands, and the phase of that beat carries the carrier's phase shift on reflection. A [[Mixers|mixer]] multiplies the photocurrent by the EOM drive at $\Omega$, and a low-pass filter keeps the slow product (demodulation). The error signal is
$$
\epsilon \propto -2\sqrt{P_c P_s}\; \mathrm{Im}\{F(\omega)F^*(\omega+\Omega) - F^*(\omega)F(\omega-\Omega)\}
$$

- $\epsilon$ — demodulated error signal (V at the mixer output)
- $P_c, P_s$ — optical power in the carrier and in each sideband (W)
- $\Omega$ — modulation frequency (rad/s): $\gg$ linewidth, so sidebands reflect as an unshifted phase reference
- $F(\omega)$ — cavity reflection coefficient (dimensionless, complex): amplitude and phase of what comes back
- $\beta$ — modulation index (rad), the EOM's peak phase excursion

The $\sqrt{P_cP_s}$ says the signal is a *beat*, so it scales with the geometric mean, maximized when the modulation index puts comparable power in both ($\beta \approx 1.08$). Taking $\mathrm{Im}\{\cdot\}$ selects the *phase* difference between carrier and sidebands, which is what makes the signal antisymmetric in detuning and insensitive to intensity.

**Picture:** the reflected light's phase changes sign as the laser crosses resonance; the sidebands, reflected off-resonance, are a fixed phase reference for reading that sign.

**The shape:** steep linear zero-crossing at resonance with slope $\propto 1/\delta\nu$ (finesse gives slope; $\delta\nu$ is the cavity linewidth), flat wings, and smaller inverted zero-crossings out at $\pm\Omega$ — the sideband resonances. The sign of $\epsilon$ tells you *which way* you're detuned; the wide capture range comes from the wings holding sign all the way to the sidebands.

**Why it's fast:** off resonance the carrier reflects promptly, while the leakage field from the stored intracavity light keeps the *old* frequency — the beat between them senses laser phase excursions immediately, not after the cavity storage time. Above the cavity linewidth the cavity acts as a frequency-to-phase integrator (error signal rolls off as $1/f$ but does not vanish), so servo bandwidth is *not* limited to the cavity linewidth — MHz-bandwidth locks to kHz-linewidth cavities are routine.

**Why intensity-insensitive:** on resonance $\epsilon = 0$ regardless of laser power — demodulation at $\Omega$ rejects DC intensity noise, and the lock point is a phase condition, not a power level. Residual sensitivity comes back through residual amplitude modulation (RAM) on the EOM, which appears as a drifting offset and is the real-world limit; the standard countermeasures are temperature-stabilizing the EOM and aligning the input polarization to its crystal axis.

**Settings:** $\beta \approx 1.08$ gives the maximum error-signal slope. The demodulation phase (the relative phase between the two mixer inputs) must also be set: at the wrong phase the trace looks like a smeared derivative of the resonance, and at the right phase it is the clean antisymmetric shape above.

**Bringing up the lock — the steps and why:**

1. **See the resonance.** Scan the laser frequency (or the cavity length) across a resonance and watch the reflected power: it dips on resonance. The depth of the dip shows how well the beam is mode-matched ([[Mode Matching]]).
2. **Check the error-signal shape.** With modulation on, the mixer output during the scan should show the antisymmetric shape above, with the two small inverted features at the sidebands. A symmetric or smeared trace means the demodulation phase is wrong: adjust it until the central slope is steepest and the shape is antisymmetric.
3. **Choose the sign.** The feedback must push the laser toward the zero crossing; with the wrong sign it pushes away, and the lock never catches, so the sign is flipped once if needed.
4. **Close the loop on resonance.** Shrink the scan until the laser sits on the resonance, switch on proportional gain, then the integrator; the laser stays on the zero crossing and the transmitted power rises to its maximum.
5. **Raise the gain** until the servo bump in the error signal's noise spectrum starts to grow, then back off ([[PID Control]], [[Stability and Phase Margin]]).

**What a failing lock looks like:**

| Symptom | Cause |
|---|---|
| holds for seconds, then jumps away | slow drift exceeds the fast actuator's range — a slower actuator (piezo, temperature) must take over the DC correction |
| oscillates at a fixed frequency | gain too high for the phase margin |
| lock point drifts slowly | residual amplitude modulation offset ([[Electro-Optic Modulator]]) |
| locks to the wrong feature | a sideband or a transverse-mode resonance has its own zero crossing — check the transmitted mode on a camera |

> [!question]- Why can the PDH servo bandwidth exceed the cavity linewidth?
> The error signal compares the promptly reflected carrier against the cavity's stored field, which acts as a flywheel phase reference. Fast laser phase noise shows up in the beat instantly; the cavity's slowness is what *makes* it a good reference, not a lag in the sensor. The response rolls off only as $1/f$ above the cavity pole — a fixable, well-behaved transfer function.

# Connections

- [[Electro-Optic Modulator]] — the sideband generator; its $J_n(\beta)$ spectrum and residual amplitude modulation (RAM) set what the lock can achieve
- [[Fabry-Perot Cavity]] — the frequency reference; finesse sets error-signal slope
- [[Mixers]] — the demodulation step is a phase detector at $\Omega$
- [[PID Control]] — the error signal is only half the lock; the loop shape is the other half
- [[Laser Linewidth]] — the purpose: pushing technical noise toward the cavity's stability

---
Source: E. Black, "An introduction to Pound–Drever–Hall laser frequency stabilization," Am. J. Phys. 69, 79 (2001)
