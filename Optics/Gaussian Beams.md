#optics

**One complex number $q(z) = z + iz_R$ carries the whole beam** — real part is distance from the waist, imaginary part the Rayleigh range, and spot size + wavefront curvature both fall out of $1/q$.

# Reference

$$
\frac{1}{q(z)} = \frac{1}{R(z)} - \frac{i\lambda}{\pi w^2(z)}
$$

With waist $w_0$ at $z=0$ and Rayleigh range $z_R = \pi w_0^2/\lambda$ (distance to $\sqrt{2}$-larger spot):

$$
w(z) = w_0\sqrt{1 + (z/z_R)^2}, \qquad R(z) = z\left[1 + (z_R/z)^2\right]
$$

$R$ is flat at the waist, tightest at $z = z_R$, then approaches $R \to z$ (spherical wave from the waist). Far-field half-angle divergence:

$$
\theta = \frac{\lambda}{\pi w_0}
$$

**Waist–divergence tradeoff: $w_0\theta = \lambda/\pi$ is invariant.** Tight focus buys you a short depth of focus $2z_R \propto w_0^2$ — halve the waist, quarter the working range. Numbers at $\lambda = 1\,\mu$m: $w_0 = 1$ mm gives $z_R \approx 3.1$ m, $\theta \approx 0.32$ mrad; $w_0 = 10\,\mu$m gives $z_R \approx 0.31$ mm.

**Intensity:** $I(r) = \frac{2P}{\pi w^2}e^{-2r^2/w^2}$ — note the 2: peak intensity is *twice* the naive $P/\pi w^2$. $w$ is the $1/e^2$ intensity radius.

**Gouy phase** $\psi(z) = \arctan(z/z_R)$: an extra $\pi$ of phase slip through the focus relative to a plane wave — this is why cavity transverse modes are frequency-split.

**Propagation through optics:** $q' = (Aq+B)/(Cq+D)$ with the same ABCD matrices as ray optics. Focusing a collimated beam of radius $w$ with a lens $f$: new waist $w_0' \approx \lambda f/\pi w$.

> [!question]- You need a 2× smaller focused spot from the same lens. What do you change, and what does it cost?
> Expand the input beam 2× before the lens ($w_0' \approx \lambda f/\pi w$). Cost: depth of focus drops 4×, since $z_R \propto w_0^2$ — alignment along the axis gets four times touchier.

# Connections

- [[Ray Transfer Matrices]] — the ABCD formalism that transforms $q$ through any paraxial system
- [[Mode Matching]] — overlapping your $q$ with a target mode (fiber, cavity) is the whole game
- [[Higher-Order Beam Modes]] — the TEM$_{00}$ described here is the ground state of a complete family
- [[Optical Cavity Stability]] — a cavity's eigenmode is the Gaussian whose $q$ reproduces itself per round trip
- [[Beam Quality M2]] — real beams diverge $M^2$ times faster than this ideal

---
Source: Siegman, *Lasers*, Ch. 17
