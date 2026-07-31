#nanofab

**Lithography transfers a pattern into a radiation-sensitive polymer (resist): expose, develop, use the resist as a stencil for etching or deposition.** Every method answers the same two questions: how tightly the exposure is confined, and how far the deposited energy spreads in the resist and substrate afterward.

# Reference

Flow: spin resist → soft bake → expose → develop → etch/deposit → strip. **Positive** resist: exposure scissions chains, exposed regions dissolve. **Negative**: exposure crosslinks, exposed regions remain. Resist **contrast** $\gamma = [\log_{10}(D_{100}/D_0)]^{-1}$, where $D_0$ is the largest dose leaving the resist untouched and $D_{100}$ the smallest that fully clears it: a high-$\gamma$ resist switches over a narrow dose range, so even a blurred exposure profile develops into a sharp edge — the resist acts as a threshold that partially rescues imperfect optics.

## Photolithography

Resolution and depth of focus for projection optics:

$$R = k_1\frac{\lambda}{\mathrm{NA}}, \qquad \mathrm{DOF} = k_2\frac{\lambda}{\mathrm{NA}^2}, \qquad k_1 \approx 0.25\text{–}0.8.$$

$R$ = smallest printable half-pitch; NA = numerical aperture of the projection lens (sine of the half-angle of light it collects — its spatial-frequency bandwidth, [[Numerical Aperture and Spot Size]]); DOF = depth of focus, the vertical range over which the image stays sharp. A pattern of period $p$ diffracts light into orders at angles $\sin\theta = \lambda/p$; the lens must capture at least the first order to reconstruct the period at all — that geometric requirement is the resolution limit, and $k_1, k_2$ are order-unity factors absorbing resist contrast and tricks that squeeze below it (phase-shift masks, off-axis illumination). The $\mathrm{NA}^2$ in DOF is the price of resolution: focusing harder shortens the focal region quadratically.

Exposure geometries: **contact** (blur $\approx$ resist thickness scale; defects transfer to the mask every touch), **proximity** (gap $g$: blur $\sim\sqrt{\lambda g}$ — 1.9 µm at $\lambda = 365$ nm, $g = 10$ µm), **projection** (mask imaged through reduction optics; the production standard). Lab i-line contact tools: ~1 µm practical. Industry: 193 nm immersion (NA = 1.35 via water) → EUV at 13.5 nm.

Character: parallel exposure — whole wafer per flash, unmatched throughput; pattern frozen in a physical mask. Direct-write laser (scanned spot, ~0.6–1 µm) is the maskless lab default for coarse layers.

## Electron-beam lithography

10–100 keV electrons, $\lambda \sim$ pm: diffraction irrelevant, beam focus ~nm, pattern from a file. Resolution is set by where the energy goes after entry:

- **Forward scattering** broadens the beam through the resist by $\sim$ few nm (worse in thick resist; improves with kV).
- **Backscattering** returns electrons from µm deep in the substrate: the deposited-energy point-spread function is modeled as a double Gaussian,
$$f(r) \propto \frac{1}{\alpha^2}e^{-r^2/\alpha^2} + \frac{\eta}{\beta^2}e^{-r^2/\beta^2},$$
with $\alpha \sim$ 10 nm (forward), $\beta \sim$ 3 µm at 30 keV in Si (backscatter), $\eta \approx 0.5$–0.8. Dense patterns accumulate the $\beta$ background — **proximity effect** — corrected by solving for a per-shape dose map (a deconvolution against $f$).
- **Secondary electrons** generated in the resist blur chemistry over ~5 nm: the practical resolution floor (~10 nm) is exposure physics, not optics, and barely improves from 30 to 100 keV.
- **Charging** on insulating substrates deflects the beam; discharge layer (thin metal or conducting polymer) on top of the resist.

Serial writing: hours–days per wafer. Resist stack for lift-off: a faster-developing bottom layer (MMA under PMMA) self-forms an undercut; a suspended top-layer bridge over a wide undercut plus two-angle evaporation places overlapping electrodes with an oxidation step between — the Dolan-bridge Josephson junction, no alignment required.

**Others:** nanoimprint (stamped master: nm resolution, parallel; master made by EBL, defects replicate), laser interference lithography (periodic patterns over large areas).

| | photo (contact) | direct-write laser | EBL |
|---|---|---|---|
| resolution | ~1 µm | ~0.6–1 µm | ~10 nm |
| throughput | wafer/flash | ~min/wafer | hours–days |
| mask | required | none | none |

> [!question]- Why can exposing a denser pattern in EBL require a lower per-shape dose?
> Each shape receives its own dose plus the backscatter tails ($\beta \sim$ µm) of every neighbor. In a dense region the accumulated background is a significant fraction of the clearing dose, so the direct dose must be reduced to avoid overexposure; isolated features get the opposite correction. Proximity-effect correction is the deconvolution of the target dose against $f(r)$.

# Connections

- [[Etching]] — pattern transfer; etch selectivity dictates resist thickness
- [[Thin-Film Deposition]] — lift-off through the undercut stencil
- [[Electron Microscopy (SEM and TEM)]] — same beam and scattering physics, reading instead of writing
- [[Numerical Aperture and Spot Size]] — $R \propto \lambda/\mathrm{NA}$, $\mathrm{DOF} \propto \lambda/\mathrm{NA}^2$
- [[Quantum Dots]] / [[Superconducting Qubits]] — gate patterns and Dolan junctions

---
Source: Campbell, *Fabrication Engineering at the Micro- and Nanoscale*, Ch. 7–9; Franssila, *Introduction to Microfabrication*, Ch. 8–10
