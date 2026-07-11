#optics

**Faraday rotation is non-reciprocal — the rotation direction is set by the magnetic field, not the propagation direction — so a 45° Faraday rotator between two polarizers passes light one way and blocks the return.** The one-way valve that keeps your laser sane.

# Reference

Faraday rotation: $\theta = V B L$ (Verdet constant × field × length). Crucially, a beam that goes through and comes back gets $2\theta$, not zero — unlike a waveplate or optically active crystal, where the return trip undoes the rotation. Non-reciprocity is the whole trick.

**The device:** input polarizer → 45° Faraday rotator → output polarizer at 45°. Forward: polarized, rotated to 45°, transmitted. Backward: enters at 45°, rotated *another* 45° to 90°, blocked at the input polarizer.

**Why lasers need them:** back-reflections re-enter the diode as an uninvited external cavity — mode hops, linewidth broadening (or collapse), full coherence chaos. Diode lasers are notoriously touchy: feedback at the $-40$ dB level already destabilizes. Every fiber tip, cavity, and vapor-cell window downstream is a retroreflector aimed at your laser.

**Numbers:** 30–40 dB isolation single stage, ~60 dB double stage (standard in front of an ECDL feeding a cavity); insertion loss ~1 dB per stage. Gotchas: isolation is wavelength-dependent (rotator tuned for one λ — re-check if you retune far); the isolator only rejects what its input polarizer sees, so scrambled-polarization returns leak; magnets are strong (keep away from atoms, beams of ions, and magnetic-field-sensitive anything); high power can thermally de-tune the rotator.

Complementary defenses: angle-polish fiber connectors (FC/APC), tilt flat optics, weak focusing onto reflective surfaces.

> [!question]- A waveplate also rotates polarization — why can't it isolate?
> Reciprocity: for a waveplate or optical activity, the rotation sense is tied to the propagation direction, so the return pass undoes the forward pass and the light exits exactly as it entered. Faraday rotation's sense is fixed by $\mathbf{B}$; forward and backward passes *add*. Isolation fundamentally requires breaking time-reversal symmetry, and the magnetic field is what breaks it.

# Connections

- [[Birefringence]] — the reciprocal cousin; the contrast is the essence of isolation
- [[Laser Fundamentals]] — parasitic external cavities are why feedback destabilizes; the isolator removes them
- [[Laser Linewidth]] — feedback-induced linewidth broadening/collapse is what you're preventing
- [[Optical Fibers and Fiber Coupling]] — APC connectors, the passive partner to the isolator

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 6 (polarization devices: Faraday rotators & isolators)
