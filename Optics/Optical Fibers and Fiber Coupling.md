#optics

**A single-mode fiber transmits exactly one transverse mode — a near-Gaussian of fixed size — so it's simultaneously a delivery pipe, an alignment reference, and a perfect spatial filter.**

# Reference

**Single-mode condition:** $V = \frac{2\pi a}{\lambda}\,\mathrm{NA} < 2.405$, with $\mathrm{NA} = \sqrt{n_{\rm core}^2 - n_{\rm clad}^2}$ (typically 0.10–0.14). Below cutoff wavelength the fiber goes multimode; far above it, guiding gets weak and bend loss grows.

**Picture:** a narrow glass guide that accepts only light matching its one mode shape: anything else leaks into the cladding, so the output is a clean near-Gaussian however messy the input.

**Mode field diameter (MFD):** the $1/e^2$ mode size — e.g. ~5 µm at 780 nm, ~10.4 µm at 1550 nm (SMF-28). Coupling target: focused waist $w_0 = \mathrm{MFD}/2$ at the tip. Divergence out of the fiber: $\theta \approx \lambda/\pi w_0$, i.e. NA-scale — collimation lens $f \approx w_{\rm desired}/\theta$.

**PM fiber:** stress rods (PANDA/bow-tie) create strong deliberate birefringence, so the two axes decouple. **Launch polarization aligned to an axis** or the output polarization wanders with temperature and bend (beat length ~mm; the two axes accumulate relative phase fast). Check by heating the fiber and watching output polarization stability through a polarizer.

**Connectors:** FC/PC — flat-ish polish, ~−40 dB return loss and the 4% tip reflection goes straight back at you. **FC/APC — the 8° angle sends the reflection into the cladding (~−60 dB): it suppresses etalon fringes and laser feedback.** Never mate PC to APC (air gap, huge loss). Angled tips also steer the output beam by ~4°, budget for it in collimator alignment.

**Coupling into a single-mode fiber — the steps and why:**

1. **Choose the lens to match the mode.** The fiber accepts only its own mode, so the focused waist must equal the mode radius: for a collimated beam of radius $w_{\text{in}}$, a lens of focal length $f = \pi w_{\text{in}} w_m/\lambda$, with $w_m$ = MFD/2 ([[Numerical Aperture and Spot Size]]). Alignment cannot fix a wrong lens; it caps the efficiency.
2. **Get a first signal.** The core is a few µm across, so start from rough overlap: send light backward out of the fiber (a visible laser into its far end, or the beam itself from a second coupler) and overlap the outgoing and incoming beams along the entire path. When they overlap in both position and angle, some light already couples.
3. **Walk the beam.** Two steering mirrors before the lens set where the focus lands on the fiber face and at what angle the light arrives. Tilting the mirror nearer the lens mainly moves the focus across the face; tilting the farther mirror moves the focus *and* changes the arrival angle. So the maximum is found by walking: tilt the far mirror slightly (the power drops because the focus moved), bring the focus back with the near mirror, and see whether the recovered maximum is higher than before; keep stepping in the direction that raises it, then repeat in the other axis.
4. **Focus last.** Adjust the lens-to-fiber distance (the waist position) and re-walk; this variable couples to the others, so it is optimized at the end.

What you watch: the power out of the far end. Efficiency that climbs to a plateau no walking improves says the limit is mode matching — lens choice, beam quality, aberration — not alignment. 70–85% routine, >90% with matched aspheric and clean $M^2 \approx 1$ beam.

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| coupling capped below ~60% | wrong lens focal length, $M^2 > 1$, or aberrations | a plateau no walking improves |
| coupling drifts down over hours | mounts relax and expand thermally; the fiber tip shifts in its connector | slow decline, recovered by re-walking |
| output polarization wanders (non-PM fiber) | bends and temperature change the fiber's stress birefringence | polarization after the fiber changes with temperature or when the fiber is touched |
| poor extinction from PM fiber | input polarization not on a fiber axis | output polarization moves when the fiber is warmed (the check above) |
| etalon fringes | flat (PC) tips form a cavity with other reflectors | intensity fringes drifting with temperature (question below) |
| dirty or damaged end face | a particle blocks the core; at high power it absorbs and burns the face | low transmission, a burned pit visible under a fiber microscope ([[Handling Lab Hardware]]) |
| bend loss | bends tighter than the specified radius let light escape the core | loss, larger at longer wavelengths |
| UV darkening | UV light creates absorbing defects in silica | transmission falling over hours in UV fiber unless it is made for UV |
| stimulated Brillouin scattering | at high power and narrow linewidth, light scatters backward off sound waves it generates | transmitted power saturates while back-reflected power rises |

> [!question]- Your fiber-coupled diode laser shows intensity fringes drifting with lab temperature. Likely culprit and fix?
> An etalon between two PC (flat) surfaces — fiber tip and some other reflector — or feedback into the diode. Replace with APC connectors (the angle removes the retro-reflection) and/or add an optical isolator at the laser.

# Connections

- [[Mode Matching]] — coupling is overlap with the fiber's Gaussian-ish mode; the recipe lives there
- [[Total Internal Reflection and Brewster Angle]] — guiding is TIR at the core-cladding index step
- [[Optical Isolators]] — the other half of the back-reflection defense
- [[Birefringence]] — PM fiber is stress birefringence used on purpose
- [[Beam Quality M2]] — the fiber transmits only the fundamental-mode fraction of a multimode beam
- [[Numerical Aperture and Spot Size]] — acceptance NA vs the mode-field diameter, and the lens that matches them
- [[Handling Lab Hardware]] — end-face care, inspection, and bend radius
- [[Fiber Noise Cancellation]] — the phase noise a fiber adds, and how it is cancelled

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 9
