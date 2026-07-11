#physics #AMO

**A driven system with loss responds most strongly when driven near its natural frequency, and the full response is complex: one number carrying both how large the response is and how much it lags the drive.** Splitting that complex response into its real and imaginary parts gives the dispersive and absorptive responses — the pair of ideas AMO is built on.

# Reference

Drive a damped oscillator, $\ddot{x} + \gamma\dot{x} + \omega_0^2 x = (F/m)\,e^{-i\omega t}$. The steady state follows the drive frequency with a complex amplitude $x = \chi(\omega)\,(F/m)\,e^{-i\omega t}$, where the **complex response function** is

$$\chi(\omega) = \frac{1}{\omega_0^2 - \omega^2 - i\gamma\omega}.$$

Near resonance, write the detuning $\Delta = \omega - \omega_0$ and use $\omega_0^2 - \omega^2 \approx -2\omega_0\Delta$. The response collapses to the **complex Lorentzian**

$$\chi(\omega) \;\propto\; \frac{1}{\Delta + i\gamma/2},$$

whose real and imaginary parts are physically distinct:

- **Imaginary part** $\dfrac{\gamma/2}{\Delta^2 + (\gamma/2)^2}$ — even in detuning, peaks on resonance, a Lorentzian of full width $\gamma$. This is the **absorptive**, out-of-phase, dissipative response: energy taken from the drive.
- **Real part** $\dfrac{-\Delta}{\Delta^2 + (\gamma/2)^2}$ — odd in detuning, zero on resonance, changes sign across it. This is the **dispersive**, in-phase, reactive response: energy stored and returned.

**Phase** runs $0 \to \pi/2 \to \pi$ as you sweep up through resonance. Exactly on resonance the response lags the drive by $\pi/2$, which is why power transfer peaks there — velocity is in phase with force. The amplitude peak's sharpness is set by $Q = \omega_0/\gamma$ (see [[Resonance and Q Factor]]).

**The time-domain price of a sharp resonance.** Everything above is *steady state*, and steady state takes $\sim Q$ cycles to establish: the transient builds (or rings down) on the timescale $\tau = 2/\gamma = 2Q/\omega_0$. Consequences that recur everywhere: a high-Q resonator cannot respond to drive changes faster than $\tau$ — its linewidth *is* its control bandwidth (a cavity lock can't correct inside the cavity's own response time); sweeping a drive through resonance faster than $\gamma^{-2}$-ish drags and distorts the line (ringing tails — the swept-cavity diagnostic); and a resonance probed for time $T < \tau$ shows a width $\sim 1/T$, not $\gamma$ — Fourier-limited, not lifetime-limited. Sharp in frequency = slow in time, always.

**Why this is the AMO precursor.** Model an atom as an electron on a spring driven by a light field (the classical Lorentz oscillator). It acquires a complex polarizability $\alpha(\omega)$ with exactly this structure: the **imaginary part governs absorption** (photon scattering, radiation pressure) and the **real part governs dispersion** (refractive index, and the dipole/optical-trap potential $\propto \mathrm{Re}\,\alpha$). The same absorptive/dispersive split reappears quantum-mechanically as the two quadratures of the [[Optical Bloch Equations]] and as scattering-rate vs. light-shift. Real and imaginary parts are not independent — causality ties them through the [[Kramers-Kronig Relations]]. "Absorption and dispersion are two faces of one complex response" is the sentence to carry forward.

> [!question]- Why does the response lag the drive by exactly 90° on resonance, and why does that maximize energy absorption?
> On resonance the inertial term $-\omega^2 x$ and restoring term $\omega_0^2 x$ cancel, leaving the damping term $\gamma\dot{x}$ to balance the drive. That forces velocity in phase with the driving force, so the instantaneous power $F\cdot v$ is always positive and its average is maximal — the drive is doing work against damping on every part of the cycle.

# Connections

- [[Driven Damped Harmonic Oscillator]] — the equation this analyzes; amplitude and phase vs. detuning
- [[Resonance and Q Factor]] — $Q$, linewidth, and ringdown; the many physical faces of the same math
- [[Complex Numbers and Phasors]] — why packaging amplitude and phase as one complex number is the natural move
- [[Kramers-Kronig Relations]] — causality linking the dispersive (real) and absorptive (imaginary) parts
- [[Optical Bloch Equations]] — the quantum successor: dispersive and absorptive quadratures of the atomic response
- [[Dielectrics and Polarizability]] — the complex $\alpha(\omega)$ this produces, and its refractive-index consequence
- [[Impulse and Frequency Response]] — a resonator as an LTI system; this $\chi(\omega)$ is its frequency response

---
Source: French, *Vibrations and Waves*, Ch. 3–4; Foot, *Atomic Physics*, §7.5 for the classical-oscillator model of the atom
