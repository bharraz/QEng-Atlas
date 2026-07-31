#nanofab

**Etching removes material where the mask does not protect. Chemistry discriminates between materials but has no direction; ion bombardment has direction but no discrimination — every process is a point on that trade, and the two figures of merit quantify it.**

# Reference

$$S = \frac{r_{\text{film}}}{r_{\text{mask}}}\ (\text{selectivity}), \qquad A = 1 - \frac{r_{\text{lateral}}}{r_{\text{vertical}}}\ (\text{anisotropy}),$$

$r_{\text{film}}, r_{\text{mask}}$ = etch rates of the target film and of the masking material (nm/min); $r_{\text{vertical}}, r_{\text{lateral}}$ = rates downward and sideways into the sidewall (nm/min). $S$ (dimensionless) counts nm of film removed per nm of mask consumed — also quoted film-vs-underlayer when the point is to stop on the layer below. $A$ (dimensionless) runs 0 (isotropic: sideways as fast as down, undercutting the mask by the etch depth) to 1 (no lateral component, vertical walls).

## Wet etching

Bath chemistry: HF for SiO₂ (attacks Si–O, ignores Si–Si: $S > 100{:}1$), KOH for Si, piranha for organics. Rates Arrhenius in bath temperature.

- Selectivity excellent, batch-parallel, damage-free.
- **Isotropic**: undercut ≈ etch depth, so linewidth changes by $2\times$ depth — unusable below a few µm.
- Exception: crystallographic etches. KOH removes Si {100} ~100× faster than {111} → 54.7° pyramidal pits bounded by {111}; the *crystal* supplies the anisotropy (MEMS, alignment marks).

## Reactive-ion etching (RIE)

The plasma supplies two agents. **Radicals** — neutral reactive fragments (F from SF₆/CF₄ for Si; Cl from Cl₂ for Al) — carry the chemistry. **Ions** carry the direction: the plasma floats positive relative to the wafer, and the voltage drop across the boundary sheath accelerates ions perpendicular to the surface with $E_{\text{ion}} \approx e(V_{\text{plasma}} - V_{\text{bias}}) \sim$ 10s–100s eV. Neither agent alone etches well; the synergy does — ion impact breaks bonds and clears reaction products, letting the radical chemistry run fast, but only on surfaces the ions strike (floors, not walls). Polymer-forming gases (CHF₃, C₄F₈) sharpen this: a fluorocarbon liner deposits everywhere, ions clear it from floors, and it survives on sidewalls — vertical walls by active sidewall protection, not mere neglect.

- **Bias power = the S–A knob**: more ion energy → straighter walls, faster etch, but sputtering does not discriminate → mask erodes ($S$ falls) and substrate damage grows. ICP tools decouple plasma density (radical/ion flux) from bias (ion energy).
- Byproducts must be volatile — the reason each material has its gas (SiF₄ volatile; AlF₃ not → Cl₂ for Al). Rate depends on open area (**loading**); endpoint by optical emission of the disappearing species; deep features etch slower than open ones (ARDE — transport into the trench).
- **Bosch (DRIE)**: alternate C₄F₈ passivation / SF₆ etch cycles → aspect ratios > 20:1 routinely, ~40:1 in production and ~80:1 demonstrated, hundreds of µm deep, scalloped walls (one scallop per cycle, < 100 nm in optimized recipes). Through-wafer vias, ion-trap chips.
- **Ion milling**: pure Ar⁺ sputtering. Etches any material (the fallback when no volatile chemistry exists — complex oxides, magnetics), $S \approx 1$, redeposition fences on sidewalls.

## Mask budget

Films are nonuniform → over-etch 10–50%; the mask must survive

$$t_{\text{mask}} > \frac{d_{\text{film}}\,(1 + \mathrm{OE})}{S}.$$

$t_{\text{mask}}$ = required mask thickness (nm); $d_{\text{film}}$ = film thickness to clear (nm); OE = fractional over-etch (0.1–0.5); $S$ = selectivity from above. Example: 500 nm of Si at 30% over-etch through a mask with $S = 2$ needs > 325 nm of resist.

This — not lithography — usually sets resist thickness. When no polymer survives (long, hot, or low-$S$ etches): pattern a thin **hard mask** (SiO₂, SiN, metal; $S$ = 10–100× against the target etch) with the resist, then spend the hard mask on the film.

| | $S$ | $A$ | scale | damage |
|---|---|---|---|---|
| wet | ≫10 | 0 (or crystal-defined) | > few µm | none |
| RIE | 5–50 | tunable → 1 | ~10 nm | ion/UV, moderate |
| DRIE (Bosch) | >100 (vs resist) | ~1 | µm, deep | scallops |
| ion mill | ~1 | 1 | ~10 nm | high, redeposition |

> [!question]- RIE gives vertical walls but the resist dies before the film clears. Which direction do the knobs move?
> Vertical walls with a dying mask = the physical (ion) component dominates, and sputtering removes resist as readily as film. Either shift work to chemistry — lower bias, raise radical flux/pressure, accept softer sidewalls — or keep the physics and switch to a hard mask. Tuning cannot fix it otherwise: anisotropy and mask erosion here have the same cause.

# Connections

- [[Lithography]] — supplies the mask; the etch budget dictates the resist stack
- [[Thin-Film Deposition]] — etch-back vs lift-off; sidewall passivation is deposition inside the etcher
- [[Vacuum Engineering]] — plasma tools are vacuum systems with RF
- [[Surface and Film Metrology]] — depth and profile verification
- [[Surface Preparation and Cleaning]] — post-etch residue and damage removal

---
Source: Campbell, *Fabrication Engineering at the Micro- and Nanoscale*, Ch. 11; Franssila, *Introduction to Microfabrication*, Ch. 11–12
