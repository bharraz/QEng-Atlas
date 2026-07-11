#circuits #electronics

**The Smith chart is the complex Γ-plane with a grid of constant-resistance circles and constant-reactance arcs drawn on it — impedance and reflection coefficient visible simultaneously, so matching becomes walking a point to the center.**

# Reference

Normalize $z = Z/Z_0$; then $\Gamma = (z-1)/(z+1)$ maps the entire right-half impedance plane into the unit disc.

**Reading it:**
- Center = $Z_0$ (matched, Γ = 0); left edge = short, right edge = open
- **Circles** = constant R; **arcs** = constant X (upper half inductive, lower capacitive)
- Distance from center = $|\Gamma|$; circles about the center = constant VSWR

**Moving along a lossless line** = rotation about the center, **clockwise toward the generator**, one full turn per λ/2 — which is why impedance repeats every half wavelength.

**Matching moves:**
- Series L or C: slide along a constant-R circle (up = L, down = C)
- Shunt L or C: reflect through the center (admittance chart), slide along constant-G
- An L-network = two slides that land on the center; the chart shows both solutions at a glance

Still the default display on every VNA — worth reading fluently even if you never design on paper.

> [!question]- A VNA trace of an antenna hugs the chart edge but sweeps through near the center at 145 MHz. Translate.
> Near the edge = |Γ| ≈ 1, badly mismatched off resonance; the pass near center = resonance where it presents ≈ 50 Ω. Usable bandwidth = the piece of trace inside your acceptable-VSWR circle.

# Connections

- [[Characteristic Impedance and Reflection]] — Γ, the coordinate this chart plots
- [[Impedance Matching]] — the design activity the chart makes visual
- [[S-Parameters]] — S11 is what the VNA draws on the chart
- [[Transmission Lines]] — the λ/2 rotation rule is line physics

---
Source: Pozar, *Microwave Engineering* 4th ed., §2.4
