#statistics #math

**The pdf is probability per unit x; the CDF is accumulated probability — differentiate one to get the other.** Every expectation value, variable transformation, and sampling trick is built from these two objects.

# Reference

$$
F(x) = P(X\le x) = \int_{-\infty}^{x} f(x')\,dx', \qquad f(x) = \frac{dF}{dx}
$$

$F$ runs monotonically 0→1 and is dimensionless; $f$ carries units of $1/[x]$ (a pdf over frequency is per Hz — forget this and normalizations break).

**Expectation values:**
$$
\langle g(X)\rangle = \int g(x)\,f(x)\,dx, \qquad \mathrm{Var}(X) = \langle X^2\rangle - \langle X\rangle^2
$$

**Change of variables — the one that bites.** For monotonic $y(x)$:
$$
f_Y(y) = f_X(x)\left|\frac{dx}{dy}\right|
$$
Probability $f\,dx$ is invariant; *density* is not — it transforms with the Jacobian. This is why distributions develop integrable peaks wherever $dy/dx = 0$: samples pile up at turning points.

> [!question]- A uniformly random phase θ produces a signal y = cos θ. Why does the histogram of y pile up at ±1?
> $f_Y(y) = \frac{1}{\pi\sqrt{1-y^2}}$ — the Jacobian $|d\theta/dy|$ diverges where $dy/d\theta = 0$, i.e. at the turning points. (The arcsine distribution; same reason fringe-scan histograms peak at the extremes.)

# Connections

- [[Inverse Transform Sampling]] — runs $F^{-1}$ backwards to manufacture samples
- [[Variance and Covariance]] — the moments defined by these integrals
- [[Gaussian Distribution]] — the pdf you write most; its CDF (erf) has no closed inverse

---
Source: Bevington & Robinson, *Data Reduction and Error Analysis*, Ch. 1–2
