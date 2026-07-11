#EnM

**Within ~λ/2π of a source the fields are quasi-static and cling to it; beyond, they detach and radiate** — and interference couples into your circuit by completely different physics in the two zones, so the fixes differ too.

# Reference

Boundary at $r \sim \lambda/2\pi$ (the "radian sphere"): for 60 Hz that's ~800 km — *all mains pickup is near-field*; for 2.4 GHz it's 2 cm — *almost everything is far-field*.

| | Near field ($r \ll \lambda/2\pi$) | Far field ($r \gg \lambda/2\pi$) |
|---|---|---|
| Character | quasi-static, reactive, energy sloshes back | radiation, energy leaves for good |
| Falloff | $1/r^3$ (dipole terms), $1/r^2$ | $1/r$, E⊥B⊥r̂ |
| Wave impedance E/H | source-dependent: ≫377 Ω (E-type: high dV/dt, high-Z) or ≪377 Ω (M-type: high dI/dt, loops) | 377 Ω always |
| Coupling into circuits | **capacitive** (E) or **inductive** (M) — mutual C or M to the source | true radiated pickup on λ-scale conductors |
| Fix | shield (E-type), shrink loop area / twist (M-type), distance helps *fast* | filter at entry, shield integrity, antenna-length awareness |

The full dipole field contains $1/r^3$ (static), $1/r^2$ (induction), and $1/r$ (radiation) terms — all three cross at exactly $r = \lambda/2\pi$. Retardation is why the far zone exists at all: fields can't update instantaneously, and the un-updated part propagates away.

**Debugging leverage:** identify the zone first. A 60 Hz problem is *never* radiation — hunting for "RF pickup" fixes is wasted; it's mutual C or M and geometry (distance, loop area, shielding) is the whole game. Conversely a 1 GHz problem at 3 m is pure far-field: think antennas and apertures, not loop area.

> [!question]- Moving the victim cable 2× farther from a switching supply drops 100 kHz pickup by ~18 dB. Near or far field?
> Near field — 18 dB per doubling is $1/r^3$, the reactive dipole term (λ/2π at 100 kHz is 500 m, so far field was never in play). Far-field pickup would drop only 6 dB per doubling.

# Connections

- [[Noise Coupling Mechanisms]] — near field splits into the capacitive and inductive rows of the table; far field is the radiated row
- [[Retarded Potentials]] — retardation is what separates the zones
- [[Dipole Radiation]] — the source expansion whose three powers of 1/r define the boundary
- [[Antennas]] — far-field pickup efficiency is antenna physics; near-field is transformer/capacitor physics
- [[Electromagnetic Shielding]] — why near-field magnetic sources are the case ordinary shields handle worst

---
Source: Jackson, *Classical Electrodynamics*, §9.1–9.2
