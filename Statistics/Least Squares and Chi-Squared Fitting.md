#statistics #math

**Minimize the error-weighted squared residuals** — each point pulls on the fit with strength $1/\sigma_i^2$, and the minimum value itself tells you whether the model and your error bars are honest.

# Reference

$$
\chi^2(\theta) = \sum_i \frac{\left(y_i - f(x_i;\theta)\right)^2}{\sigma_i^2}
$$

**The goodness check:** at the minimum, $\chi^2_\nu = \chi^2/(N - p) \approx 1 \pm \sqrt{2/(N-p)}$ if model and errors are right.
- $\chi^2_\nu \gg 1$: wrong model, or $\sigma_i$ underestimated (unmodeled systematics).
- $\chi^2_\nu \ll 1$: $\sigma_i$ overestimated — or you're overfitting.
- Never quote parameter errors from a fit with bad $\chi^2_\nu$ without saying so (common bodge: scale errors by $\sqrt{\chi^2_\nu}$, which assumes the excess is just mis-set error bars).

**Parameter errors from curvature:** covariance matrix $C = H^{-1}$ where $H_{jk} = \tfrac{1}{2}\,\partial^2\chi^2/\partial\theta_j\partial\theta_k$; for linear-in-parameters models with Jacobian $J$, $C = (J^{\mathsf T} W J)^{-1}$, $W = \mathrm{diag}(1/\sigma_i^2)$. Then $\sigma_{\theta_j} = \sqrt{C_{jj}}$, off-diagonals = parameter trade-offs, and $\Delta\chi^2 = 1$ marks the 1σ boundary.

**Always plot residuals** $(y_i - f_i)/\sigma_i$: structure (waves, trends, one end blowing up) means wrong model even when $\chi^2_\nu$ looks tolerable — it's the single highest-value diagnostic per second spent.

> [!question]- Fit converges, parameters look fine, $\chi^2_\nu = 4$. What do you do before quoting errors?
> Look at residuals: coherent structure ⇒ wrong/incomplete model — fix the model, errors from this fit are meaningless. White-looking residuals ⇒ your $\sigma_i$ are ~2× too small; rescale (multiply parameter errors by $\sqrt{\chi^2_\nu} = 2$) and find out why.

# Connections

- [[Maximum Likelihood Estimation]] — χ² is MLE for Gaussian errors; switch to likelihood for counts
- [[Confidence Intervals]] — the $\Delta\chi^2$ rules for turning curvature into quotable errors
- [[Variance and Covariance]] — the returned covariance matrix and what its off-diagonals mean
- [[Condition Number]] — ill-conditioned $J^{\mathsf T}J$ = degenerate parameters, absurd errors
- [[Pseudo-Inverse]] — the SVD route to linear least squares when it's degenerate anyway

---
Source: Bevington & Robinson, *Data Reduction and Error Analysis for the Physical Sciences* 3rd ed., Ch. 8
