#circuits #electronics

**A chip draws its supply current in fast spikes, and the power supply sits at the end of wiring whose inductance keeps it from delivering a spike quickly, so the voltage at the chip's supply pin dips with every spike.** A decoupling capacitor next to the pin is a local charge reservoir and an RF short: chip current spikes get served from millimeters away instead of from the far end of the supply wiring, and noise on the supply line (the rail) sees a low-impedance path to ground before entering the chip. What limits it is not the capacitance but the inductance between the capacitor and the pin.

# Reference

**Defaults that work:** 100 nF ceramic (X7R or X5R, the common ceramic dielectrics with moderate temperature stability) **at every supply pin, as close as layout allows**, plus 1–10 µF bulk per rail region, plus a board-level electrolytic. Decade-spaced values are the tradition; many-of-the-same-value is the modern view of the power distribution network (PDN), the entire set of supply planes, traces, and capacitors seen from the chip.

**Why "close" is the spec:** trace + via inductance ≈ **1 nH/mm**. The cap is really a series RLC, which resonates at its self-resonant frequency (SRF):
$$
f_\text{SRF} = \frac{1}{2\pi\sqrt{LC}}
$$
100 nF with 2 nH is self-resonant at ~11 MHz and **inductive above** — at 100 MHz your "capacitor" is about an ohm of inductive reactance. A shorter cap→pin→via loop is worth more than more microfarads.

**Picture:** a small water tank beside each tap: the main supply is far away down a narrow pipe, so sudden demand is served from the tank, and the pipe refills it slowly.

**Anti-resonance:** two different-value caps in parallel form a parallel LC between their SRFs — an impedance *peak* right where you assumed coverage. If it causes trouble, damp it with the capacitors' equivalent series resistance (ESR) or use same-value multiples.

**Symptoms of inadequate decoupling:** unexplained oscillation in fast op-amps, logic glitches correlated with output switching, clock harmonics appearing on every rail (common-impedance coupling through the supply).

> [!question]- Why doesn't swapping the 100 nF for 10 µF at the pin fix 100 MHz supply noise, when a *better-placed* 100 nF does?
> Above self-resonance only loop inductance matters, and the bigger package's L is the same or worse — capacitance value is irrelevant at 100 MHz. Placement (loop area) sets the high-frequency impedance.

# Connections

- [[Capacitance and Inductance]] — the ~nH/mm, ~pF/cm parasitics that set this behaviour
- [[Grounding and Shielding Practice]] — decoupling is the power-rail half of return-current management
- [[Noise Coupling Mechanisms]] — poor decoupling = common-impedance coupling via the supply
- [[Op-Amp Golden Rules and Real Limits]] — undecoupled op-amps oscillate through supply feedback
- [[Capacitors in Practice]] — dielectrics, DC-bias derating, and failure modes
- [[Filtering Power and Signal Lines]] — filtering whole lines rather than single supply pins

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Ch. 11
