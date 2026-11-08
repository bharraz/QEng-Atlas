#circuits #electronics

**A source with internal impedance $Z_S$ delivers maximum power when the load is its complex conjugate ($Z_L = Z_S^*$); on 50 Ω lines the same condition kills reflections.** Match when power or reflections matter; when voltage fidelity matters, deliberately mismatch instead — *bridging*, a low-impedance source driving a high-impedance load.

# Reference

**When to match:** RF systems, lines longer than ~λ/10, power delivery (amps → antennas/[[Acousto-Optic Modulator|AOMs]]), anywhere reflections cause ringing or standing waves.
**When to bridge:** audio and low-frequency instrumentation — low-Z source into high-Z load preserves the voltage and skips the 6 dB (half the voltage) plus noise that a matched pad (a fixed attenuator that looks like 50 Ω from both sides) costs.

**L-network** — one series and one shunt reactance, the simplest and most common matching network (two elements) — for $R_\text{high} \to R_\text{low}$:
$$
Q = \sqrt{\frac{R_\text{high}}{R_\text{low}} - 1}
$$

- $Q$ — loaded quality factor of the matching section (dimensionless): each element's reactance-to-resistance ratio, *and* the bandwidth
- $R_\text{high}, R_\text{low}$ — the two resistances being matched (Ω)

Series reactance $QR_\text{low}$ on the low side, shunt reactance $R_\text{high}/Q$ across the high side. Choosing the inductor in series and the capacitor in shunt makes a low-pass topology, so harmonics are filtered as well.

**Picture:** two ropes of different mass per length joined end to end: a wave partly reflects at the junction unless a matching section between them makes the transition tuned or gradual.

**Bandwidth cost:** the match holds over roughly $f_0/Q$, so with $Q \approx \sqrt{R_\text{high}/R_\text{low}}$ the fractional bandwidth goes as the inverse square root of the transformation ratio — big ratios are inherently narrowband. 50 Ω → 5 kΩ: Q ≈ 10, ~10% bandwidth. Broadband needs cascaded L-sections (each with lower Q) or a transmission-line transformer.

Worked numbers: 50 → 200 Ω at 100 MHz: $Q = \sqrt3 \approx 1.7$; series X = 87 Ω (139 nH), shunt X = 115 Ω (13.8 pF).

> [!question]- Why does a 6 dB matched attenuator pad "fix" a misbehaving RF source, and what does it cost?
> The pad presents ~50 Ω both directions regardless of what's behind it, and reflected power crosses it twice — return loss improves by 12 dB. Cost: 6 dB of signal. Stability at the cost of power.

# Connections

- [[Characteristic Impedance and Reflection]] — Γ, the quantity matching drives to zero
- [[Smith Chart]] — the graphical L-network designer
- [[Complex Impedance]] — resistance and reactance, the two parts a match handles differently
- [[LC Resonators]] — the same Q/bandwidth arithmetic in a resonator
- [[Transmission Lines]] — where and why 50 Ω became the boundary condition

---
Source: Pozar, *Microwave Engineering* 4th ed., Ch. 5
