#optics

**A waveplate delays one linear polarization component relative to the orthogonal one by a fixed phase** — λ/2 (π) reflects polarization about its fast axis, λ/4 (π/2) converts linear ↔ circular when at 45°.

# Reference

Retardance $\Gamma = 2\pi(n_e - n_o)\,d/\lambda$ from birefringent thickness $d$.

**Picture:** on the Poincaré sphere a waveplate rotates the polarization point about the axis set by its fast axis, by an angle equal to its retardance.

**λ/2 plate:** linear in at angle $\theta$ to fast axis → linear out at $-\theta$ (i.e. **rotated by $2\theta$**). Rotate the plate by $\alpha$, polarization rotates by $2\alpha$. The standard power-control knob: HWP + polarizing beamsplitter gives $\cos^2 2\alpha$ splitting. Also flips circular handedness.

**λ/4 plate:** linear at 45° to fast axis → circular; circular → linear at 45°. At other angles: elliptical. Double-pass through a QWP (mirror behind it) = HWP — used in double-pass AOMs and as an optical isolator substitute.

**Zero-order vs multi-order:** a true λ/2 of quartz is fragile-thin, so plates are cut with $\Gamma = 2\pi m + \pi$. Multi-order (large $m$): retardance error scales with $m$ — **strongly temperature- and wavelength-sensitive** (quartz multi-order can drift a few degrees of retardance per °C). Zero-order (compound: two plates subtracted, or true zero-order) is what you want on anything that matters. Achromatic (bimaterial) for multi-wavelength beams.

**Alignment:** finding the axis — rotate between crossed polarizers, nulls every 45°(HWP)/90°; distinguishing fast from slow axis needs a known reference or the wavelength dependence.

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| used at the wrong wavelength | retardance scales as $1/\lambda$, and for a multi-order plate the error is multiplied by the order | a half-wave plate no longer gives a full null after a polarizer; leakage that rotating the plate cannot remove |
| temperature drift (multi-order plates) | birefringence and thickness change with temperature, and the large total retardance amplifies the change | slow drift of the power split after a polarizing beamsplitter |
| tilted plate | path length and effective birefringence change with the angle of incidence | retardance error (a deliberate tilt is also used to fine-tune a plate) |
| reflections from the faces | each uncoated quartz surface reflects ~4.5% ([[Fresnel Equations]]); anti-reflection coatings work only over their design band | ghost beams, power loss, light sent back toward the laser |
| etalon between the faces | the two parallel faces form a weak Fabry–Pérot | transmission and retardance that oscillate with temperature and wavelength; a slight tilt or a wedged plate suppresses it |
| cemented zero-order plate in the UV or at high power | the adhesive between the two plates absorbs and degrades | darkening or damage; air-spaced or optically contacted plates avoid it |
| mount stress | clamping adds stress birefringence ([[Birefringence]]) | retardance error that varies across the aperture |
| trusting the engraved axis mark | the mark is placed only to about a degree | set the axis by measurement (above) wherever the extinction matters |

**Polarizers and polarizing beamsplitters,** which every waveplate setup relies on, have their own limits:

| Limit | Mechanism | Consequence |
|---|---|---|
| the reflected port is less pure than the transmitted port | a cube's dielectric coating transmits p-polarization almost completely but reflects a few percent of it along with the s-polarization | transmitted extinction is typically above 1000:1, reflected only ~20–100:1; take the transmitted port when purity matters, or add a polarizer after the reflected one |
| limited angle and wavelength range | the coating separates polarizations only near its design angle and band | extinction degrades for strongly converging beams, tilted cubes, or other wavelengths |
| cemented cubes at high power or in the UV | the glue layer absorbs | damage; optically contacted cubes or plate polarizers avoid it |
| reflections from the cube faces | flat faces at normal incidence | ghosts and feedback into the laser; tilt the cube slightly |

> [!question]- Why does a QWP double-passed (mirror retro-reflection) act as an HWP, and what's it for?
> Two passes accumulate π/2 + π/2 = π of retardance about the same fast axis (the mirror reverses $k$ but the crystal axes are unchanged in the transverse plane). Set at 45°, input linear → circular → reflected → orthogonal linear: the return beam exits the *other* port of a PBS. That's how double-pass AOM setups separate the return beam.

# Connections

- [[Jones Calculus]] — the matrices; compose waveplates by multiplication
- [[Birefringence]] — $n_e \ne n_o$ is the physical origin of retardance
- [[Polarization of EM Waves]] — the state space these devices rotate
- [[Acousto-Optic Modulator]] — the QWP double pass in the standard double-pass AOM configuration
- [[Fresnel Equations]] — the ~4% reflection per uncoated surface

---
Source: Hecht, *Optics*, Ch. 8
