#optics

**Add fields, not intensities: the cross term $2\sqrt{I_1 I_2}\cos\Delta\phi$ is interference** — visible only while the two paths stay phase-correlated (coherent) and share polarization.

# Reference

$$
I = I_1 + I_2 + 2\sqrt{I_1 I_2}\cos\Delta\phi, \qquad \Delta\phi = k\,\Delta L
$$

**Visibility (contrast):**
$$
V = \frac{I_{\max} - I_{\min}}{I_{\max} + I_{\min}} = \frac{2\sqrt{I_1 I_2}}{I_1 + I_2}\,|\gamma_{12}|
$$
Balanced intensities give the first factor = 1; $|\gamma_{12}|$ is the degree of mutual coherence — it decays as path difference approaches the coherence length. Fringes fade, they don't stop abruptly.

**Coherence length:**
$$
\ell_c = \frac{c}{\Delta\nu}
$$
Numbers: free-running diode laser ($\Delta\nu \sim 1$ MHz) → 300 m; He-Ne (~1 GHz multimode) → 30 cm; LED ($\Delta\nu \sim 10$ THz) → 30 µm. Rule: interferometers with path mismatch $\gg \ell_c$ show no fringes — which is also a *feature* (white-light fringes locate zero path difference to µm; unwanted etalons vanish for broadband light).

**Requirements checklist when fringes are missing:** path difference $< \ell_c$; polarizations parallel (crossed pol → zero cross term — the classic silent killer after a fiber); spatial overlap and matched wavefronts (mismatched curvature = bullseye rings, tilt = straight fringes); detector faster than any relative phase drift, or fringes average away.

> [!question]- Your Mach-Zehnder shows weak fringes ($V \approx 0.3$) with balanced arms and equal powers. Top two suspects?
> Polarization mismatch between arms (check with a polarizer at the output — visibility restored means one arm's polarization rotated, e.g. by mirror phase shifts or fiber) and transverse mode/wavefront mismatch (fringe pattern shows rings or high spatial frequency — fix mode overlap). Coherence is exonerated by the balanced arms.

# Connections

- [[Two-Beam Interferometers]] — the standard geometries that turn phase into intensity
- [[Laser Linewidth]] — sets $\Delta\nu$, hence $\ell_c$ and how far arms can be unbalanced
- [[Fourier Transform]] — fringe visibility vs delay is the FT of the source spectrum (Wiener-Khinchin for light)
- [[Heterodyne Detection]] — interference with a frequency offset: the fringe becomes an RF beat

---
Source: Hecht, *Optics*, Ch. 9, 12
