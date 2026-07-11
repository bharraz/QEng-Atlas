#math

**Solve the equation once for a point source, then build every solution by superposition** — G is the system's response to a delta kick, and since the operator is linear, any source is just a weighted sum of kicks.

# Reference

For a linear operator $L$:
$$
L\, G(x, x') = \delta(x - x') \quad\Longrightarrow\quad y(x) = \int G(x, x')\, f(x')\, dx' \text{ solves } L y = f
$$
For time-invariant systems $G(t,t') = G(t-t')$ and the solution is a convolution; in frequency space it's just division: $\tilde{y}(\omega) = \tilde{f}(\omega)/L(\omega)$ — the Green's function *is* the transfer function.

**Driven damped oscillator** ($\ddot{x} + \gamma\dot{x} + \omega_0^2 x = f(t)$):
$$
G(t-t') = \frac{e^{-\gamma(t-t')/2}}{\omega_1}\sin\!\big(\omega_1 (t-t')\big)\,\Theta(t-t'), \qquad \omega_1 = \sqrt{\omega_0^2 - \gamma^2/4}
$$
— kick it, it rings and decays. The $\Theta$ enforces causality (retarded Green's function). In frequency space $\tilde{G}(\omega) = 1/(\omega_0^2 - \omega^2 + i\gamma\omega)$: the Lorentzian resonance is the FT of the ringdown.

**Poisson's equation:** $\nabla^2 G = -\delta^3(\mathbf{r}-\mathbf{r}')/\varepsilon_0$ gives $G = 1/4\pi\varepsilon_0|\mathbf{r}-\mathbf{r}'|$ — the Coulomb potential is the Green's function of electrostatics, and $V = \int \rho\, G\, dV'$ is just superposition of point charges.

**Boundary conditions matter:** G isn't unique until you impose them — retarded vs advanced in time, grounded-conductor vs free-space in electrostatics (method of images = constructing G for the boundary). Choose the G that matches your physical setup, not the formula you remember.

> [!question]- Why is the steady-state response to a sinusoidal drive completely determined by the free ringdown after a kick?
> They're a Fourier pair: $\tilde{G}(\omega)$ (the resonance curve you'd trace with a swept drive) is the FT of $G(t)$ (the decaying ring after an impulse). Measuring one is measuring the other — ringdown and swept-sine spectroscopy give identical information.

# Connections

- [[Dirac Delta]] — the source that defines G
- [[Driven Damped Harmonic Oscillator]] — the canonical example, ringdown ↔ Lorentzian
- [[Convolution]] — the superposition integral is a convolution for time-invariant L
- [[Method of Images]] — image charges are Green's-function construction for boundaries
- [[Electrostatic Potential and Poisson Equation]] — Coulomb's law as the Green's function of ∇²

---
Source: Arfken & Weber, *Mathematical Methods for Physicists*, Ch. 10
