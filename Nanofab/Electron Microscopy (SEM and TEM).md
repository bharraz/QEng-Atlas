#nanofab #characterization

**Image with electrons instead of light: SEM rasters a focused beam over a surface and collects what comes back off the top; TEM shoots the beam through a thinned sample and images what gets through.** Electrons win because their wavelength is picometers — diffraction never limits you. What limits you instead is where the electrons *go* once inside the sample, and that one idea explains most of both instruments' behavior.

# Reference

De Broglie wavelength of an accelerated electron:

$$\lambda = \frac{h}{\sqrt{2 m_e e V}} \approx \frac{1.23\ \text{nm}}{\sqrt{V\,[\text{V}]}}$$

— 12 pm at 10 kV. Electron lenses are so aberrated that real resolution sits 10³–10⁵ above λ, but that still lands at nanometers to sub-Ångström.

## SEM

The beam enters the sample and scatters into a pear-shaped **interaction volume** — up to ~1 µm across at 30 kV — and different signals escape from different depths of it:

- **Secondary electrons** (a few eV, knocked out of atoms) can only escape from the top few nm — so they carry *surface* information. Their yield depends on how much of the interaction volume sits near a surface, which is why edges and slopes glow: topographic contrast.
- **Backscattered electrons** (keV, reflected by nuclei) escape from deeper; the backscatter probability grows with atomic number, so BSE images are composition (Z-contrast) maps.
- **Characteristic X-rays** escape from the whole pear → EDS elemental analysis, but with the pear's µm-scale resolution, not the beam's.

Because signal generation needs nothing but the beam hitting the surface, sample prep is nearly nil and you image in minutes; the small beam convergence angle gives enormous depth of field (the "3D look"). The costs come from the same physics: the beam *injects charge*, so insulators accumulate potential that deflects the beam and blooms the image (fix: nm of sputtered Au/C, or low kV so injected ≈ emitted current); and the dose is real — resists expose, gate oxides trap charge — inspecting a device is not free ([[Lithography|an EBL tool is literally this instrument writing instead of reading]]). Lowering kV shrinks the interaction volume, which *sharpens* surface detail even as the optics get worse — the practical resolution is the escape volume, not the spot.

## TEM

Thin the sample below ~100 nm — now the interaction volume argument is moot because there is no bulk to scatter into; electrons at 80–300 kV pass through, and you image with what emerges. Contrast comes from diffraction and phase: crystalline regions redirect intensity into Bragg spots ([[Crystal Diffraction]] with a nanometer-sized, tunable-camera-length probe — you can take a diffraction pattern of a single grain), and phase interference resolves atomic columns (< 1 Å with aberration correction). Cross-sections show buried interfaces and layer thicknesses as directly as a photograph — the ground truth against which the [[Surface and Film Metrology|indirect tools]] are calibrated.

Everything hard about TEM is the sample: getting your one device thinned to electron transparency (FIB liftout + milling, a day of skilled work, destructive by construction), after which you have statistics-of-one from a µm² region. And 300 keV is above the knock-on threshold of most lattices — the microscope damages the very structure it resolves; dose management is part of the measurement.

**Cousins, one line each:** **STEM** — TEM operated as a scanned nm probe; annular dark-field signal ∝ Z², atoms counted one column at a time. **FIB** — an SEM column plus a Ga⁺ ion column: the ions mill rather than image, cutting cross-sections and TEM lamellae site-specifically (and implanting Ga into whatever remains — not innocent either). **EELS** — energy loss of transmitted electrons: composition and bonding at the STEM probe position.

> [!question]- Why can EDS in an SEM report "10% of element X" from a region that SE imaging shows is only 50 nm wide?
> The two signals come from different volumes. Secondary electrons escape only from the top few nm near the beam — nm-scale image. The X-rays that EDS collects are generated throughout the full µm-scale interaction pear, mostly *below and around* the feature — so the spectrum is dominated by the substrate and surroundings, not the 50 nm object you think you're pointing at. Quantitative EDS on nanostructures needs either low kV (shrink the pear) or a thinned sample in STEM (remove the bulk entirely).

# Connections

- [[Lithography]] — same beam, same scattering physics; the interaction pear *is* the proximity effect
- [[Crystal Diffraction]] — TEM diffraction patterns are Bragg's law on a single grain
- [[Surface and Film Metrology]] — the non-destructive tools TEM cross-sections calibrate
- [[Thin-Film Deposition]] — layer-stack ground truth via cross-section

---
Source: Goldstein et al., *Scanning Electron Microscopy and X-Ray Microanalysis*; Williams & Carter, *Transmission Electron Microscopy*
