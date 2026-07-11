#nanofab #characterization

**The non-destructive everyday toolbox: profilometry and AFM measure topography by touching it, ellipsometry infers film thickness from how a film changes reflected polarization, and XRD reads crystal structure from diffraction angles.** The organizing question for each: is the number measured *directly*, or inferred through a *model* — because model-based tools are fast and precise right up until the model is wrong.

# Reference

## Stylus profilometry — direct height measurement

A diamond stylus (µm-scale tip radius, µN force) is dragged in a line; its vertical motion is the surface profile. Height is measured against an interferometric or capacitive reference, so it's absolute and calibration is trivial — this is why "measure the step where the mask was" is the routine check of every etch depth and deposition.

The tip radius is the resolution limit, and it's geometric: the recorded profile is the surface *dilated by the tip shape*. A µm-radius sphere cannot enter a 100 nm trench at all, and reports every sharp step as a ramp with the tip's own radius. Lateral resolution ~µm; vertical resolution nm (limited by vibration, not the sensor). The µN contact force concentrated on the tip point can plow soft films (resists, polymers) — you're measuring with a plow. Optical profilometers do the same job interferometrically without contact and over a whole field at once, but they measure *optical* path: a transparent film adds phase from both surfaces, and the height map silently becomes wrong unless the film is modeled.

## AFM — the same idea at nN and nm

Shrink the tip to ~10 nm radius on a flexible cantilever, and detect force instead of position: either static deflection (contact mode) or the shift of the cantilever's resonance as the tip enters the force gradient (tapping/non-contact):

$$\Delta f \approx -\frac{f_0}{2k}\frac{\partial F}{\partial z}.$$

A feedback loop moves the sample vertically to hold the force signal constant; the feedback voltage *is* the topography. Because force detection works on any surface, AFM needs no conductivity, coating, or vacuum — the advantage over [[Electron Microscopy (SEM and TEM)|SEM]] for insulators and delicate samples. Sub-nm vertical resolution makes RMS roughness of a deposited film its bread-and-butter output; swap the tip and the same feedback maps magnetic force (MFM), surface potential (KPFM), or stiffness.

The limits are the probe's, and they're the same ones as profilometry scaled down: the image is surface ⊗ tip, so a blunt or doubled tip prints its own shape into every feature (the classic artifact: identical ghost shapes repeated across the image — that's your tip, imaged by the sample). Serial scanning through a mechanical feedback loop means minutes per frame and ≲100 µm fields, and the tip only knows the top surface — nothing buried is visible.

## Ellipsometry — thickness by model fit

Reflect polarized light off the film; p- and s-polarizations reflect with different amplitude and phase (they see different boundary conditions), and interference between the top-surface and film-bottom reflections encodes the film thickness in that difference. Measure the complex ratio

$$\rho = \frac{r_p}{r_s} = \tan\Psi\; e^{i\Delta},$$

then fit a stack model — layer thicknesses and refractive indices — until it reproduces $(\Psi, \Delta)$ across wavelength. Phase is exquisitely sensitive, so thickness precision reaches Ångströms in seconds, non-contact: the standard readout for oxides, nitrides, resists, ALD films.

But the thickness is a *fit parameter*, not a measurement. The data constrain the product of thickness and optical path; if the film's real index differs from the model's (porosity, hydrogen in PECVD films, hydration in ALD films), the fit converges happily to a wrong thickness with small residuals — confidently wrong is the signature failure. Cross-check against a direct method whenever the film is new. Opaque films are opaque to the method too: no light returns from the bottom interface, so metals thicker than the skin depth yield only optical constants, not thickness.

## XRD — structure without imaging

Bragg diffraction ($2d\sin\theta = n\lambda$, see [[Crystal Diffraction]]) from the film's lattice planes: peak *positions* give the lattice constants (and via their shift, strain), peak *identity* fingerprints the phase. Peak *width* measures how many planes diffract coherently — a grain of finite size $t$ truncates the interference sum, broadening the peak by the same Fourier logic that broadens the spectrum of a truncated pulse:

$$t \approx \frac{0.9\,\lambda}{\beta\cos\theta} \quad (\text{Scherrer}; \; \beta = \text{FWHM in rad}).$$

The beam averages over mm² — real statistics, the complement to TEM's statistics-of-one — but that is also the limitation: no spatial resolution, weak signal from thin films (grazing incidence increases path length in the film to compensate), and nothing at all from amorphous films, since there are no planes to diffract. For those, **XRR** (same tool, grazing incidence, watching interference fringes vs angle rather than diffraction) gives thickness, density, and roughness of any film, crystalline or not — it only needs interfaces, not order.

**Choosing:** step height → profilometer (direct, absolute); roughness or nm morphology → AFM (direct, slow); transparent-film thickness → ellipsometer (model-based, fast) sanity-checked by XRR (direct-ish, slower); crystallinity/strain/grain size → XRD; when tools disagree or the answer is buried → cross-section [[Electron Microscopy (SEM and TEM)|TEM]], the destructive ground truth.

> [!question]- Ellipsometry says your ALD alumina is 42 nm; XRR says 38 nm. Which do you believe, and what's actually wrong?
> XRR — its fringe spacing depends on thickness and (weakly) density, with no refractive-index assumption. The disagreement is telling you the film's index is lower than the textbook Al₂O₃ value in your ellipsometer model (low-temperature ALD films are commonly porous or hydrated); the ellipsometer honored its wrong index by inflating the thickness. The productive move: fix the thickness at the XRR value, refit ellipsometry for the index — now you've measured the porosity too, and calibrated the fast tool for the rest of the run.

# Connections

- [[Electron Microscopy (SEM and TEM)]] — the destructive escalation path and ground truth
- [[Crystal Diffraction]] — the physics under XRD and XRR
- [[Thin-Film Deposition]] — what these tools qualify, film by film
- [[Etching]] — depth and profile verification
- [[FFT in Practice]] — Scherrer broadening is spectral leakage of a truncated lattice

---
Source: Ohring, *Materials Science of Thin Films*, Ch. 10; Fujiwara, *Spectroscopic Ellipsometry*; Birkholz, *Thin Film Analysis by X-Ray Scattering*
