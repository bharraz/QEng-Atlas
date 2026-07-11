#math

**Close the contour in the complex plane and a hard real integral becomes bookkeeping: $2\pi i$ times the residues you enclose.** The integrand's poles carry all the information; the arc you add contributes nothing if you close on the side where the integrand dies.

# Reference

$$
\oint_C f(z)\,dz = 2\pi i \sum_{\text{poles inside}} \mathrm{Res}\,f, \qquad \mathrm{Res}_{z_0} f = \lim_{z\to z_0}(z-z_0)f(z) \;\text{(simple pole)}
$$

For a pole of order $n$: $\frac{1}{(n-1)!}\lim_{z\to z_0}\frac{d^{n-1}}{dz^{n-1}}\left[(z-z_0)^n f(z)\right]$. For $p(z)/q(z)$ with simple zero of $q$: residue $= p(z_0)/q'(z_0)$ — the workhorse form.

**Closing contours:** for $\int_{-\infty}^{\infty} f(x)e^{i\omega x}dx$, close where the exponential decays — upper half-plane for $\omega>0$, lower for $\omega<0$. **Jordan's lemma** guarantees the arc vanishes as long as $f\to 0$ on it, even slowly (~$1/|z|$).

**The Lorentzian example** (memorize the mechanics):
$$
\int_{-\infty}^{\infty}\frac{dx}{x^2+\gamma^2} = 2\pi i \cdot \mathrm{Res}_{i\gamma}\frac{1}{(x-i\gamma)(x+i\gamma)} = 2\pi i\cdot\frac{1}{2i\gamma} = \frac{\pi}{\gamma}
$$
Same machinery shows the FT of $e^{-\gamma|t|}$ is a Lorentzian — decay ↔ linewidth in one contour.

**Causality connection:** a response function analytic in the upper half-plane (no poles = no response before the kick) lets you run a contour around the real axis and relate its real and imaginary parts — that is exactly [[Kramers-Kronig Relations]]. Pole placement ($\omega\to\omega\pm i\epsilon$) is also how retarded vs advanced Green's functions get chosen.

> [!question]- You need $\int_{-\infty}^{\infty} f(x)e^{i\omega x}dx$ with $\omega<0$. Which way do you close, and what if the pole is in the other half-plane?
> Close in the lower half-plane, where $e^{i\omega z}$ decays (mind the extra minus sign from clockwise orientation). If the enclosed region has no poles, the integral is zero — that's not a failure, that's causality showing up as "no response at negative time."

# Connections

- [[Kramers-Kronig Relations]] — analyticity from causality + this contour machinery = absorption↔dispersion
- [[Fourier Transform]] — most inverse FTs in physics are evaluated by closing a contour
- [[Green's Functions]] — the $\pm i\epsilon$ pole shift selects retarded vs advanced solutions
- [[Driven Damped Harmonic Oscillator]] — its Lorentzian response is the residue calculation above, live

---
Source: Arfken & Weber, *Mathematical Methods for Physicists*, Ch. 11 (Residue theorem and applications)
