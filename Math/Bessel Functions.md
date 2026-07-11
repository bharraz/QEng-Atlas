#math

**What sines and cosines become when the geometry is cylindrical** — separate the Laplacian in cylindrical coordinates and the radial equation is Bessel's; $J_n$ is the oscillation that stays finite on the axis. Also, entirely separately, the sideband amplitudes of any phase-modulated signal.

# Reference

**Bessel's equation** (from $\nabla^2$ in cylindrical coordinates, radial part):
$$
x^2 y'' + x y' + (x^2 - n^2)\, y = 0 \qquad \Rightarrow \qquad y = J_n(x) \text{ (regular)}, \; Y_n(x) \text{ (blows up at 0)}
$$
Keep $Y_n$ only for annular domains (coax, ring). Modified Bessel $I_n, K_n$ (equation with $-x^2$) are the exponential-like versions — evanescent radial behavior.

**Behavior of $J_n$:** near zero $J_n(x) \approx \frac{1}{n!}(x/2)^n$ — only $J_0$ is nonzero on axis. Large $x$: decaying oscillation,
$$
J_n(x) \approx \sqrt{\frac{2}{\pi x}}\,\cos\!\left(x - \frac{n\pi}{2} - \frac{\pi}{4}\right)
$$
Zeros are unevenly spaced (first few of $J_0$: 2.405, 5.520, 8.654; of $J_1$: 3.832, 7.016). Boundary condition $J_n(k a) = 0$ quantizes $k$ — drumhead modes, fiber modes, cylindrical cavity modes all indexed by these zeros.

**FM/phase-modulation sidebands** — the Jacobi–Anger identity:
$$
e^{i\beta\sin\omega t} = \sum_{n=-\infty}^{\infty} J_n(\beta)\, e^{in\omega t}
$$
A phase-modulated carrier with modulation depth $\beta$ carries sidebands at $\pm n\omega$ with amplitudes $J_n(\beta)$. Small $\beta$: carrier $J_0 \approx 1 - \beta^2/4$, first sidebands $J_1 \approx \beta/2$. **Carrier nulls at $\beta = 2.405$** (first zero of $J_0$) — the standard EOM calibration: crank modulation depth until the carrier vanishes on the spectrum analyzer, and you know $\beta$ exactly. Power conservation: $\sum J_n^2(\beta) = 1$.

> [!question]- How do you calibrate an EOM's modulation depth with nothing but a spectrum analyzer?
> Increase drive until the carrier disappears — that's $J_0(\beta) = 0$, so $\beta = 2.405$ exactly. Ratios like $J_1^2/J_0^2$ between sideband and carrier powers give $\beta$ at intermediate settings.

# Connections

- [[Electro-Optic Modulator]] — J_n(β) sideband amplitudes in the lab
- [[Curvilinear Coordinates]] — the cylindrical Laplacian these solve
- [[Sideband Spectrum of Modulated Light]] — reading J_n structure off a heterodyne spectrum
- [[Sturm-Liouville Theory]] — orthogonality with weight x, completeness on [0,a]
- [[Separation of Variables]] — the step that produces Bessel's equation

---
Source: Boas, *Mathematical Methods in the Physical Sciences*, Ch. 12 §12–20
