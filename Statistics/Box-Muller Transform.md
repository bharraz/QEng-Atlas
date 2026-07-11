#statistics #math

**Two uniforms in, two independent Gaussians out** — the 1D Gaussian CDF won't invert, but in 2D the radial part becomes an exponential, which does. The polar dodge for the missing $\mathrm{erf}^{-1}$.

# Reference

$$
z_1 = \sqrt{-2\ln u_1}\,\cos(2\pi u_2), \qquad z_2 = \sqrt{-2\ln u_1}\,\sin(2\pi u_2)
$$

with $u_1, u_2 \sim \mathrm{Uniform}(0,1)$ independent; $z_1, z_2$ are independent standard normals. Scale to $\mu + \sigma z$ as needed.

**Why it works:** a 2D isotropic Gaussian in polar coordinates factorizes — the extra Jacobian $r$ makes $r^2/2 \sim \mathrm{Exponential}(1)$, so $r = \sqrt{-2\ln u_1}$ by [[Inverse Transform Sampling]], and $\theta = 2\pi u_2$ is trivially uniform. The angle supplies the second, independent Gaussian for free.

**Marsaglia polar variant:** draw $(v_1, v_2)$ uniform in the unit disk (reject outside), use $s = v_1^2+v_2^2$; $z_i = v_i\sqrt{-2\ln s / s}$ — same math, no trig calls.

> [!question]- Why go to 2D at all?
> $\int e^{-x^2/2}dx$ has no closed form, but $\int e^{-r^2/2}\,r\,dr$ does — the polar Jacobian $r$ is exactly the factor that makes the radial CDF invertible. Same trick that evaluates the Gaussian integral itself.

# Connections

- [[Gaussian Distribution]] — what this generates; the anchor for every noise simulation
- [[Inverse Transform Sampling]] — Box-Muller is inverse transform applied to $(r, \theta)$ instead of $x$
- [[Monte Carlo Methods]] — Gaussian draws are the raw material of most physics MC (noise realizations, error budgets)

---
Source: Devroye, *Non-Uniform Random Variate Generation*, Ch. 5 (free online)
