#EnM

**Treat a metal's electrons as a free, collisionally-damped gas and you get its entire optical response** — below the plasma frequency the electrons keep up with the field and cancel it (mirror), above it they can't and the metal goes transparent.

# Reference

Free electrons of density $n$, collision time $\tau$:

$$
\sigma(\omega) = \frac{\sigma_0}{1 - i\omega\tau}, \quad \sigma_0 = \frac{ne^2\tau}{m}, \qquad \omega_p^2 = \frac{ne^2}{m\epsilon_0}
$$

In the collisionless limit ($\omega\tau \gg 1$) the dielectric function and dispersion relation:

$$
\epsilon(\omega) = 1 - \frac{\omega_p^2}{\omega^2}, \qquad \omega^2 = \omega_p^2 + c^2k^2
$$

- $\omega < \omega_p$: $\epsilon < 0$, $k$ imaginary — waves are **evanescent**, penetrating only $\sim c/\omega_p$ (~25 nm for metals) before total reflection. **This is why metals are shiny.**
- $\omega > \omega_p$: $\epsilon > 0$, the metal transmits. For typical metals $\omega_p/2\pi \sim 2000$ THz (UV) — hence **X-ray transparency**, and why alkali metals go transparent already in the UV.
- Same relation governs the ionosphere ($f_p \sim$ 3–10 MHz): shortwave bounces, GHz satellite signals punch through.

**Regime map for a metal:** at low frequency ($\omega\tau \ll 1$) conduction is resistive and fields die by [[Skin Depth]] diffusion; near optical frequencies the response is the reactive plasma one above; the crossover is set by $1/\tau \sim 10{-}40$ THz at room temperature.

> [!question]- Why can the ionosphere reflect a 5 MHz signal but not 5 GHz?
> Its electron density gives $f_p \sim$ few–10 MHz. Below $f_p$, $\epsilon<0$ and the wave is evanescent — reflected back down. At 5 GHz $\gg f_p$, $\epsilon \approx 1$ and the layer is transparent.

# Connections

- [[Dispersion Relations]] — $\omega^2 = \omega_p^2 + c^2k^2$ is *the* cutoff dispersion, mathematically identical to a waveguide's
- [[Skin Depth]] — the resistive small-ωτ limit of the same σ(ω)
- [[Evanescent Waves]] — sub-$\omega_p$ fields in the metal are evanescent, not absorbed-and-gone (frustration possible in thin films)
- [[Dielectrics and Polarizability]] — bound-electron (Lorentz) version: add a spring, get resonances instead of a cutoff

---
Source: Jackson, *Classical Electrodynamics*, §7.5(D)
