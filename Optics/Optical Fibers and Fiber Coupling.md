#optics

**A single-mode fiber transmits exactly one transverse mode — a near-Gaussian of fixed size — so it's simultaneously a delivery pipe, an alignment reference, and a perfect spatial filter.**

# Reference

**Single-mode condition:** $V = \frac{2\pi a}{\lambda}\,\mathrm{NA} < 2.405$, with $\mathrm{NA} = \sqrt{n_{\rm core}^2 - n_{\rm clad}^2}$ (typically 0.10–0.14). Below cutoff wavelength the fiber goes multimode; far above it, guiding gets weak and bend loss grows.

**Mode field diameter (MFD):** the $1/e^2$ mode size — e.g. ~5 µm at 780 nm, ~10.4 µm at 1550 nm (SMF-28). Coupling target: focused waist $w_0 = \mathrm{MFD}/2$ at the tip. Divergence out of the fiber: $\theta \approx \lambda/\pi w_0$, i.e. NA-scale — collimation lens $f \approx w_{\rm desired}/\theta$.

**PM fiber:** stress rods (PANDA/bow-tie) create strong deliberate birefringence, so the two axes decouple. **Launch polarization aligned to an axis** or the output polarization wanders with temperature and bend (beat length ~mm; the two axes accumulate relative phase fast). Check by heating the fiber and watching output polarization stability through a polarizer.

**Connectors:** FC/PC — flat-ish polish, ~−40 dB return loss and the 4% tip reflection goes straight back at you. **FC/APC — the 8° angle sends the reflection into the cladding (~−60 dB): it kills etalon fringes and laser feedback.** Never mate PC to APC (air gap, huge loss). Angled tips also steer the output beam by ~4°, budget for it in collimator alignment.

**Coupling recipe:** collimate → match mode with correct aspheric → walk two mirrors (near = position, far = angle) maximizing transmitted power; then tweak the coupling lens $z$. 70–85% routine, >90% with matched aspheric and clean $M^2 \approx 1$ beam.

> [!question]- Your fiber-coupled diode laser shows intensity fringes drifting with lab temperature. Likely culprit and fix?
> An etalon between two PC (flat) surfaces — fiber tip and some other reflector — or feedback into the diode. Replace with APC connectors (angle kills the retro-reflection) and/or add an optical isolator at the laser.

# Connections

- [[Mode Matching]] — coupling is overlap with the fiber's Gaussian-ish mode; the recipe lives there
- [[Total Internal Reflection and Brewster Angle]] — guiding is TIR at the core-cladding index step
- [[Optical Isolators]] — the other half of the back-reflection defense
- [[Birefringence]] — PM fiber is stress birefringence used on purpose
- [[Beam Quality M2]] — the fiber transmits only the fundamental-mode fraction of a dirty beam

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 9
