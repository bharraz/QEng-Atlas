#nanofab

**Lithography transfers a pattern into a radiation-sensitive polymer (resist): expose, develop, then use the resist as a stencil for etching or deposition.** Everything downstream inherits its resolution and alignment. The physics of every litho method is the same question twice: how tightly can you confine the exposure, and how far does the energy spread once it's in the resist and substrate?

# Reference

**The universal flow:** spin-coat resist → soft bake → expose → develop → (etch or deposit) → strip. Exposure changes the polymer's solubility: **positive resist** — radiation breaks chains, exposed regions dissolve; **negative resist** — radiation crosslinks chains, exposed regions stay.

## Photolithography

UV light projects a mask onto the resist. The confinement limit is diffraction: light passing an aperture of size ~λ spreads, so the sharpest printable feature is

$$R = k_1 \frac{\lambda}{\mathrm{NA}},$$

where NA is the numerical aperture of whatever optics recollect the diffracted orders (you need at least the first order to reconstruct any spatial information — lose it and the pattern is gone), and $k_1 \approx 0.25$–0.8 encodes process cleverness (resist contrast, phase-shift masks, off-axis illumination). Lab contact aligners at $\lambda = 365$ nm print ~1 µm reliably; industry got to 193 nm immersion and then EUV (13.5 nm) by attacking λ directly.

The three exposure geometries differ in how they manage diffraction: **contact** (mask touches resist — diffraction has no distance to spread, best resolution for a simple tool, but every touch transfers defects to mask and wafer, which is why the mask degrades and why production abandoned it); **proximity** (small gap $g$ — spreading over the gap costs you, blur $\sim \sqrt{\lambda g}$); **projection/stepper** (image the mask through reduction optics — resolution set by NA, mask flies clean, the production standard).

Character of the method: the entire wafer exposes in one flash, so throughput is essentially unbeatable and cost-per-device tiny — but the pattern is frozen into a physical mask that takes days/weeks and real money to change. Photolitho is what you use when the design is settled or the features are coarse.

## Electron-beam lithography (EBL)

Replace photons with 10–100 keV electrons: λ is picometers, so diffraction is irrelevant and the beam focuses to ~nm. Being a serial scanned probe, it needs no mask — the pattern is a file, and design-to-device is same-day. That combination (resolution + agility) makes it the research workhorse for gate-defined [[Quantum Dots]], Josephson junctions, photonic crystals.

What limits it is not the spot but **where the electrons go afterward**. A keV electron doesn't stop in the 100 nm resist; it plows into the substrate and scatters:

- **Forward scattering** — small-angle deflections on the way through the resist broaden the written line by a few nm (worse in thick resist, better at high kV where the beam stiffens).
- **Backscattering** — a fraction of electrons return from deep in the substrate and re-expose the resist over a radius of *microns* (at 30 keV, ~3 µm in Si). Every shape you write sprays background dose over its whole neighborhood: the **proximity effect**. Dense patterns accumulate this background, so correct exposure requires solving for a dose map — isolated features get more, crowded ones less — before writing (proximity-effect correction is a deconvolution done in the pattern file).
- **Charging** — on insulating substrates (glass, GaAs, diamond) the injected charge has nowhere to go; the accumulated field deflects the incoming beam and warps the pattern. Fix: a nm-scale metal or conducting-polymer discharge layer on top of the resist.

The costs are the mirror of the benefits: serial writing means hours-to-days per wafer (fine for twenty devices, absurd for production), and the machine time is expensive.

**Two-layer resists and the undercut.** For lift-off (see [[Thin-Film Deposition]]) you *want* the resist profile to overhang, so the deposited film breaks at the edge. Standard trick: a bottom layer that develops faster (more sensitive copolymer, e.g. MMA under PMMA) automatically develops wider than the top — a self-formed undercut. A free-standing bridge of top-layer resist over a wide undercut is the **Dolan bridge**: evaporate at two angles through it and the shadows place two overlapping electrodes with the oxide barrier grown between — a Josephson junction with no alignment step.

**Honorable mentions:** direct-write laser (a scanned focused laser spot: maskless like EBL, resolution ~0.6–1 µm like photolitho — the modern lab default for coarse layers and mask-making); nanoimprint (press a master stamp into resist: nm resolution at parallel throughput, but you need EBL to make the master and stamp defects replicate forever).

> [!question]- Why does EBL resolution barely improve between 30 and 100 keV even though the beam gets sharper?
> The spot was never the bottleneck — resist and scattering are. Higher kV stiffens the beam (less forward scatter, good) but pushes backscatter *further out* rather than eliminating it (the dose background gets flatter and easier to correct, not smaller in total). Meanwhile the resist itself imposes a floor: secondary electrons generated during exposure blur chemistry over ~5–10 nm regardless of beam size, and resist polymer granularity adds roughness. That ~10 nm practical floor is set by the exposure physics, not the optics.

# Connections

- [[Etching]] — one of the two ways the stencil becomes a device; dictates resist thickness via selectivity
- [[Thin-Film Deposition]] — the other way (lift-off), enabled by undercut + line-of-sight evaporation
- [[Electron Microscopy (SEM and TEM)]] — an EBL tool is an SEM with a pattern generator; same beam, same scattering physics
- [[Quantum Dots]] — gate geometries drawn by EBL
- [[Superconducting Qubits]] — Dolan-bridge double-angle evaporation makes the junctions

---
Source: Campbell, *Fabrication Engineering at the Micro- and Nanoscale*, Ch. 7–9; Franssila, *Introduction to Microfabrication*, Ch. 8–10
