#nanofab

**Putting material down: physical methods (PVD) transport atoms through vacuum to the substrate; chemical methods (CVD family) react precursor gases at the surface.** Nearly every practical property of a deposition method — coverage, adhesion, density, what it damages — traces back to two numbers: the **arrival angle distribution** and the **arrival energy** of the atoms landing on your substrate. Read each technique below through those two.

# Reference

## PVD — evaporation

Heat a source (resistive boat, or an e-beam spot for refractory metals) in high vacuum until its vapor pressure is useful. The chamber is at $\sim 10^{-6}$ mbar, where the mean free path

$$\lambda_{\text{mfp}} \approx \frac{k_B T}{\sqrt{2}\,\pi d^2 P} \sim 1 \text{ m}$$

exceeds the source–substrate distance: atoms fly in straight lines from what is effectively a point source. So the arrival angles are **narrow** (line-of-sight) and the arrival energy is just the source temperature — **thermal, ~0.1 eV**.

Consequences, in order:

- **Shadowing.** Any topography blocks the flux; sidewalls and trench bottoms get almost nothing. Bad if you wanted a conformal coat — but exactly what **lift-off** requires: an undercut resist profile means the film on top of the resist and the film on the substrate are *never connected*, so the resist dissolves cleanly away. Tilt the sample and the shadow becomes a tool (angled evaporation through a resist bridge = two junction electrodes from one pump-down, the Dolan technique).
- **Weak adhesion.** A 0.1 eV atom arrives with no ability to embed, intermix, or break surface bonds; it sits where van der Waals forces put it. For metals that also don't chemically bond to oxide surfaces (Au, Ag, Pt — full d-shells, unreactive), the interface is held by almost nothing and the film peels with the tape test. The fix is chemical, not physical: 5 nm of Ti or Cr first — reactive metals that bond to the oxide below and alloy with the noble metal above.
- **Porous, low-stress films.** No energy to rearrange after landing → open microstructure. Gentle on whatever is underneath, but not the densest or most robust film.
- **Alloy fractionation.** Components evaporate according to their individual vapor pressures, not the melt composition; the more volatile species leaves first, so film stoichiometry drifts over the deposition. Evaporating an alloy accurately requires either co-evaporation from two rate-controlled sources or giving up and sputtering.

## PVD — sputtering

Strike an Ar plasma at ~mTorr; the target sits at negative potential, so Ar⁺ ions accelerate across the sheath into it and knock atoms out by momentum transfer (billiards, not evaporation — no melting involved). Two things are now different at the substrate:

- **Arrival angles are broad.** At mTorr the mean free path is ~cm, shorter than the throw distance, so sputtered atoms scatter off gas on the way and arrive from many directions. Steps and sidewalls get coated — better step coverage than evaporation *for the same reason* lift-off now fails: the resist sidewalls get coated too, the film is continuous over the edge, and lift-off tears ragged flags instead of breaking cleanly. Sputtered films are therefore patterned the other way around: blanket-deposit, then etch through a resist mask (**etch-back** — see [[Etching]]).
- **Arrival energies are 1–10 eV, with a high-energy tail.** Sputtered atoms leave the target far above thermal energy, and they are accompanied by reflected neutrals, plasma UV, and stray ions. This energy is the source of *both* the advantages and the damage:
    - *Advantages:* arriving atoms embed a monolayer or so deep and locally intermix at the interface — adhesion is good without adhesion layers; films pack dense. Stress is tunable because pressure sets how much of the energy survives the trip: low pressure → energetic "peening" → compressive films; high pressure → thermalized arrivals → porous, tensile films.
    - *Damage:* the same bombardment that densifies the film wrecks anything whose function lives in a few nm or in fragile bonds. Concretely: a gate oxide accumulates trapped charge from ion/UV flux (shifted thresholds); an organic film or a molecular layer gets bonds broken and crosslinked; an existing 1–2 nm tunnel barrier can be shorted by interfacial intermixing. "Delicate" means: thin oxides, organics, and any structure whose thickness is comparable to the implantation depth of a few-eV-to-100-eV particle.
- **Stoichiometry is preserved.** Momentum transfer removes the target surface roughly layer by layer; after a brief transient (the more-easily-sputtered species depletes from the surface until removal rates balance), the film composition tracks the target. This — plus not needing to melt anything — is why refractory metals (Nb, TiN: the superconducting-circuit materials) and alloys are sputtered. Adding N₂ or O₂ to the plasma reacts with the depositing metal in flight and at the surface: **reactive sputtering**, the standard route to nitrides and oxides.

## CVD / PECVD

No solid source: precursor gases (SiH₄, TEOS, NH₃...) react *at the heated surface* to leave solid film and volatile byproducts. The rate follows Arrhenius, $r \propto e^{-E_a/k_B T}$, and the key regime question is which step is slowest:

- **Reaction-limited** (lower T): the surface reaction is the bottleneck, so every surface site — floor, sidewall, deep trench — grows at the same rate set by local chemistry, not by arrival direction. This is *why CVD is conformal*: there is no "arrival angle" to speak of once the gas fills the feature and the reaction can't keep up with supply. Uniformity across the wafer is also best here.
- **Transport-limited** (higher T): reaction is instant and gas-phase diffusion is the bottleneck — faster growth, but thickness now depends on local gas supply (pattern density, position in the boat), and conformality degrades.

The cost of thermal CVD is temperature: 600–900 °C for good films, incompatible with metals already on the wafer or with resists. **PECVD** uses a plasma to crack the precursors, so the surface chemistry runs at ~300 °C — but the film pays: incomplete reactions leave hydrogen in the network (looser, etchier films) and the plasma adds the same charge/UV damage considerations as sputtering, in milder form.

## ALD — conformality taken to its logical limit

Split the CVD reaction into two half-reactions and pulse them alternately with purges between (canonical: TMA then H₂O for Al₂O₃). Each precursor reacts **only with the surface groups the previous pulse left behind** — once those are consumed, additional precursor does nothing. Self-limiting saturation means growth per cycle is fixed (~1 Å) regardless of flux, so:

- thickness is digital: cycles × growth-per-cycle, no rate calibration drift;
- coverage is perfect into arbitrary aspect ratios — excess exposure can't over-deposit, so even the deepest trench just needs a longer pulse to saturate;
- films are dense and pinhole-free at 100–300 °C.

The price is that saturation takes time (nm/min at best — you use it for the critical 1–20 nm, not for µm) and each material needs a worked-out precursor pair.

**Choosing:** evaporation when you pattern by lift-off; sputtering for superconductors, alloys, and adhesion-critical metal (patterned by etch-back); PECVD for µm-thick dielectric; ALD for the thin dielectric whose quality you actually care about. Rates are monitored in situ by quartz-crystal microbalance (PVD) and verified by [[Surface and Film Metrology|ellipsometry, XRR, or profilometry]].

> [!question]- Why does the same property — arrival energy — explain both why sputtered films stick well and why sputtering can destroy a tunnel junction?
> Adhesion and damage are the same event at different depths. A few-eV atom embeds and intermixes over ~1 monolayer: at a fresh film/substrate interface that intermixing *is* the adhesion; at a pre-existing 1.5 nm AlOₓ tunnel barrier the same monolayer of intermixing is a significant fraction of the barrier — pinholes and shorts. Whether energy helps or harms depends only on whether the length it stirs is smaller or larger than the structure you care about.

# Connections

- [[Vacuum Engineering]] — mean free path vs pressure: the single number behind line-of-sight vs diffuse arrival
- [[Lithography]] — lift-off vs etch-back, decided by the arrival-angle distribution
- [[Etching]] — the subtractive partner; etch-back patterning for sputtered films
- [[Superconductivity]] — sputtered Nb/TiN as circuit materials; junction barriers as the damage-sensitive structure
- [[Surface and Film Metrology]] — qualifying thickness, roughness, and stress after the fact

---
Source: Ohring, *Materials Science of Thin Films*, Ch. 3–6; Campbell, *Fabrication Engineering at the Micro- and Nanoscale*, Ch. 12–14; George, *Chem. Rev.* 110, 111 (2010) (ALD)
