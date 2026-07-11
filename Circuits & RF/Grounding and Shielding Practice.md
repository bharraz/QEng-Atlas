#circuits #electronics

**"Ground" is not 0 V everywhere — it's a network of impedances carrying return currents, and every millivolt of difference between two "grounds" sits in series with somebody's signal.** Grounding is deciding where currents flow; shielding is keeping fields out; both fail the same way: shared paths.

# Reference

**The core fact:** 1 m of hookup wire ≈ 1 µH ≈ 6 Ω at 1 MHz (mΩ at DC — fine at DC, terrible at RF). Ground wires are impedances and $V = IZ$ applies to them (**common-impedance coupling**).

**Topology by frequency:**

| Regime | Strategy | Why |
|---|---|---|
| ≲ 100 kHz | **star (single-point)** | you control where mains-frequency and load currents flow |
| ≳ 1 MHz | **ground plane, many points** | wire inductance makes stars useless; the plane is the lowest-Z return under every trace |
| mixed-signal | one plane, but *route* the returns; split planes usually cause more problems than they solve | return current flows under its own trace anyway |

**Shield connection rules:**
- **Low frequency (hum band):** shield grounded at **one end only** — both ends invites ground-loop current *through the shield*, which couples into the center conductor.
- **RF (≳ 1 MHz):** ground **both ends, 360° termination** — skin effect keeps shield current on the outside; a floated end re-radiates. Hybrid: hard ground one end, small capacitor at the other covers both regimes.
- **Pigtails ruin shields:** a few cm of pigtail ≈ tens of nH; at RF the shield current detours through it and injects straight into the signal. Use connectors that clamp the shield circumferentially.

**Chassis vs signal ground:** tie them together **once**, at the cable-entry panel, so cable noise currents flow around the chassis skin instead of through the board.

> [!question]- A rack-to-rack shielded cable hums at 60 Hz when the shield is grounded at both ends, but a 100 MHz pickup problem gets worse when you lift one end. Reconcile.
> Two regimes: at 60 Hz, both-ends grounding lets loop current flow in the shield and couple in — lift one end. At 100 MHz the shield needs both ends bonded so induced current stays on its outer surface — a lifted end is an antenna. Fix: ground one end, RF-cap the other.

# Connections

- [[Ground Loops]] — the failure mode this doctrine exists to prevent
- [[Electromagnetic Shielding]] — the field-physics side: skin depth, apertures, µ-metal for low-f B
- [[Common-Mode and Differential-Mode Signals]] — ground differences arrive common-mode; balanced inputs forgive imperfect grounding
- [[Noise Coupling Mechanisms]] — the diagnosis table for which coupling you actually have
- [[Skin Depth]] — why RF shield current stays outside and both-end grounding works

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Chs. 3 & 6
