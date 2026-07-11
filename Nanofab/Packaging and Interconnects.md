#nanofab

**Packaging is everything between the finished chip and the working experiment: singulating the wafer, attaching the die, and getting signals on and off it. It is where fab meets the lab bench — and where a device that measured perfectly at the probe station dies of a bad wirebond, a lossy interface, or thermal mismatch.** The organizing physics: every interconnect is a transmission-line discontinuity, a thermal joint, and a mechanical stress point *simultaneously*.

# Reference

**Dicing.** Wafer → dies by diamond-blade saw (fast; chipping at edges — keep devices ≳100 µm from streets), laser scribing (cleaner edges, heat-affected zone), or cleave-along-crystal-planes for quick lab work on Si/GaAs (the {110} planes of a (100) wafer cleave at right angles — scribe and snap). Protect surfaces with resist before dicing; the saw is a slurry of water and debris.

**Die attach.** Glue (silver epoxy: conductive, cures 100–150 °C; GE varnish for cryo removability), solder (real thermal/electrical contact, needs metallized backside), or clamp (stress-free, thermal contact only as good as the [[Cryogenics|asperity story]]). The consideration hierarchy: does the joint need to conduct heat (power dissipation → solder), conduct electricity (grounded backside?), survive thermal cycling (**CTE mismatch is the packaging failure mode**: Si at 2.6 ppm/K on brass at 19 ppm/K accumulates ~0.5% strain over a 300 K cool-down — dies crack, epoxy shears; match materials or use compliant joints), and come off again (varnish).

**Wire bonding — the default signal path.** A µm-scale wire (25 µm Au or Al) welded by ultrasonic energy + pressure (+ heat for Au): *ball bonding* (Au, fast, needs ~150 °C) or *wedge bonding* (Al or Au, room temperature, directional). Practical physics:

- A 1 mm bond wire is ~1 nH — at 5 GHz that's $\omega L \approx 30\ \Omega$ of series reactance: **bond wires are inductors**, the dominant parasitic of microwave packaging. Mitigations: short wires, several in parallel, ribbon bonds; in superconducting-qubit packages, wirebonds stitched across ground planes every ~λ/8 to suppress slotline/chip modes ("bond-wire fences").
- Bonds stick only to clean noble metal: pads need Au (or Al) surfaces — the fab flow must end with a bondable metal, and an oxidized or contaminated pad is why "the bonder won't take" (plasma-ash the surface).
- Pull strength is the QC metric; a properly welded 25 µm Au wire holds ~5–10 g. Heel cracks from over-worked wedge bonds fail on thermal cycling.

**Flip-chip** — the scaling alternative: bump the chip face with solder or indium, flip it onto a matching carrier, bond under force/heat. Short (~10 µm) vertical interconnects → tiny inductance, area (not perimeter) I/O density, and the geometry behind current multi-chip qubit stacks (qubit chip flipped onto a wiring/readout chip — indium bumps, superconducting, ~µm alignment). Cost: planarity and alignment infrastructure, and you can no longer see the device face.

**Microwave packaging** (the RF discipline transplanted): the package is a cavity — its resonances must sit far from operating bands (smaller boxes, mode-suppressing geometry, lossy absorber where fields shouldn't be); launch transitions (SMA/GPO connector → PCB → chip) are impedance discontinuities to be tapered ([[Impedance Matching]], [[S-Parameters]] of the *assembled* package, not just the chip); ground is a topology question — a single continuous ground with stitched vias, or you've built a slot antenna ([[Grounding and Shielding Practice]]).

**Hermeticity and environment:** epoxy-lidded packages breathe; glass-frit/welded metal packages hold vacuum or dry N₂ (relevant for MEMS, bare NV/photonics dies, anything humidity-sensitive). For cryo packages, light-tightness doubles as IR shielding (see [[Cryogenics]] — stray IR breaks Cooper pairs).

> [!question]- A superconducting resonator measured Q = 10⁶ on a probe wafer but 10⁴ packaged. The film didn't change — what did?
> The electromagnetic environment did. Prime suspects, in order: a package/chip-box mode or slotline mode between chip ground planes now overlapping the resonance (fix: bond-wire fences across grounds, smaller cavity, absorber); radiation loss through a too-open geometry (probe stations are lossy but *close*; a roomy box is a good antenna cavity); lossy die-attach adhesive wicking under the chip into the field region; and magnetic flux trapped during cooldown from a magnetized part (screws!) near the chip. The film's intrinsic Q is only an upper bound — packaging sets what you measure, which is why serious groups characterize the empty package as carefully as the device.

# Connections

- [[Transmission Lines]] / [[Impedance Matching]] — every launch and bond is a discontinuity
- [[S-Parameters]] — the language of package characterization
- [[Grounding and Shielding Practice]] — ground topology, now in 3D
- [[Cryogenics]] — CTE mismatch, thermal joints, and light-tightness at mK
- [[Thin-Film Deposition]] — bondable pad metallization as the last fab step
- [[Superconducting Qubits]] — flip-chip stacks and bond-fence practice

---
Source: Harman, *Wire Bonding in Microelectronics*; Tummala, *Fundamentals of Microsystems Packaging*; Huang et al., *IEEE Trans. Quantum Eng.* 2, 1 (2021) (qubit packaging)
