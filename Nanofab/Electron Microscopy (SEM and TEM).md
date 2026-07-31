#nanofab #characterization

**SEM rasters a focused beam over a surface and collects what comes back; TEM transmits the beam through a ≲100 nm foil and images what passes. Electron wavelengths are picometers, so diffraction never limits resolution — the interaction volume in the sample does.**

# Reference

$$\lambda = \frac{h}{\sqrt{2m_e eV}} \approx \frac{1.23\ \mathrm{nm}}{\sqrt{V\,[\mathrm{V}]}} \quad (12\ \mathrm{pm\ at\ 10\ kV}).$$

Electron lenses are aberration-dominated; real resolution sits $10^3$–$10^5 \times \lambda$.

## SEM

The beam scatters into a pear-shaped **interaction volume**; its size follows the Kanaya–Okayama range,

$$R_{KO} \approx \frac{27.6\, A\, E^{1.67}}{Z^{0.89}\rho}\ \mathrm{nm} \quad \sim 1\ \mu\mathrm{m\ in\ Si\ at\ 10\ kV},$$

with $E$ the beam energy in keV, $A$ the atomic weight, $Z$ the atomic number, $\rho$ the density in g/cm³. Read the scalings: higher energy penetrates much deeper ($E^{1.67}$ — the electron outruns its stopping power), heavier/denser targets stop it shorter. Different signals escape from different depths of this volume, which is why one beam produces several images:

| signal | escape depth | carries | contrast |
|---|---|---|---|
| secondary electrons (few eV) | ~1–10 nm | topography | edges/slopes bright |
| backscattered electrons (keV) | ~$R_{KO}/3$ | composition | yield rises with $Z$ |
| characteristic X-rays (EDS) | full volume | elemental ID | µm-scale resolution regardless of spot |

Practical consequences: resolution is the escape volume, not the spot — **lowering kV sharpens surface detail** (smaller pear) even as the optics degrade; insulators charge (coat with nm of Au/C, or run low kV where injected ≈ emitted current); the beam dose is real — resists expose, oxides trap charge ([[Lithography|an EBL tool is this instrument writing]]). Depth of field is large (small convergence angle). Minutes from sample to image.

## TEM

Thinning below ~100 nm deletes the interaction volume; 80–300 keV electrons transmit. Contrast from diffraction (crystalline regions redirect intensity into Bragg spots — [[Crystal Diffraction]] with a nm-sized probe, per-grain diffraction patterns) and phase interference (< 1 Å with aberration correction; atomic columns). Cross-sections give layer thicknesses and buried interfaces directly — the calibration ground truth for [[Surface and Film Metrology|the indirect tools]].

Costs: sample prep is the job (FIB liftout + thinning, ~a day, destructive); sampled volume ~µm² (statistics of one); 300 keV exceeds knock-on thresholds — the measurement damages the lattice, and dose management is part of it.

**Variants:** STEM — TEM as a scanned nm probe, annular dark field ∝ $Z^2$, atom-column counting; FIB — Ga⁺ column for site-specific cross-sections and TEM lamellae (implants Ga into what remains); EELS — energy loss at the probe position: composition and bonding.

> [!question]- SE imaging shows a 50 nm feature, but EDS on the same spot reports mostly substrate. Why?
> Different escape volumes. SE come from the top few nm near the beam (nm-scale image); EDS X-rays are generated throughout the µm-scale pear, which is mostly substrate below and around the feature. Quantitative EDS on nanostructures requires shrinking the pear (low kV) or removing the bulk (thinned sample in STEM).

# Connections

- [[Lithography]] — EBL: the same column and the same scattering pear, writing
- [[Crystal Diffraction]] — TEM diffraction is Bragg's law on a single grain
- [[Surface and Film Metrology]] — the non-destructive complement
- [[Thin-Film Deposition]] — cross-section TEM as layer-stack ground truth

---
Source: Goldstein et al., *Scanning Electron Microscopy and X-Ray Microanalysis*; Williams & Carter, *Transmission Electron Microscopy*
