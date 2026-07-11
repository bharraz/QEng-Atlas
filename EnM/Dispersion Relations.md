#EnM

**A dispersion relation ω(k) is the medium's complete answer to "how do waves move here"** — its slope at a point is how fast a wavepacket travels, its curvature is how fast that packet falls apart.

# Reference

$$
v_p = \frac{\omega}{k}, \qquad v_g = \frac{d\omega}{dk}
$$

Phase velocity moves the carrier ripples; **group velocity moves the envelope, the energy, and the information** (in transparent regions). They coincide only when ω(k) is a straight line through the origin — vacuum, ideally.

**Recognition table:**

| System | ω(k) | Behavior |
|---|---|---|
| Vacuum | $\omega = ck$ | dispersionless |
| Plasma / waveguide | $\omega^2 = \omega_c^2 + c^2k^2$ | cutoff below $\omega_c$; $v_p > c$, $v_g < c$, $v_pv_g = c^2$ |
| Dielectric | $\omega = ck/n(\omega)$ | normal dispersion: $dn/d\omega > 0$ (blue bends more) |
| Near absorption line | anomalous: $dn/d\omega < 0$ | $v_g$ can exceed c or go negative — no signal violation, the pulse reshapes |

**Pulse spreading:** group velocity dispersion $\beta_2 = d^2k/d\omega^2$ makes different frequency components of a pulse walk at different speeds — a transform-limited pulse of duration τ doubles after $L \sim \tau^2/\beta_2$. This is the fiber-optics chirp problem and why fs pulses need dispersion compensation.

$v_p > c$ is common (waveguides, plasmas) and harmless: no energy or signal rides pure phase fronts.

> [!question]- In a waveguide near cutoff, which velocity dives toward zero and which diverges?
> $v_g \to 0$ (energy barely crawls forward — the wave is mostly bouncing transversely) while $v_p \to \infty$. Their product stays $c^2$.

# Connections

- [[Plasma Frequency and Drude Model]] — the canonical cutoff dispersion relation, same form as a waveguide's
- [[Waveguides]] — geometry manufactures an effective mass/cutoff for photons
- [[Kramers-Kronig Relations]] — causality ties the dispersive (real) part to absorption; anomalous dispersion *must* sit on an absorption line
- [[Optical Fibers and Fiber Coupling]] — GVD-driven pulse spreading is the practical cost of ω(k) curvature
- [[Fourier Transform]] — the packet picture: each k-component propagates with its own phase $e^{i(kx-\omega(k)t)}$

---
Source: Jackson, *Classical Electrodynamics*, §7.5 & §7.8–7.9
