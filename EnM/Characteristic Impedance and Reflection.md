#EnM

**Whatever fraction of the wave the load can't absorb, it reflects** — the mismatch between load and line impedance sets the reflected amplitude, and in the time domain those reflections are the ringing on your scope.

# Reference

$$
\Gamma = \frac{Z_L - Z_0}{Z_L + Z_0}
$$

| Load | Γ | What comes back |
|---|---|---|
| Matched ($Z_L = Z_0$) | 0 | nothing — line looks infinite |
| Open | +1 | full reflection, same sign (V doubles at the open end) |
| Short | −1 | full reflection, inverted |
| $Z_L = 2Z_0$ | +1/3 | partial |

Reflected power fraction $= |\Gamma|^2$; return loss $= -20\log|\Gamma|$ dB.

**Frequency domain:** incident + reflected waves interfere into a standing-wave pattern along the line; $\mathrm{VSWR} = (1+|\Gamma|)/(1-|\Gamma|)$ is what you read off the peak/trough ratio (VSWR 1.5 ↔ |Γ| = 0.2 ↔ 4% power reflected). The input impedance of a mismatched line rotates with length — a λ/4 line transforms $Z_{in} = Z_0^2/Z_L$ (shorts become opens!).

**Time domain — the debugging picture:** drive an edge into an unterminated line and it bounces between the unmatched source and load, one round-trip time apart, until the bounces decay: **that's the ringing on fast digital edges and pulse lines.** The staircase/oscillation period gives you the cable's electrical length (TDR is exactly this). Fixes: series resistor at the source ($R_s + Z_{out} = Z_0$, one clean bounce absorbed at the source) or parallel $Z_0$ at the load. A scope's 1 MΩ input on a 50 Ω line *is* an open — switch in the 50 Ω termination.

> [!question]- An edge into a 3 m unterminated coax rings with period ~30 ns. Why that number, and what kills it?
> Round trip = 2 × 3 m × 5 ns/m = 30 ns: the edge reflects off the open far end (Γ=+1) and again off the low-Z source (Γ≈−1), flipping sign each lap. Terminate one end in Z₀ — series 50 Ω at the driver or shunt 50 Ω at the load.

# Connections

- [[Transmission Lines]] — where Z₀ and the wave picture come from
- [[S-Parameters]] — S11 *is* Γ measured at a port; the VNA formalization
- [[Smith Chart]] — Γ-plane map; line length = rotation, matching = walking to center
- [[Impedance Matching]] — the networks that force Γ → 0
- [[Fresnel Equations]] — same mismatch-reflection structure with wave impedances of media

---
Source: Pozar, *Microwave Engineering*, Ch. 2.3
