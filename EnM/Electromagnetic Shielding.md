#EnM

**A shield works by reflecting the wave at the impedance mismatch of its surface, then absorbing what gets in via skin-effect decay** — and it fails not through its walls but through its holes, seams, and the cables you poke through it.

# Reference

Shielding effectiveness (dB) = **reflection loss + absorption loss** (+ a multiple-reflection correction for thin walls):

$$
SE_{abs} \approx 8.7\,\frac{t}{\delta}\ \text{dB}, \qquad \delta = \sqrt{2/\mu\sigma\omega}
$$

Reflection loss depends on the wave impedance vs the metal's (tiny) surface impedance — huge for far-field and near-field *electric* sources, **small for near-field magnetic sources** (low wave impedance already matches the metal).

**The regimes:**

| Threat | What works |
|---|---|
| E-field / far-field, any f | almost any continuous metal — reflection does it |
| RF magnetic (> ~100 kHz) | eddy currents in ordinary copper/aluminum (t ≳ few δ) |
| Low-freq magnetic (50/60 Hz) | the hard case: flux diversion with high-μ material (mu-metal), or shrink the victim loop |

**Where real shields leak:**
- **Apertures and seams** — a slot of length $\ell$ radiates like a slot antenna, efficiently once $\ell \sim \lambda/2$. Attenuation goes as the *longest dimension*, not the area: a thin 10 cm seam leaks like a 10 cm hole. Many small holes ≫ one long slot.
- Holes smaller than cutoff act as below-cutoff waveguides — deep honeycomb vents shield well because the evanescent decay is exponential in depth/diameter.
- **Cable penetrations** — an unfiltered wire through the wall carries the interference straight in; shield the cable to the chassis at the entry (360°, no pigtails) or filter there.
- Mu-metal saturates in strong fields and loses μ when bent or machined (needs re-annealing).

> [!question]- Your RF-tight box has a 12 cm ventilation slot. Around what frequency does it stop being RF-tight?
> When the slot approaches λ/2: λ ≈ 24 cm → ~1.2 GHz it radiates like a proper slot antenna; leakage is already significant an octave or two below. Break the slot into short segments with screws/gasket every few cm.

# Connections

- [[Skin Depth]] — sets the absorption term and why thin walls are fine at RF but useless at 60 Hz
- [[Waveguides]] — below-cutoff evanescence is the design principle for honeycomb vents and viewing holes
- [[Antennas]] — a seam is a slot antenna; Babinet reciprocity of the leak
- [[Grounding and Shielding Practice]] — how to actually connect the shield without ruining it (pigtails, one end vs both)
- [[Noise Coupling Mechanisms]] — shielding addresses the capacitive and radiated rows, not common-impedance coupling

---
Source: Jackson, *Classical Electrodynamics*, §8.1; practical layer: Ott, *Electromagnetic Compatibility Engineering*, Ch. 6
