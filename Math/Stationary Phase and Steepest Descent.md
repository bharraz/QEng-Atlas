#math

**An integral with a large parameter in the exponent is dominated by a single point — where the exponent is stationary — and the whole method is expanding around that point and doing the resulting Gaussian.**

# Reference

Three names for one idea, differing only in whether the exponent is real, imaginary, or complex:

| Method | Integral | Dominated by | Mechanism |
|---|---|---|---|
| **Laplace** | $\int g(x)\,e^{\lambda\phi(x)}dx$, $\phi$ real | the **maximum** of $\phi$ | everything else is exponentially smaller |
| **Stationary phase** | $\int g(x)\,e^{i\lambda\phi(x)}dx$, $\phi$ real | points where $\phi'=0$ | everywhere else the phase spins and cancels |
| **Steepest descent** | $\int g(z)\,e^{\lambda\phi(z)}dz$, complex | saddle points of $\phi$ | deform the contour to pass through the saddle |

**Laplace's method.** With a single interior maximum at $x_0$, expand $\phi(x) \approx \phi(x_0) + \tfrac12\phi''(x_0)(x-x_0)^2$ and do the Gaussian:
$$\int g(x)e^{\lambda\phi(x)}dx \;\sim\; g(x_0)\,e^{\lambda\phi(x_0)}\sqrt{\frac{2\pi}{\lambda\,|\phi''(x_0)|}} \qquad (\lambda\to\infty)$$

The width of the contributing region is $\sim 1/\sqrt{\lambda|\phi''|}$ — the integral localizes, and that shrinking width is where the $\lambda^{-1/2}$ prefactor comes from. Stirling's formula is this method applied to $\Gamma(n+1) = \int_0^\infty t^n e^{-t}dt$.

**Stationary phase.** Nothing decays, so the argument is cancellation rather than smallness: away from a stationary point the phase runs fast, adjacent contributions arrive with opposite signs and cancel. Only where $\phi'(x_0)=0$ do neighbouring contributions add in step. The result carries a characteristic $\pm\pi/4$:
$$\int g(x)\,e^{i\lambda\phi(x)}dx \;\sim\; g(x_0)\,e^{i\lambda\phi(x_0)}\sqrt{\frac{2\pi}{\lambda|\phi''(x_0)|}}\;e^{\,i\,\mathrm{sgn}(\phi'')\pi/4}$$

Those $\pi/4$'s are not decoration — they are the Gouy phase, the Maslov index at a WKB turning point, and the $-\pi/4$ in the large-argument [[Bessel Functions|Bessel asymptotic]]. **When you meet an unexplained $\pi/4$, a stationary-phase evaluation happened somewhere upstream.**

**Steepest descent** unifies the two. Deform the contour (Cauchy permits it) to pass through a saddle $\phi'(z_0)=0$ along the direction where $\mathrm{Im}\,\phi$ is constant — so the integrand has *no* oscillation on the path and $\mathrm{Re}\,\phi$ falls off as fast as possible. On that contour the problem is Laplace's. The practical content:

- Which saddles the deformed contour actually crosses can change discontinuously with a parameter — **Stokes phenomenon**, and it is why asymptotic expansions swap form across Stokes lines ([[Asymptotic Series and Dominant Balance]]).
- Contour deformation is the same tool as [[Contour Integration and Residues]]; here you steer toward a saddle rather than enclose a pole.

**Degenerate stationary points.** If $\phi''(x_0)=0$ too, the Gaussian fails and the next term governs: $\phi'''\neq0$ gives an Airy function and a $\lambda^{-1/3}$ scaling instead of $\lambda^{-1/2}$. This is exactly the caustic case — a fold in the phase surface — which is why Airy functions describe both the WKB turning point and the intensity near a rainbow or a focus.

## Where it shows up

| Setting | The stationary point is | Yields |
|---|---|---|
| Fresnel/Kirchhoff diffraction | the ray path of stationary optical path length | **Fermat's principle**; geometric optics as the $\lambda\to0$ limit of wave optics ([[Diffraction]]) |
| Semiclassical QM | the classical trajectory | [[WKB Approximation]]; Bohr–Sommerfeld; classical paths as stationary action |
| Path integrals | the solution of the equations of motion | the classical limit; loops as fluctuations about it |
| Wave packet propagation | $\omega'(k) = x/t$ | **group velocity** — the packet arrives where the phase is stationary ([[Dispersion Relations]]) |
| Chirped signals / FM spectra | $d\phi/dt = \omega$ | the stationary-phase approximation for chirp spectra ([[Sideband Spectrum of Modulated Light]]) |
| Statistics | the mode of the log-likelihood | **Laplace approximation**; the Gaussian around the MLE ([[Maximum Likelihood Estimation]]) |
| Special-function asymptotics | the saddle of the integral representation | Stirling, Bessel, Airy large-argument forms |

The group-velocity row is the cleanest way to internalize the method: a wave packet is a superposition, and at position $x$ and time $t$ only the components whose phase $kx - \omega(k)t$ is stationary in $k$ survive — giving $x/t = d\omega/dk$ directly.

> [!question]- Why does a stationary-phase result carry a factor $e^{\pm i\pi/4}$ when a Laplace result does not?
> The Gaussian integral being done is $\int e^{i\lambda\phi'' u^2/2}du$ with an *imaginary* coefficient. Rotating the contour to make it a real Gaussian costs $\sqrt{i} = e^{i\pi/4}$, with the sign set by that of $\phi''$. Laplace's exponent is already real, so no rotation and no phase.

# Connections

- [[Asymptotic Series and Dominant Balance]] — the expansion this method generates the terms of
- [[WKB Approximation]] — the semiclassical case; turning points as degenerate stationary points
- [[Contour Integration and Residues]] — the deformation licence steepest descent relies on
- [[Bessel Functions]] — the $-\pi/4$ in the large-argument form, from exactly this
- [[Diffraction]] — Fermat's principle as stationary optical path length
- [[Dispersion Relations]] — group velocity as a stationary-phase condition
- [[Maximum Likelihood Estimation]] — the Laplace approximation around the mode
- [[Gaussian Distribution]] — the integral every one of these reduces to

---
Source: Bender & Orszag, *Advanced Mathematical Methods for Scientists and Engineers*, Ch. 6; Arfken & Weber, *Mathematical Methods for Physicists*, Ch. 12
