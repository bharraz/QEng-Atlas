#nanofab #characterization

**Profilometry and AFM measure topography by contact; ellipsometry infers thickness from polarized reflection; XRD reads structure from diffraction angles. The organizing distinction: direct measurements vs model-based fits — the latter are fast and precise until the model is wrong.**

# Reference

## Stylus profilometry

Diamond tip (µm radius, µN force) dragged in a line; height measured interferometrically — absolute, calibration-free. The recorded profile is the surface dilated by the tip: lateral resolution ~ tip radius (a µm sphere cannot enter a 100 nm trench; steps become ramps of the tip's own shape). Vertical: nm (vibration-limited). µN on a point contact plows soft films. The routine check of every etch depth and deposition (measure the masked step). Optical profilometers: non-contact, full-field, but measure *optical* path — transparent films silently corrupt the height map unless modeled.

## AFM

Tip (~10 nm radius) on a cantilever; contact mode holds deflection constant, tapping/non-contact holds the resonance shift constant:

$$\Delta f \approx -\frac{f_0}{2k}\frac{\partial F}{\partial z},$$

with $f_0$ the cantilever's free resonance frequency, $k$ its spring constant, and $\partial F/\partial z$ the gradient of the tip–surface force: an attractive gradient effectively softens the spring and pulls the resonance down. The feedback holds $\Delta f$ (or the oscillation amplitude) constant by moving the sample vertically, and that feedback voltage is the topography. Works on insulators in air (no coating/vacuum — the advantage over [[Electron Microscopy (SEM and TEM)|SEM]]). Sub-nm vertical: RMS roughness of films is the standard output. Variants map the force channel: MFM (magnetic), KPFM (surface potential), force curves (mechanics).

Limits: image = surface ⊗ tip (a doubled tip prints repeated ghost shapes — the sample imaging the tip); minutes per frame, ≲100 µm fields; top surface only.

## Ellipsometry

$p$ and $s$ polarizations reflect differently; interference between top- and bottom-interface reflections encodes thickness in the complex ratio

$$\rho = \frac{r_p}{r_s} = \tan\Psi\, e^{i\Delta},$$

where $r_p, r_s$ are the complex reflection coefficients for polarization in and perpendicular to the plane of incidence, $\tan\Psi$ their amplitude ratio, and $\Delta$ their relative phase — the phase is where the Å-level thickness sensitivity lives. Fit a layer model (thicknesses, refractive indices) to $(\Psi, \Delta)$ vs wavelength. Phase sensitivity → Å-level thickness in seconds, non-contact: the standard readout for oxides, nitrides, resists, ALD films.

Thickness is a **fit parameter**: the data constrain (thickness × index), so a wrong model index (porosity, hydrogen in PECVD films, hydration in ALD) converges to a wrong thickness with small residuals. Cross-check new films against a direct method. Opaque films return only optical constants — no light from the bottom interface.

## XRD / XRR

Bragg peaks ($2d\sin\theta = n\lambda$, [[Crystal Diffraction]]): positions → lattice constants and strain; identity → phase; width → coherently diffracting size via Scherrer,

$$t \approx \frac{0.9\,\lambda}{\beta\cos\theta},$$

$t$ = coherently diffracting crystallite size (nm; a lower bound on grain size — strain broadens too); $\lambda$ = X-ray wavelength (nm; 0.15406 for Cu Kα); $\beta$ = peak FWHM in **radians**, instrument broadening subtracted; $\theta$ = Bragg angle. Since $t \propto 1/\beta$, halving the grain size doubles the peak width — fewer coherent planes, broader peak, the same inverse relation as

the Fourier width of a truncated lattice ([[Fourier Transform]]). Averages over mm² — the statistical complement to TEM. Thin films: grazing incidence for path length; amorphous films show nothing in XRD but everything in **XRR** — grazing-incidence interference fringes with spacing $\Delta\theta \approx \lambda/2t$ give thickness, density, and roughness of any film with interfaces, crystalline or not, model-light.

| quantity | tool | direct? |
|---|---|---|
| step height, etch depth | profilometer | yes |
| roughness, nm morphology | AFM | yes (⊗ tip) |
| transparent-film thickness | ellipsometer | model fit |
| thickness/density, any film | XRR | fringe spacing |
| phase, strain, grain size | XRD | yes |
| buried structure | cross-section TEM | destructive ground truth |

> [!question]- Ellipsometry reports 42 nm of ALD alumina; XRR reports 38 nm. Which is right, and what is the discrepancy worth?
> XRR — fringe spacing depends on thickness with no index assumption. The gap means the film's index is below the model value (porous or hydrated low-temperature ALD); the ellipsometer honored its wrong index by inflating thickness. Fix the thickness at the XRR value and refit ellipsometry for the index: the discrepancy has now measured the film porosity and calibrated the fast tool for the rest of the run.

# Connections

- [[Electron Microscopy (SEM and TEM)]] — the destructive escalation
- [[Crystal Diffraction]] — the physics under XRD/XRR
- [[Thin-Film Deposition]] — what these tools qualify
- [[Etching]] — depth and profile verification

---
Source: Ohring, *Materials Science of Thin Films*, Ch. 10; Fujiwara, *Spectroscopic Ellipsometry*; Birkholz, *Thin Film Analysis by X-Ray Scattering*
