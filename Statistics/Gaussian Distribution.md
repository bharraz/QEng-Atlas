#statistics #math

**The distribution everything converges to** — average enough independent anythings and you get a Gaussian, which is why error bars, fit residuals, and averaged noise all end up looking like it.

# Reference

$$
f(x) = \frac{1}{\sigma\sqrt{2\pi}}\, e^{-(x-\mu)^2/2\sigma^2}
$$

with mean $\mu$ and variance $\sigma^2$ — a Gaussian is fully specified by two numbers; all higher cumulants vanish.

**The lookup numbers:**

| quantity | value |
|---|---|
| FWHM | $2\sqrt{2\ln 2}\,\sigma \approx 2.355\,\sigma$ |
| within $\pm 1\sigma,\ 2\sigma,\ 3\sigma$ | 68.3%, 95.4%, 99.7% |
| height at $\pm\sigma$ | $e^{-1/2}\approx 0.61$ of peak |

**Sums stay Gaussian:** independent $X_i \sim \mathcal N(\mu_i,\sigma_i^2)$ give $\sum X_i \sim \mathcal N(\sum\mu_i,\ \sum\sigma_i^2)$ — variances add, never widths. Convolving two Gaussians: widths add in quadrature (instrument response × lineshape).

**Why it's everywhere:** [[Central Limit Theorem]] — noise that is a sum of many small independent contributions comes out Gaussian regardless of the microscopic distributions. This is also what licenses χ² fitting: least squares is maximum likelihood *only* for Gaussian errors.

> [!question]- A Gaussian line has FWHM 10 MHz. What's σ, and what fraction of the area lies within ±FWHM/2?
> $\sigma = 10/2.355 \approx 4.25$ MHz; ±FWHM/2 is ±1.18σ, which holds about 76% of the area.

# Connections

- [[Central Limit Theorem]] — the reason this distribution is the default, not a choice
- [[Least Squares and Chi-Squared Fitting]] — χ² is maximum likelihood *assuming* Gaussian errors
- [[Box-Muller Transform]] — how to sample it, since the CDF (erf) has no closed inverse
- [[Error Propagation]] — linearized propagation implicitly keeps everything Gaussian

---
Source: Bevington & Robinson, *Data Reduction and Error Analysis*, Ch. 2
