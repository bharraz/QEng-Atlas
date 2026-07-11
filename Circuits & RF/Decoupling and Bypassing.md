#circuits #electronics

**A decoupling cap is a local charge reservoir and an RF short: chip current spikes get served from millimeters away instead of dragging the whole supply net, and rail noise sees a low-Z path to ground before entering the chip.** The enemy is not capacitance — it's the inductance between cap and pin.

# Reference

**Defaults that work:** 100 nF ceramic (X7R/X5R) **at every supply pin, as close as layout allows**, plus 1–10 µF bulk per rail region, plus a board-level electrolytic. Decade-spaced values are the tradition; many-of-the-same-value is the modern PDN view.

**Why "close" is the spec:** trace + via inductance ≈ **1 nH/mm**. The cap is really a series RLC:
$$
f_\text{SRF} = \frac{1}{2\pi\sqrt{LC}}
$$
100 nF with 2 nH is self-resonant at ~11 MHz and **inductive above** — at 100 MHz your "capacitor" is a few ohms of inductor. A shorter cap→pin→via loop is worth more than more microfarads.

**Anti-resonance gotcha:** two different-value caps in parallel form a parallel LC between their SRFs — an impedance *peak* right where you assumed coverage. If it bites, damp with ESR or use same-value multiples.

**Symptoms of inadequate decoupling:** unexplained oscillation in fast op-amps, logic glitches correlated with output switching, clock harmonics appearing on every rail (common-impedance coupling through the supply).

> [!question]- Why doesn't swapping the 100 nF for 10 µF at the pin fix 100 MHz supply noise, when a *better-placed* 100 nF does?
> Above self-resonance only loop inductance matters, and the bigger package's L is the same or worse — capacitance value is irrelevant at 100 MHz. Placement (loop area) sets the high-frequency impedance.

# Connections

- [[Capacitance and Inductance]] — the ~nH/mm, ~pF/cm parasitics that run this show
- [[Grounding and Shielding Practice]] — decoupling is the power-rail half of return-current management
- [[Noise Coupling Mechanisms]] — poor decoupling = common-impedance coupling via the supply
- [[Op-Amp Golden Rules and Real Limits]] — undecoupled op-amps oscillate through supply feedback

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Ch. 11
