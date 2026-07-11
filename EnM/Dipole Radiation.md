#EnM

**An oscillating dipole radiates with power ∝ ω⁴p², in a donut pattern with zero emission along the dipole axis.** The ω⁴ is why the sky is blue, why UV transitions are fast, and why high-frequency currents on your cables radiate so much better than low-frequency ones.

# Reference

Time-averaged total power of a dipole $p(t)=p_0\cos\omega t$:
$$
P = \frac{\omega^4 p_0^2}{12\pi\varepsilon_0 c^3}, \qquad \frac{dP}{d\Omega} \propto \sin^2\theta
$$

$\theta$ measured from the dipole axis: **maximum broadside, exactly zero along the axis.** The radiated fields fall as $1/r$ (so power $\sim 1/r^2$ survives to infinity), transverse, with $E/H=\eta_0$.

**Larmor** (same physics, accelerating point charge): $P = q^2 a^2/6\pi\varepsilon_0 c^3$.

**Two big customers:**
- **Antennas** — a short current element is literally this; real antennas are integrals of it, and the $\sin^2\theta$ donut is the λ/2 dipole's pattern to good approximation.
- **Atomic spontaneous emission** — quantize and $p_0\to$ dipole matrix element: $\Gamma = \omega^3 d^2/3\pi\varepsilon_0\hbar c^3$. The $\omega^3$ (rate, not power) is why blue transitions have Γ/2π ~ 20 MHz while IR ones are kHz, and why clock states are chosen where $d\approx 0$.

**Pattern gotcha:** an atom emitting on a $\Delta m=0$ ($\pi$) transition radiates *nothing* along the B-field axis — collection efficiency depends on where your objective sits relative to the quantization axis.

> [!question]- Two effects of the $\omega^4$: why is scattered skylight blue, and why does the same cable radiate ~80 dB more at 100 MHz than at 1 kHz?
> Rayleigh scattering is re-radiation by induced dipoles, so blue (higher ω) wins by $(\omega_b/\omega_r)^4\approx 5\times$. And a fixed stray current on a cable radiates $\propto\omega^4$ ($\omega^2$ from $\ddot{p}$, squared) — low-frequency noise couples by induction instead, because radiation is hopeless there.

# Connections

- [[Spontaneous Emission and Linewidth]] — the quantum version; matrix element in place of $p_0$
- [[Antennas]] — engineered dipole radiation; reciprocity makes it the pickup pattern too
- [[Poynting Vector and Energy Flow]] — integrate $\mathbf{S}$ over the sphere to get $P$
- [[Near and Far Field]] — the $1/r$ radiation field is only the far zone; up close the dipole is quasi-static
- [[Multipole Expansion]] — dipole is just the leading radiating term; E2/M1 follow

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 11.1; Jackson Ch. 9
