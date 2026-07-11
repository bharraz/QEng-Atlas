#optics

**The far-field diffraction pattern is the Fourier transform of the aperture** — each aperture point radiates, and in the far field the phases add with a linear kernel $e^{ikx\sin\theta}$, which is literally an FT with conjugate variable $\sin\theta/\lambda$. Confine light to size $a$, pay $\sim\lambda/a$ in angular spread.

# Reference

Fraunhofer regime: Fresnel number $N_F = a^2/\lambda z \ll 1$ (or at a lens focal plane, always). Closer in ($N_F \gtrsim 1$) is Fresnel diffraction — near-field ripples, no clean FT.

**Single slit**, width $a$:
$$
I(\theta) = I_0\,\mathrm{sinc}^2\!\left(\frac{\pi a \sin\theta}{\lambda}\right), \qquad \text{first zero at } \sin\theta = \lambda/a
$$

**Circular aperture**, diameter $D$ — Airy pattern:
$$
\sin\theta_{\text{first dark ring}} = 1.22\,\frac{\lambda}{D}
$$

**Resolution limits follow directly.** Rayleigh criterion: two points are resolved when one peak sits on the other's first null → angular resolution $1.22\lambda/D$, focused spot size $\approx 1.22\,\lambda f/D$. So the f-number, not the lens quality, sets your addressing-beam spot — and clipping a beam on a small optic buys you diffraction rings plus extra divergence.

Same physics as Gaussian beam divergence $\theta = \lambda/\pi w_0$: diffraction is just the uncertainty principle for transverse position and momentum.

> [!question]- Why is the far-field pattern the Fourier transform of the aperture?
> Every aperture point emits a wavelet; toward angle $\theta$ the point at $x$ contributes phase $e^{ikx\sin\theta}$. Summing the aperture function against that kernel is exactly a Fourier transform evaluated at spatial frequency $\sin\theta/\lambda$. Hard edges = high spatial frequencies = wide-angle ringing.

# Connections

- [[Fourier Transform]] — the far field computes it optically; aperture and angular spectrum are an FT pair
- [[Diffraction Gratings]] — periodic aperture ⇒ the FT is a comb of discrete orders
- [[Gaussian Beams]] — $\theta = \lambda/\pi w_0$ divergence is diffraction; Gaussians are self-Fourier beams
- [[Acousto-Optic Modulator]] — Bragg diffraction off a sound-written index grating

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 4 (Fourier optics)
