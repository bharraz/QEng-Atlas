#EnM

**Conducting walls force transverse standing-wave patterns, and each pattern (mode) only propagates above its own cutoff frequency** — below cutoff the wave doesn't travel, it dies exponentially, which is a feature you can shield with.

# Reference

For each mode, the guide dispersion relation:

$$
k_z^2 = \frac{\omega^2}{c^2} - k_\perp^2, \qquad f_c = \frac{c\,k_\perp}{2\pi}
$$

$k_z$ = propagation constant along the guide (m⁻¹); $\omega/c$ = the free-space wavevector the wave would have (m⁻¹); $k_\perp$ = transverse wavevector (m⁻¹), fixed entirely by the cross-section geometry and boundary conditions — for a rectangular guide $k_\perp = \sqrt{(m\pi/a)^2 + (n\pi/b)^2}$, so it is set by the guide dimensions, not the drive; $f_c$ = cutoff frequency (Hz). The relation is Pythagorean: the total wavevector is fixed by frequency and split between transverse (spent on fitting the boundary) and longitudinal (left over for travel). When the geometry demands more transverse wavevector than the frequency provides, $k_z^2 < 0$ and the wave is evanescent. Above $f_c$: propagation with $v_g < c < v_p$. Below $f_c$: $k_z$ imaginary — **evanescent decay** $e^{-z/\ell}$, $\ell = c/\sqrt{\omega_c^2 - \omega^2} \to c/\omega_c$ well below cutoff.

**Rectangular guide (a × b, a > b):** dominant mode is **TE₁₀** ($E$ vertical, one half-sine across the broad wall), $f_c = c/2a$. Single-mode band runs from $f_c$ to $2f_c$ (next mode) — e.g. WR-90: 8.2–12.4 GHz. TE modes have $E_z=0$; TM modes $B_z=0$; hollow single-conductor guides support **no TEM mode** (that needs two conductors — that's a [[Transmission Lines]] job).

**Below-cutoff evanescence as engineering:** a hole of diameter $d$ in a shield is a circular guide with $f_c \approx 1.76\,c/(\pi d)$ — far above any frequency of concern for small holes — so making the hole a *tube* (depth ≳ diameter) buys exponential attenuation, ~32 dB per diameter of depth. This is the honeycomb-vent and viewing-port trick.

Optical fibers are the dielectric version: total internal reflection replaces the conducting wall, same mode/cutoff structure.

> [!question]- Why does making a shield penetration deeper (a tube instead of a hole) improve shielding so dramatically?
> Below cutoff the field decays exponentially along the tube, ~32 dB per diameter of depth. A hole only offers its aperture impedance mismatch; a tube multiplies that by $e^{-k_\perp L}$.

# Connections

- [[Cavity Modes]] — cap both ends: $k_z$ quantizes too and the mode spectrum goes fully discrete
- [[Evanescent Waves]] — below-cutoff behavior is the same physics as TIR tunneling
- [[Electromagnetic Boundary Conditions]] — $E_\parallel = 0$ at the walls is what quantizes $k_\perp$
- [[Electromagnetic Shielding]] — waveguide-below-cutoff is how you put holes in a shield without ruining it
- [[Dispersion Relations]] — the guide dispersion is the plasma-type cutoff form; all the $v_p v_g = c^2$ consequences apply

---
Source: Pozar, *Microwave Engineering*, Ch. 3
