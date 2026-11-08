#optics

**Faraday rotation is non-reciprocal — the rotation direction is set by the magnetic field, not the propagation direction — so a 45° Faraday rotator between two polarizers passes light one way and blocks the return.** It acts as a one-way valve that protects a laser from its own back-reflections.

# Reference

Faraday rotation: $\theta = V B L$ (Verdet constant × field × length). A beam that goes through and comes back gets $2\theta$, not zero — unlike a waveplate or optically active crystal, where the return trip undoes the rotation. This non-reciprocity is what makes isolation possible.

**Picture:** a one-way door: Faraday rotation turns the polarization the same way whichever direction the light travels, so returning light reaches the input polarizer rotated by 90° and is blocked.

**The device:** input polarizer → 45° Faraday rotator → output polarizer at 45°. Forward: polarized, rotated to 45°, transmitted. Backward: enters at 45°, rotated *another* 45° to 90°, blocked at the input polarizer.

**Why lasers need them:** back-reflections re-enter the diode and form an unintended external cavity — mode hops, linewidth broadening, or coherence collapse. Diode lasers are highly sensitive: feedback at the $-40$ dB level already destabilizes. Every fiber tip, cavity, and vapor-cell window downstream is a retroreflector aimed at your laser.

**Numbers:** 30–40 dB isolation single stage, ~60 dB double stage (standard in front of an ECDL feeding a cavity); insertion loss ~1 dB per stage.

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| input polarization not aligned with the input polarizer | light is rejected at the input | low transmission; the rejected light leaves through the polarizer's side port and must be blocked |
| laser retuned far from the design wavelength | rotation is proportional to the Verdet constant, which varies strongly with λ, so it is no longer 45° | isolation drops; re-check it after retuning, and readjust the rotator if it has an adjustment |
| returns with scrambled polarization | the isolator only rejects what its input polarizer sees | depolarized back-reflections partly leak through |
| reflections from the isolator's own input faces | those faces sit before any polarizer | feedback that persists with the isolator installed; tilt the isolator slightly |
| high power | absorption heats the Faraday crystal, detuning the rotation and forming a thermal lens | isolation and beam quality degrade as power rises |
| the strong magnet | | pulls steel tools; its stray field shifts Zeeman levels of nearby atoms and ions and the gain of PMTs, so keep it away from field-sensitive apparatus |
| the rejected backward beam | returning light leaves through the input polarizer's side port | a beam carrying the full back-reflected power, exiting sideways — block it |

**Measuring the isolation:** send the beam back through the isolator with a mirror after it, and measure the power that emerges backward, picked off before the isolator; its ratio to the power sent back is the isolation.

Complementary defenses: angle-polish fiber connectors (FC/APC), tilt flat optics, weak focusing onto reflective surfaces.

> [!question]- A waveplate also rotates polarization — why can't it isolate?
> Reciprocity: for a waveplate or optical activity, the rotation sense is tied to the propagation direction, so the return pass undoes the forward pass and the light exits exactly as it entered. Faraday rotation's sense is fixed by $\mathbf{B}$; forward and backward passes *add*. Isolation fundamentally requires breaking time-reversal symmetry, and the magnetic field is what breaks it.

# Connections

- [[Birefringence]] — the reciprocal counterpart; the contrast is the essence of isolation
- [[Laser Fundamentals]] — parasitic external cavities are why feedback destabilizes; the isolator removes them
- [[Laser Linewidth]] — feedback-induced linewidth broadening/collapse is what you're preventing
- [[Optical Fibers and Fiber Coupling]] — APC connectors, the passive partner to the isolator
- [[Laser Sources]] — which lasers need isolation, and what feedback does to each
- [[Handling Lab Hardware]] — magnets near tools and field-sensitive apparatus

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 6 (polarization devices: Faraday rotators & isolators)
