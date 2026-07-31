#nanofab

**Packaging is everything between finished chip and working experiment: dicing, die attach, and signal I/O. Every interconnect is simultaneously a transmission-line discontinuity, a thermal joint, and a mechanical stress point — devices that measured perfectly at the probe station die of exactly these.**

# Reference

## Dicing and die attach

Dicing: diamond saw (fast; edge chipping — keep devices ≳100 µm from streets, protect with resist), laser scribe, or cleave along crystal planes ({110} of a (100) Si wafer cleave at right angles — scribe and snap for lab work).

Die attach chooses along four axes: thermal contact (solder ≫ Ag epoxy ≫ clamp), electrical contact (metallized backside + solder), removability (GE varnish), and **CTE mismatch** — the packaging failure mode:

$$\epsilon = \Delta\alpha\,\Delta T \quad (\text{Si on brass: } (19 - 2.6)\ \mathrm{ppm/K} \times 300\ \mathrm{K} \approx 0.5\%\ \text{strain}),$$

where $\Delta\alpha$ is the difference in thermal expansion coefficients and $\Delta T$ the temperature swing: the two materials want different lengths, and a rigid joint forces the difference into strain. 0.5% is far beyond silicon's fracture strain when concentrated at a corner — dies crack, epoxy shears on cycling. Match CTEs, use a compliant (thin, soft) joint that absorbs the difference, or shrink the bonded area.

## Wire bonding

25 µm Au or Al welded by ultrasonics + pressure: ball bonding (Au, ~150 °C) or wedge (Al/Au, room temperature, directional). The electrical fact:

$$L \approx 1\ \mathrm{nH/mm} \;\Rightarrow\; \omega L \approx 30\ \Omega\ \mathrm{at\ 5\ GHz\ per\ mm}$$

— bond wires are the dominant microwave parasitic. Mitigate: short wires, parallel wires (inductances halve), ribbon; in superconducting packages, bonds stitched across ground planes every ≲λ/8 suppress slotline and chip modes. Bonds weld only to clean noble metal: pads must end in Au/Al, and a non-bonding pad means surface contamination (plasma ash — [[Surface Preparation and Cleaning]]). QC: pull test, ~5–10 g for 25 µm Au.

## Flip-chip

Solder or indium bumps, chip flipped onto a carrier: ~10 µm vertical interconnects (negligible $L$), area rather than perimeter I/O, µm alignment. The geometry of multi-chip qubit stacks (qubit die on a wiring die, superconducting In bumps). Cost: planarity/alignment tooling; device face hidden.

## Microwave packaging

The package is a cavity: lowest mode $f \approx c/(2L\sqrt{\epsilon_r})$, with $L$ the largest interior dimension and $\epsilon_r$ the effective dielectric constant filling it — a half-wavelength must fit in the box. A 20 mm air box: ~7.5 GHz, squarely in the qubit band; the mode steals signal, couples channels, and adds loss. Shrink the cavity (push $f$ up), break its symmetry, or load it with absorber where the mode has field and the signal does not. Launches (connector → PCB → chip) are impedance steps to be tapered ([[Impedance Matching]]); characterize the assembled package, not the bare chip ([[S-Parameters]]). Ground must be simply connected — split ground planes without stitching form slot antennas ([[Grounding and Shielding Practice]]). Hermeticity: epoxy lids breathe; welded/glass-frit packages hold vacuum or dry N₂; at mK, light-tightness doubles as IR shielding ([[Cryogenics]] — stray IR breaks Cooper pairs).

> [!question]- A resonator measured Q = 10⁶ on the probe station reads 10⁴ packaged. The film did not change — what did?
> The electromagnetic environment. In order of likelihood: a package or slotline mode overlapping the resonance (fix: bond fences, smaller cavity, absorber); radiation loss into a roomy box; lossy die-attach adhesive wicked into the field region; trapped flux from a magnetized part cooled nearby. Film Q is only an upper bound — the empty package deserves the same characterization as the device.

# Connections

- [[Transmission Lines]] / [[Impedance Matching]] — every launch and bond as a discontinuity
- [[S-Parameters]] — package characterization language
- [[Grounding and Shielding Practice]] — ground topology in 3D
- [[Cryogenics]] — CTE, thermal joints, IR-tightness at mK
- [[Superconducting Qubits]] — flip-chip stacks, bond fences
- [[Surface Preparation and Cleaning]] — bondability as surface cleanliness

---
Source: Harman, *Wire Bonding in Microelectronics*; Tummala, *Fundamentals of Microsystems Packaging*; Huang et al., *IEEE Trans. Quantum Eng.* 2, 1 (2021)
