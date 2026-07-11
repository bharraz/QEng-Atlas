#optics

**A waveplate delays one linear polarization component relative to the orthogonal one by a fixed phase** — λ/2 (π) reflects polarization about its fast axis, λ/4 (π/2) converts linear ↔ circular when at 45°.

# Reference

Retardance $\Gamma = 2\pi(n_e - n_o)\,d/\lambda$ from birefringent thickness $d$.

**λ/2 plate:** linear in at angle $\theta$ to fast axis → linear out at $-\theta$ (i.e. **rotated by $2\theta$**). Rotate the plate by $\alpha$, polarization rotates by $2\alpha$. The standard power-control knob: HWP + polarizing beamsplitter gives $\cos^2 2\alpha$ splitting. Also flips circular handedness.

**λ/4 plate:** linear at 45° to fast axis → circular; circular → linear at 45°. At other angles: elliptical. Double-pass through a QWP (mirror behind it) = HWP — the trick in double-pass AOMs and optical isolator substitutes.

**Zero-order vs multi-order:** a true λ/2 of quartz is fragile-thin, so plates are cut with $\Gamma = 2\pi m + \pi$. Multi-order (large $m$): retardance error scales with $m$ — **strongly temperature- and wavelength-sensitive** (quartz multi-order can drift a few degrees of retardance per °C). Zero-order (compound: two plates subtracted, or true zero-order) is what you want on anything that matters. Achromatic (bimaterial) for multi-wavelength beams.

**Alignment gotcha:** finding the axis — rotate between crossed polarizers, nulls every 45°(HWP)/90°; distinguishing fast from slow axis needs a known reference or the wavelength dependence.

> [!question]- Why does a QWP double-passed (mirror retro-reflection) act as an HWP, and what's it for?
> Two passes accumulate π/2 + π/2 = π of retardance about the same fast axis (the mirror reverses $k$ but the crystal axes are unchanged in the transverse plane). Set at 45°, input linear → circular → reflected → orthogonal linear: the return beam exits the *other* port of a PBS. That's how double-pass AOM setups separate the return beam.

# Connections

- [[Jones Calculus]] — the matrices; compose waveplates by multiplication
- [[Birefringence]] — $n_e \ne n_o$ is the physical origin of retardance
- [[Polarization of EM Waves]] — the state space these devices rotate
- [[Acousto-Optic Modulator]] — the QWP double-pass trick in the standard double-pass configuration

---
Source: Hecht, *Optics*, Ch. 8
