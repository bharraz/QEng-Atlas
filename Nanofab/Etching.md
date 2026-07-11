#nanofab

**Etching removes material where the resist doesn't protect it. Everything is a trade between selectivity (etch the film, not the mask or the layer below) and anisotropy (etch down, not sideways) — and the trade is physical: chemistry is selective but has no sense of direction, while ion bombardment has direction but attacks everything.**

# Reference

The two figures of merit:

$$S = \frac{r_{\text{film}}}{r_{\text{mask}}} \;\;(\text{selectivity}), \qquad A = 1 - \frac{r_{\text{lateral}}}{r_{\text{vertical}}} \;\;(\text{anisotropy}).$$

Chemistry discriminates between materials because reactions depend on bonds — that's where selectivity comes from. But a liquid or a thermal radical reacts wherever it touches, at the same rate on every exposed face — chemistry alone is isotropic. Directionality has to be *imposed*, and the only practical way to impose it is with ions accelerated along one axis. Ion momentum, though, doesn't care what it hits. Every etch process is some blend of the two, and the knobs move you along that line.

## Wet etching

Immerse in a bath: HF for SiO₂, KOH for Si, piranha for organics. Pure chemistry:

- **Selectivity is superb** — HF etches SiO₂ over Si at >100:1 because it attacks Si–O bonds and does essentially nothing to Si–Si. Choose the chemistry, get the discrimination for free. Also batch-parallel, damage-free, cheap.
- **Isotropy is the failure mode** — the etch proceeds equally in all directions from every exposed point, so it undercuts the mask laterally by about the etch depth. For a 1 µm-deep etch, your linewidth just changed by 2 µm; below a few µm feature size, wet patterning is hopeless. (Where the *crystal* supplies the direction, wet etching turns anisotropic: KOH removes Si {100} planes ~100× faster than the densely packed {111}, carving geometrically perfect 54.7° pits — used in MEMS where you want the crystal's geometry, not the mask's.)

## Dry (plasma) etching — RIE

Reactive-ion etching gets the good half of both. A plasma over the wafer creates **radicals** (F from SF₆/CF₄, Cl from Cl₂ — the chemistry) and **ions**; the wafer sits on the driven electrode, which self-biases negative, so ions fall out of the plasma *vertically* with 10s–100s of eV (the direction). The key is that neither alone etches well — the synergy does: on surfaces being ion-bombarded, the impacts break bonds, clear passivating byproducts, and let the radical chemistry proceed fast; surfaces *not* bombarded (sidewalls) only see slow spontaneous chemistry. Adding a polymer-forming gas (CHF₃, C₄F₈) makes this sharp: a fluorocarbon film continuously deposits everywhere, ions clear it from horizontal surfaces, and it survives on the sidewalls as a protective liner. Vertical walls emerge because the sidewalls are actively defended, not merely neglected.

The selectivity–anisotropy trade is now a knob: **bias power sets ion energy**. More energy → more physical sputtering component → straighter walls and faster etch, but sputtering barely distinguishes materials, so the mask erodes too (selectivity falls) and energetic ions bury themselves in whatever is below (lattice damage, trapped charge in oxides). Less bias, more chemistry → selective and gentle, but the sidewalls start to breathe. ICP tools split the knobs — one RF source sets plasma density (radical/ion *flux*), a separate bias sets ion *energy* — so you can run high-rate *and* low-damage.

Practical realities that follow from the mechanism: rate depends on how much open area is consuming radicals (**loading**); the byproducts must be volatile or they redeposit (that's why each material has its gas: fluorine for Si (SiF₄ is volatile), chlorine for Al (AlF₃ is not)); endpoint is detected by watching the plasma emission change color as the film clears.

**Bosch process (DRIE):** alternate the two roles in time instead of space — a C₄F₈ passivation pulse coats everything, then an SF₆ etch pulse in which ions clear the floor and the chemistry digs. Repeat hundreds of times: aspect ratios >20:1, hundreds of µm deep, with the signature scalloped sidewalls (each cycle bites one scallop). Through-wafer vias, MEMS, ion-trap chips.

**Ion milling** is the all-physics endpoint: pure Ar⁺ sputtering, no chemistry at all. It etches *anything* — the fallback for materials with no volatile halide (complex oxides, magnetic stacks, some superconductors) — precisely because it discriminates *nothing*: selectivity ≈ 1, the mask erodes as fast as the film, and sputtered material redeposits on sidewalls (fences). You use it when chemistry has nothing to offer.

**Mask accounting** (why resist thickness is chosen by the etch, not the litho): films are non-uniform so you always over-etch 10–50%; the mask must survive $t_{\text{etch}}(1 + \text{OE})/S$. When no polymer resist survives — long etches, hot etches, low-selectivity chemistries — you first pattern a thin **hard mask** (SiO₂, SiN, or metal) whose selectivity against the target etch is 10–100×, and spend the resist on patterning *that*.

> [!question]- Your RIE gives beautiful vertical walls but the resist dies before the film clears. What is the process telling you, and which way do you move?
> Vertical walls + dying mask = the ion (physical) component is doing the work, and sputtering doesn't distinguish resist from film. Either shift work back to chemistry — lower bias power, raise radical flux or pressure, accept slightly softer sidewalls — or keep the physics and give it a mask it can't kill (hard mask). The diagnosis works because anisotropy and mask erosion have the same cause; you can't fix one by turning up the thing that produces both.

# Connections

- [[Lithography]] — supplies the mask; the etch budget often dictates the resist stack
- [[Thin-Film Deposition]] — etch-back vs lift-off; sidewall passivation is deposition inside the etcher
- [[Vacuum Engineering]] — plasma tools are vacuum systems with RF attached
- [[Surface and Film Metrology]] — verifying depth and sidewall profile afterward

---
Source: Campbell, *Fabrication Engineering at the Micro- and Nanoscale*, Ch. 11; Franssila, *Introduction to Microfabrication*, Ch. 11–12
