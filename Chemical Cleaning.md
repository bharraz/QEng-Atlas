#labwork #reference

**A dirty surface carries several kinds of layer at once — oil and organic films from fingers, pumps, and air; salts and ions; loose particles; and the surface's own oxide — and each is removed by a different mechanism: dissolve it in a liquid with similar chemistry, lift it off with a detergent, oxidize it into gas, or dissolve the layer underneath it.** Etching uses the same chemistry aimed at the material itself instead of what sits on it.

# Reference

**Solvents: like dissolves like.** A substance dissolves in a liquid whose molecules attract it about as strongly as it attracts itself: nonpolar oils and greases dissolve in nonpolar or moderately polar solvents, salts and ionic residues in water, and alcohols sit in between, mixing with both water and many organics.

**Picture:** a surface as a stack, with particles and oils on top, salts in between, and the oxide at the bottom, removed from the top down, each layer by the mechanism that matches its chemistry.

| Solvent | Dissolves | Drawbacks |
|---|---|---|
| acetone | oils, greases, photoresists, most adhesives, many plastics | evaporates so fast it redeposits what it dissolved; attacks plastics, many epoxies, and cemented optics; highly flammable; penetrates nitrile gloves within minutes |
| isopropanol (IPA) | acetone and what it carries, light oils; mixes with water | slower to dry; drugstore "rubbing alcohol" is often 70% IPA in water, sometimes with additives, and leaves residue |
| methanol | like IPA, drying faster and cleaner — common for optics | toxic through skin and vapor |
| ethanol | like IPA | denatured grades contain additives that leave residue |
| deionized (DI) water | salts, ionic residues, rinsing acids and bases | leaves water spots of dissolved solids if it dries in place |
| hexane, heptane | nonpolar oils, vacuum grease | flammable |

Whatever is dissolved in a solvent stays on the surface when the solvent evaporates, so purity grade matters (spectroscopic or electronic grade for optics), and a cleaning step should end by removing the liquid — blown off with dry nitrogen, or chased by a cleaner solvent — rather than letting it dry in place.

**Why acetone, then IPA, then dry.** Acetone removes the organics but dries within seconds, leaving the dissolved contaminant behind as a film. Rinsing with IPA before the acetone dries dilutes and carries away that contaminated acetone. IPA evaporates more slowly and leaves less, and blowing it off with nitrogen removes the liquid before it can evaporate in place.

**Detergents and ultrasound.** A surfactant molecule has a water-attracting head and an oil-attracting tail; surfactants surround oil droplets (micelles), so water can carry the oil away. This is how machined parts are degreased of cutting oil before vacuum use. The detergent itself must be rinsed off completely, or its film outgasses. An ultrasonic bath adds mechanical scrubbing: sound in the liquid creates bubbles that collapse violently against surfaces and into crevices (cavitation). The same collapse damages optical coatings, crystals, glued joints, and wire bonds.

**Oxidizers: burning organics without a flame.**

- **Piranha** (sulfuric acid with hydrogen peroxide) forms a powerful oxidizer that converts organic residue to CO₂ and water and leaves glass and silicon hydrophilic. Mixing releases enough heat to exceed 100 °C.
- **Oxygen plasma and UV–ozone** create reactive oxygen that oxidizes the last molecular layers of organics into volatile CO, CO₂, and H₂O. They are dry and gentle on most inorganic surfaces — the usual final step before bonding or deposition — but do nothing to particles and metals, and they oxidize copper and silver.

**Acids and bases: dissolving the layer underneath.**

| Chemical | Dissolves | Mechanism | Typical use |
|---|---|---|---|
| hydrochloric acid (HCl) | metal oxides and reactive metals (not Cu, Ag, Au, Pt) | non-oxidizing acid: protons attack the oxide, chloride holds the metal ions in solution | removing metal contamination (RCA SC-2), rust |
| nitric acid (HNO₃) | most metals including Cu and Ag; not Au or Pt; passivates Al and stainless steel instead | oxidizing acid | dissolving metal residue; passivating stainless steel |
| aqua regia (3 HCl : 1 HNO₃) | gold, platinum | nitric acid oxidizes the metal, chloride binds the ions and drives the reaction forward | removing gold; made fresh, releases toxic gases |
| hydrofluoric acid (HF), dilute or buffered (BOE) | SiO₂ and glass | fluoride forms soluble SiF₆²⁻ | stripping native oxide from Si (leaving it H-terminated), etching glass |
| citric acid | free iron and iron oxides on stainless steel | chelation: the molecule binds metal ions | passivating stainless, gentler than nitric |
| KOH, NaOH | silicon (along crystal planes), aluminium, glass slowly; oils | bases break Si–Si and Si–O bonds; turn fats into soap (saponification) | anisotropic Si etching, degreasing |
| ammonia–peroxide (RCA SC-1) | organics and particles | oxidizes and slightly etches the surface so particles lift off and are repelled | wafer cleaning ([[Surface Preparation and Cleaning]]) |

**Cleaning versus etching is a question of selectivity** — the rate on what you want removed divided by the rate on what you want kept. HF removes an oxide film from silicon without touching the silicon, but dissolves a glass substrate outright; KOH degreases a steel part harmlessly but etches silicon and aluminium. Etch rates, anisotropy, and masks are on [[Etching]].

**Order matters.** Each step must reach the surface and must leave nothing the next step cannot remove:

1. Remove oils first — an acid cannot reach a surface through an oil film.
2. Remove particles while the surface is still wet — drying fixes them in place.
3. Do the oxidizing or etching steps.
4. End with a rinse that leaves nothing behind, then blow dry.

For vacuum parts a typical sequence is detergent, water, acetone, IPA, dry; for resist residue, acetone, IPA, then plasma.

**What a cleanliness check tells you:**

| Check | What it tells you |
|---|---|
| water on glass or oxide: sheets out or beads up | clean glass and oxide are hydrophilic, so water spreads; beading means an organic film (on HF-dipped silicon beading is expected — the surface is H-terminated) |
| grazing light (dark-field) on an optic | particles, and streaks left by evaporated solvent |
| breath on an optic | the condensation pattern shows residue films |
| residual gas analyzer after a bake | hydrocarbon peaks at masses 41, 43, 55, 57 indicate oil contamination ([[Vacuum Engineering]]) |

**Safety notes, by mechanism:**

- Solvent vapours are heavier than air and ignite from hot plates and sparks: use small amounts, no open heat.
- Nitrile gloves resist acids and alcohols for a while, but acetone penetrates them within minutes; butyl rubber resists acetone.
- Add acid to water, never water to concentrated acid: the heat of dilution boils the added water and spatters acid.
- Piranha reacts explosively with organic solvents and evolves gas, so it is never mixed with solvent waste and never stored in a closed container.
- HF penetrates skin with little immediate pain and binds the calcium in tissue, causing delayed deep injury and systemic toxicity. It requires specific training, calcium gluconate gel at hand, and plastic (PTFE or polypropylene) containers, never glass.
- Never mix oxidizing-acid waste with solvent waste.
- All acid work, and all work with volatile solvents, belongs in a fume hood.

> [!question]- Why rinse with IPA after acetone, rather than letting the acetone evaporate?
> Evaporation leaves behind everything the liquid had dissolved, and acetone evaporates fast enough to strand its dissolved contaminant as a film — while its evaporative cooling can also condense moisture onto the part. IPA, applied while the acetone is still wet, dissolves both the acetone and what it carried, and it is then blown off as a liquid rather than left to dry, taking the contamination with it.

# Connections

- [[Surface Preparation and Cleaning]] — wafer-level cleaning sequences (RCA, HF-last) and why interfaces matter for devices
- [[Etching]] — the same chemistry used to remove material on purpose
- [[Handling Lab Hardware]] — keeping parts clean so they need cleaning less often
- [[Vacuum Engineering]] — why hydrocarbons and water set the base pressure
- [[Lithography]] — stripping resist
- [[Thin-Film Deposition]] — adhesion starts at the cleaned surface

---
Source: W. Kern, *J. Electrochem. Soc.* 137, 1887 (1990); J. H. Moore, C. C. Davis & M. A. Coplan, *Building Scientific Apparatus*, 4th ed. (Cambridge, 2009); National Research Council, *Prudent Practices in the Laboratory* (2011)
