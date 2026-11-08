#EnM

**A hollow metal pipe can carry an electromagnetic wave, but its conducting walls force transverse standing-wave patterns, and each pattern (mode) only propagates above its own cutoff frequency** — below cutoff the wave doesn't travel, it decays exponentially, which is what below-cutoff shielding uses.

# Reference

For each mode, the guide dispersion relation:

$$
k_z^2 = \frac{\omega^2}{c^2} - k_\perp^2, \qquad f_c = \frac{c\,k_\perp}{2\pi}
$$

- $k_z$ — propagation constant along the guide (m⁻¹)
- $\omega/c$ — the free-space wavevector the wave would have (m⁻¹)
- $k_\perp$ — transverse wavevector (m⁻¹): fixed by the cross-section alone, $\sqrt{(m\pi/a)^2+(n\pi/b)^2}$ for a rectangular guide
- $f_c$ — cutoff frequency (Hz)

The relation is Pythagorean: the total wavevector is fixed by frequency and split between transverse (spent on fitting the boundary) and longitudinal (left over for travel). When the geometry demands more transverse wavevector than the frequency provides, $k_z^2 < 0$ and the wave is evanescent. Above $f_c$: propagation with $v_g < c < v_p$. Below $f_c$: $k_z$ imaginary — **evanescent decay** $e^{-z/\ell}$, $\ell = c/\sqrt{\omega_c^2 - \omega^2} \to c/\omega_c$ well below cutoff.

**Picture:** a wave bouncing between the walls at an angle: lower frequencies need steeper angles, and at cutoff the wave bounces straight across without moving down the pipe.

**Mode names:** a mode is labelled by which field has no component along the guide — TE (transverse electric) modes have $E_z=0$; TM (transverse magnetic) modes $B_z=0$; TEM (transverse electromagnetic) modes have neither. Hollow single-conductor guides support **no TEM mode** (that needs two conductors — that's a [[Transmission Lines]] job). The indices $m, n$ count half-wavelengths across the broad and narrow walls.

**Rectangular guide (a × b, a > b):** dominant mode is **TE₁₀** ($E$ vertical, one half-sine across the broad wall), $f_c = c/2a$. Single-mode band runs from $f_c$ to $2f_c$ (next mode) — e.g. WR-90 (the standard designation for a 22.9 × 10.2 mm guide): $f_c = 6.56$ GHz, with a recommended operating band of 8.2–12.4 GHz kept inside the single-mode range with margin at both ends.

**Below-cutoff evanescence as engineering:** a hole of diameter $d$ in a shield is a circular guide with $f_c \approx 1.84\,c/(\pi d)$ (its lowest mode, TE₁₁) — far above any frequency of concern for small holes — so making the hole a *tube* (depth ≳ diameter) gives exponential attenuation, ~32 dB per diameter of depth. This is how honeycomb vents and viewing ports block RF while staying open to air and light.

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
