#EnM

**A field polarizes matter — each atom acquires an induced dipole $\mathbf{p}=\alpha\mathbf{E}$ — and the material's response is the sum: $\mathbf{P}=\varepsilon_0\chi\mathbf{E}$.** The macroscopic ε and the microscopic α are the same physics at two zoom levels.

# Reference

$$
\mathbf{P} = \varepsilon_0\chi\mathbf{E}, \qquad \mathbf{D}=\varepsilon_0(1+\chi)\mathbf{E} = \varepsilon_0\varepsilon_r\mathbf{E}, \qquad n=\sqrt{\varepsilon_r} \ \ (\mu_r\approx1)
$$

Bound charge: $\rho_b=-\nabla\cdot\mathbf{P}$, $\sigma_b=\mathbf{P}\cdot\hat{n}$ — polarization piles up charge where it starts, stops, or varies.

**Micro→macro (Clausius–Mossotti):** with number density $N$ and the local-field correction,
$$
\frac{\varepsilon_r - 1}{\varepsilon_r + 2} = \frac{N\alpha}{3\varepsilon_0}
$$
Dilute limit: $\varepsilon_r\approx 1+N\alpha/\varepsilon_0$.

**α is frequency-dependent** — a driven-oscillator response with resonances at the transitions: large and real far below resonance, dispersive/absorptive near it. Evaluated at optical ω, **α is exactly what sets AC Stark shifts: $U=-\frac{1}{2}\alpha(\omega)\langle E^2\rangle$** — a dipole trap is a region of high $E^2$ and a light shift is the same expression rebranded. Sign flips with detuning because α does. DC α also gives static Stark shifts and blackbody shifts in clocks.

Practical numbers: $\varepsilon_r\approx$ 2.1 (PTFE), 3.9 (SiO₂), 4.4 (FR4), ~80 (water, DC). Energy density in a dielectric $\frac{1}{2}\mathbf{E}\cdot\mathbf{D}$; capacitors scale by $\varepsilon_r$.

> [!question]- Why is the trap depth of a far-red-detuned dipole trap and the refractive index of glass "the same physics"?
> Both are $\alpha(\omega)$ below resonance: real, positive polarizability. In glass, dense packing sums to $n>1$ (phase delay); on an atom, the induced dipole's $-\frac{1}{2}\alpha E^2$ energy is lowest where intensity is highest — attraction to the focus.

# Connections

- [[Stark Effect and Light Shifts]] — $-\frac{1}{2}\alpha E^2$ with quantum α; the trap/shift duality
- [[Fresnel Equations]] — ε mismatch at interfaces is what reflects light
- [[Dispersion Relations]] — α(ω) makes ε(ω); resonances make dispersion
- [[Kramers-Kronig Relations]] — the real and imaginary parts of α(ω) are causally locked
- [[Capacitance and Inductance]] — the humble application: ε_r multiplies C

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 4
