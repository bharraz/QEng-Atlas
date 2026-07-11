#EnM

**When a cable is longer than a fraction of a wavelength, voltage and current become waves propagating on its distributed L and C** — the lumped-circuit picture dies and every wire becomes a wave medium with its own impedance.

# Reference

Telegrapher equations for per-length inductance $L$ and capacitance $C$ (lossless):

$$
\frac{\partial V}{\partial z} = -L\frac{\partial I}{\partial t}, \quad \frac{\partial I}{\partial z} = -C\frac{\partial V}{\partial t}
\;\Rightarrow\; v = \frac{1}{\sqrt{LC}}, \quad Z_0 = \sqrt{\frac{L}{C}}
$$

$Z_0$ is the V/I ratio of a single traveling wave — real, but **not a resistance** (no dissipation; it's the ratio the wave carries with it).

**When do you care?** Rule of thumb: treat as a transmission line when length ≳ **λ/10** — equivalently when the round-trip delay is comparable to your signal's rise time ($\ell \gtrsim v\,t_r/6$). Coax delay ≈ 5 ns/m ($v \approx 0.66c$ for solid PE): a 1 m cable is "long" above ~20 MHz, or for edges faster than ~30 ns. Digital edges, not clock rates, set this.

| Line | Z₀ |
|---|---|
| Standard coax (RG-58, SMA ecosystem) | 50 Ω |
| Video/antenna coax (RG-59/6) | 75 Ω |
| Twisted pair | ~100–120 Ω |
| PCB microstrip/stripline | designable 40–120 Ω via w/h |

Coax: $Z_0 = \frac{1}{2\pi}\sqrt{\mu/\epsilon}\,\ln(b/a) \approx \frac{60}{\sqrt{\epsilon_r}}\ln(b/a)$ Ω. Loss ∝ √f from skin effect, plus dielectric loss ∝ f taking over at GHz.

**Termination:** a line ended in $Z_L = Z_0$ absorbs the wave completely — the line looks like a resistor from any length away. Anything else reflects; that's the next card.

> [!question]- Why does a 2 m scope probe cable show clean 10 MHz sine waves but mangle 5 ns edges?
> The edge has content past 100 MHz where 2 m ≫ λ/10; without matched termination each edge reflects off the unmatched ends and rings. The 10 MHz sine (λ ≈ 20 m in cable) still sees a lumped circuit.

# Connections

- [[Characteristic Impedance and Reflection]] — what happens at the end of the line: Γ, standing waves, ringing
- [[Capacitance and Inductance]] — supplies the per-length L and C (coax formulas live there)
- [[Impedance Matching]] — when and how to make $Z_L = Z_0$ on purpose
- [[Skin Depth]] — the √f conductor loss in real coax
- [[Cable Care and Connectors]] — which physical cable/connector at which frequency

---
Source: Pozar, *Microwave Engineering*, Ch. 2
