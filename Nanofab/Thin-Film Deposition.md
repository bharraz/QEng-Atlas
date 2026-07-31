#nanofab

**Physical methods (PVD) transport atoms through vacuum; chemical methods (CVD family) react precursor gases at the surface. Nearly every property of a deposited film — coverage, adhesion, density, damage — follows from two variables: the arrival angle distribution and the arrival energy of the species landing on the substrate.**

# Reference

## Evaporation

Source heated in HV; flux from the Hertz–Knudsen relation and mean free path:

$$\Phi = \frac{P_{\text{vap}}(T)}{\sqrt{2\pi m k_B T}}, \qquad \lambda_{\text{mfp}} = \frac{k_B T}{\sqrt{2}\pi d^2 P} \sim 1\ \mathrm{m\ at\ }10^{-6}\ \mathrm{mbar}.$$

$\Phi$ = atoms leaving the melt per area per second, set entirely by the source's vapor pressure $P_{\text{vap}}(T)$ and atomic mass $m$ — exponential in $T$, which is why rate control means temperature control. $\lambda_{\text{mfp}}$ = mean free path of those atoms in the chamber's residual gas ($d$ = molecular diameter, $P$ = chamber pressure): at $10^{-6}$ mbar it exceeds the source–substrate distance, so atoms fly straight — **line-of-sight arrival** (narrow angle spread), with only the source temperature's ~0.1 eV of kinetic energy. Consequences:

- **Shadowing**: sidewalls uncoated → lift-off works (undercut resist breaks the film); tilting the sample makes shadowing a tool (two-angle Dolan junctions).
- **Adhesion**: 0.1 eV cannot intermix or break surface bonds; unreactive metals (Au, Pt) adhere by van der Waals only → 5 nm Ti/Cr adhesion layer bonds to the oxide below and alloys above.
- **Alloys fractionate**: components leave per their individual $P_{\text{vap}}(T)$, so film stoichiometry drifts; co-evaporate with independent rate control, or sputter.
- Films porous, low-stress; substrate undisturbed. Rate monitored by quartz-crystal microbalance (Sauerbrey: $\Delta f \propto -\Delta m$).

## Sputtering

Ar plasma at ~mTorr. A plasma sits at a positive potential relative to every surface it touches (electrons, being fast, escape first and charge surfaces negative until balance); the resulting voltage drop across the thin boundary layer — the **sheath**, $V_{\text{sheath}} \sim$ 100s of V at the driven target — accelerates Ar⁺ perpendicularly into the target with energy $eV_{\text{sheath}}$, ejecting target atoms by momentum transfer (billiards, no melting). At mTorr $\lambda_{\text{mfp}} \sim$ cm < throw distance → atoms scatter off gas en route → **broad arrival angles**; they leave the target at 1–10 eV (far above thermal) and are accompanied by an energetic tail of reflected neutrals and plasma UV.

- Broad angles: sidewalls and steps coated (conformal-ish) — and resist sidewalls too, so **lift-off tears**; sputtered films are patterned by blanket deposition + etch-back ([[Etching]]).
- eV-scale arrival: ~monolayer embedding and interfacial intermixing → good adhesion, dense films — and the same energy damages structures thinner than the mixing depth (gate oxides charge, organics crosslink, existing 1–2 nm tunnel barriers short).
- **Stoichiometry preserved**: layer-by-layer momentum-transfer removal tracks the target composition after an initial transient; refractory metals (Nb, TiN) need no melting. Reactive sputtering (add N₂/O₂) forms nitrides/oxides in flight.
- **Stress tunable via pressure**: low $P$ → energetic peening → compressive; high $P$ → thermalized arrival → porous, tensile (Thornton zone diagram).

## CVD / PECVD

Precursors react at the surface; rate is Arrhenius, $r \propto e^{-E_a/k_BT}$. The controlling regime decides film quality:

- **Reaction-limited** (lower $T$): surface kinetics is the bottleneck → every site grows at the same rate regardless of orientation → **conformal**, uniform across the wafer.
- **Transport-limited** (higher $T$): gas diffusion is the bottleneck → faster, but thickness follows local gas supply (loading, position) and conformality degrades.

Thermal CVD needs 600–900 °C. **PECVD** cracks precursors in a plasma → surface chemistry at ~300 °C, paying with hydrogen incorporation (looser, faster-etching films) and mild ion/UV damage.

## ALD

Two self-limiting half-reactions pulsed alternately with purges (TMA/H₂O → Al₂O₃): each pulse saturates the available surface groups and stops, so growth per cycle is fixed (~1 Å) independent of flux. Thickness $= N_{\text{cycles}} \times \mathrm{GPC}$; conformal into arbitrary aspect ratios (excess exposure cannot overdeposit); dense, pinhole-free at 100–300 °C. Cost: nm/min rates and a limited precursor library.

| | arrival angles | arrival energy | conformality | pattern by |
|---|---|---|---|---|
| evaporation | narrow | ~0.1 eV | poor (shadowing) | lift-off |
| sputtering | broad | 1–10 eV + tail | moderate | etch-back |
| CVD/PECVD | n/a (reaction-limited) | thermal | good | etch-back |
| ALD | n/a (saturating) | thermal | perfect | etch-back |

> [!question]- The same arrival energy explains both sputtered films' adhesion and their ability to destroy a tunnel junction — how?
> A few-eV atom embeds and intermixes over ~1 monolayer. At a fresh film/substrate interface that intermixing is the adhesion; at a pre-existing 1.5 nm AlOₓ barrier the same monolayer is a large fraction of the barrier thickness — and tunneling resistance is exponential in thickness, so pinholes and shorts follow. Energy helps or harms according to whether the stirred length is smaller or larger than the structure in question.

# Connections

- [[Vacuum Engineering]] — mean free path vs pressure sets line-of-sight vs diffuse arrival
- [[Lithography]] — lift-off vs etch-back, decided by the arrival-angle column
- [[Etching]] — the subtractive partner
- [[Superconductivity]] — sputtered Nb/TiN; junction barriers as the damage-sensitive case
- [[Surface and Film Metrology]] — post-deposition qualification

---
Source: Ohring, *Materials Science of Thin Films*, Ch. 3–6; Campbell, *Fabrication Engineering at the Micro- and Nanoscale*, Ch. 12–14; George, *Chem. Rev.* 110, 111 (2010)
