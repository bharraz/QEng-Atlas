#optics

**A periodic surface kicks light by transverse momentum in quanta of $2\pi/d$, sending each wavelength into its own discrete angle** — dispersion from interference, no material dispersion needed.

# Reference

Grating equation (angles from grating normal, $d$ = groove spacing = 1/line density):
$$
d\,(\sin\theta_m - \sin\theta_i) = m\lambda
$$

**Resolving power:**
$$
\frac{\lambda}{\Delta\lambda} = mN
$$

$m$ = diffraction order (integer); $N$ = number of *illuminated* grooves = beam footprint ÷ groove spacing; $\lambda/\Delta\lambda$ = resolving power (dimensionless). Both factors do the same thing — $mN$ counts total wavelengths of path difference across the beam, so resolution is really "how many wave periods you can make interfere," whether by using more grooves or by taking a higher order. Note $N$ is the number of *illuminated* grooves — resolution comes from the beam footprint on the grating, not just groove density. Under-fill the grating and you throw resolution away.

**Blaze:** grooves are tilted micro-mirrors so specular reflection off each facet coincides with the chosen order — concentrates power into one order at the blaze wavelength instead of splattering across all $m$.

**Littrow:** $\theta_m = \theta_i$, i.e. $2d\sin\theta = m\lambda$ — the order retroreflects. This is the ECDL geometry: first order feeds back into the diode and pulls the lasing wavelength, zeroth order is your output, and turning the grating tunes the laser (with the beam-walk penalty every ECDL owner knows).

> [!question]- Why does resolving power scale with the number of illuminated grooves?
> $N$ grooves interfere like an $N$-slit array: principal maxima sharpen as $1/N$ (phased-array logic). Sharper order peaks = smaller resolvable $\Delta\lambda$; formally $\delta\lambda/\lambda = 1/mN$.

# Connections

- [[Diffraction]] — a grating is a periodic aperture; the orders are the FT of a comb
- [[Laser Fundamentals]] — Littrow feedback is the standard single-mode selection trick for diode lasers
- [[Acousto-Optic Modulator]] — a traveling index grating: same Bragg condition, plus a frequency shift
- [[Fourier Transform]] — discrete orders = discrete spectrum of a periodic transmission function

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 2 & 4
