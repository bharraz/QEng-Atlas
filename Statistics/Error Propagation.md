#statistics #math

**Linearize $f$ about the measured values and add the resulting error contributions in quadrature** — each input's uncertainty enters through its slope $\partial f/\partial x_i$, and independent errors add like orthogonal vectors.

# Reference

$$
\sigma_f^2 = \sum_i \left(\frac{\partial f}{\partial x_i}\right)^{\!2}\sigma_i^2 \;+\; 2\sum_{i<j}\frac{\partial f}{\partial x_i}\frac{\partial f}{\partial x_j}\,\mathrm{Cov}(x_i, x_j)
$$

Each partial derivative is the *sensitivity* — units of $f$ per unit of $x_i$ — so the product $(\partial f/\partial x_i)\sigma_i$ is an error contribution already in the units of $f$, and the sum is a Pythagorean addition of those contributions. Reading it as a sensitivity budget is the useful move: compute each term separately and the dominant one names the measurement worth improving; halving an error that contributes 30% of the quadrature sum changes almost nothing.

Drop the covariance term only if inputs are actually independent — shared calibration constants make them not.

**The quick table** (independent inputs):

| $f$ | rule |
|---|---|
| $ax \pm by$ | $\sigma_f^2 = a^2\sigma_x^2 + b^2\sigma_y^2$ (absolute, quadrature) |
| $xy$ or $x/y$ | $(\sigma_f/f)^2 = (\sigma_x/x)^2 + (\sigma_y/y)^2$ (relative, quadrature) |
| $x^n$ | $\sigma_f/f = \|n\|\,\sigma_x/x$ |
| $\ln x$ | $\sigma_f = \sigma_x/x$ |
| $e^{ax}$ | $\sigma_f/f = \|a\|\,\sigma_x$ |

**When linearization fails:** $\sigma_x$ large enough that $f$ curves across it (second-derivative term competes), or at a stationary point $\partial f/\partial x = 0$ where the formula predicts $\sigma_f = 0$ — falsely. Then propagate numerically: sample the inputs, push through $f$, histogram the output ([[Monte Carlo Methods]]).

> [!question]- Two measurements share the same calibration factor. What does naive quadrature do to the error of their ratio?
> Overestimates it — the calibration error is common-mode and cancels in the ratio, which is exactly what the (negative-covariance) cross term encodes. Ignoring covariance isn't conservative in general; it can err in either direction.

# Connections

- [[Variance and Covariance]] — the machinery underneath; the formula is just $\mathrm{Var}(\nabla f \cdot \mathbf{x})$
- [[Confidence Intervals]] — turning the propagated $\sigma_f$ into a quotable interval
- [[Central Limit Theorem]] — why quadrature-summed errors end up Gaussian
- [[Monte Carlo Methods]] — the numerical fallback when derivatives or linearity fail

---
Source: Taylor, *An Introduction to Error Analysis* 2nd ed., Ch. 3
