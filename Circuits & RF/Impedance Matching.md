#circuits #electronics

**Maximum power transfers when the load is the complex conjugate of the source ($Z_L = Z_S^*$); on 50 Ω lines the same condition kills reflections.** Match when power or reflections matter; deliberately mismatch (bridge) when voltage fidelity matters.

# Reference

**When to match:** RF systems, lines longer than ~λ/10, power delivery (amps → antennas/AOMs), anywhere reflections cause ringing or standing waves.
**When to bridge:** audio and low-frequency instrumentation — low-Z source into high-Z load preserves the voltage and skips the 6 dB (half the voltage) plus noise that a matched pad costs.

**L-network (two elements, the workhorse)** for $R_\text{high} \to R_\text{low}$:
$$
Q = \sqrt{\frac{R_\text{high}}{R_\text{low}} - 1}
$$

$Q$ = loaded quality factor of the matching section (dimensionless) — here it plays two roles at once: it is the reactance-to-resistance ratio each element must have, *and* it sets the bandwidth. $R_\text{high}, R_\text{low}$ = the two resistances being matched (Ω). Series reactance $QR_\text{low}$ on the low side, shunt reactance $R_\text{high}/Q$ across the high side; pick L/C placement for a low-pass topology so harmonics are filtered for free.

**Bandwidth cost:** the match holds over roughly $f_0/Q$, so with $Q \approx \sqrt{R_\text{high}/R_\text{low}}$ the fractional bandwidth goes as the inverse square root of the transformation ratio — big ratios are inherently narrowband. 50 Ω → 5 kΩ: Q ≈ 10, ~10% bandwidth. Broadband needs cascaded L-sections (each with lower Q) or a transmission-line transformer.

Worked numbers: 50 → 200 Ω at 100 MHz: $Q = \sqrt3 \approx 1.7$; series X = 87 Ω (139 nH), shunt X = 115 Ω (13.8 pF).

> [!question]- Why does a 6 dB matched attenuator pad "fix" a misbehaving RF source, and what does it cost?
> The pad presents ~50 Ω both directions regardless of what's behind it, and reflected power crosses it twice — return loss improves by 12 dB. Cost: 6 dB of signal. Stability bought with power.

# Connections

- [[Characteristic Impedance and Reflection]] — Γ, the quantity matching drives to zero
- [[Smith Chart]] — the graphical L-network designer
- [[LC Resonators]] — the same Q/bandwidth arithmetic wearing a different hat
- [[Transmission Lines]] — where and why 50 Ω became the boundary condition

---
Source: Pozar, *Microwave Engineering* 4th ed., Ch. 5
