#nanofab #reference

**Map of the Nanofab folder — every process is either adding material, removing it, patterning where that happens, or measuring what you got.**

# Reference

## The four verbs

| Verb | Pages | The controlling variable |
|---|---|---|
| **Pattern** | [[Lithography]] | resist contrast and the exposure's point-spread — what sets the smallest reliable feature |
| **Add** | [[Thin-Film Deposition]] | arrival *angle* and arrival *energy* of the species landing on the substrate |
| **Remove** | [[Etching]] | chemistry discriminates between materials but has no direction; ions have direction but no discrimination |
| **Measure** | [[Surface and Film Metrology]], [[Electron Microscopy (SEM and TEM)]] | what the probe couples to, and what it therefore cannot see |

Supporting the four: [[Surface Preparation and Cleaning]] (every interface was once an exposed surface), [[Vacuum Engineering]] (which sets the mean free path that decides arrival angles), [[Cryogenics]] (the heat budget the finished device lives in), and [[Packaging and Interconnects]] (every interconnect is also a transmission-line discontinuity).

## The decision that couples them: lift-off vs. etch-back

This is the choice most process flows turn on, and it is decided by the deposition's arrival-angle column:

| | Lift-off | Etch-back |
|---|---|---|
| Deposition | line-of-sight (evaporation) | conformal (sputter, CVD, ALD) |
| Why | sidewalls stay uncoated, so the film tears cleanly at the resist edge | conformal coating covers resist sidewalls, so lift-off tears badly |
| Patterning | undercut resist profile, deposit, dissolve | blanket deposit, then pattern and etch |
| Costs | limited thickness, edge quality | etch selectivity and damage to layers below |

Read left to right: **choosing evaporation is choosing lift-off**, and choosing sputtering commits you to etching. That coupling is the single most useful thing to hold about the folder.

## Cross-cutting constraints

- **Vacuum sets the deposition regime.** At $10^{-6}$ mbar the mean free path exceeds the chamber, so atoms fly straight; at mTorr they scatter and arrive from all angles. One pressure knob decides conformality ([[Vacuum Engineering]]).
- **Energy helps or harms depending on what it hits.** Few-eV arrival intermixes a monolayer: adhesion at a fresh interface, destruction of a 1.5 nm tunnel barrier ([[Thin-Film Deposition]], [[Josephson Junction]]).
- **Every interface is a contamination record and a loss channel.** Surfaces carry adsorbates and native oxide, which become the amorphous layers hosting two-level fluctuators ([[Surface Preparation and Cleaning]], [[TLS and Dielectric Loss]]).
- **Thermal budget is cumulative.** Each anneal affects every layer already present, so process order is a constraint, not a preference.
- **Metrology only sees what its probe couples to.** Ellipsometry infers thickness from a model; AFM measures topography, not composition; SEM's interaction volume is larger than the beam spot ([[Surface and Film Metrology]]).

## Where the devices land

| Device | Fab-critical step |
|---|---|
| Josephson junctions | double-angle shadow evaporation; barrier thickness enters $I_c$ exponentially ([[Josephson Junction]]) |
| Superconducting resonators and qubits | surface and interface quality — the participation-ratio fight ([[TLS and Dielectric Loss]]) |
| Surface-electrode ion traps | electrode surface treatment against anomalous heating; RF breakdown; dielectric loss |
| Colour centres | ion implantation plus anneal, then photon extraction structures ([[Color Centers]]) |
| Gate-defined dots | e-beam lithography at the resolution limit; gate oxide integrity ([[Quantum Dots]]) |

> [!question]- Your metal film adheres poorly and lifts off during the next process step. Which knob, and why?
> Arrival energy. Evaporated atoms land with ~0.1 eV, too little to intermix or break surface bonds, so an unreactive metal adheres only by van der Waals. Either add a thin Ti or Cr adhesion layer that bonds to the oxide below, or sputter instead — few-eV arrival embeds a monolayer and makes the interface. The same energy would destroy a thin tunnel barrier, so the fix is not universally safe.

# Connections

- [[(Guide) Debugging Method]] — the procedural stance for when a process stops working
- [[Josephson Junction]] / [[TLS and Dielectric Loss]] — what the fab quality actually buys or costs
- [[Color Centers]] — implantation and anneal as a creation process
- [[Bandwidth]] / [[Time Constants and Reactance Rules of Thumb]] — the packaging side, once the chip is wired
- [[Conventions and Factor-of-Two Traps]] — units and conventions in process specs

---
Source: Campbell, *Fabrication Engineering at the Micro- and Nanoscale*; Franssila, *Introduction to Microfabrication*
