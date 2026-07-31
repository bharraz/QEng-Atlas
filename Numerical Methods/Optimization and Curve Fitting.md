#numerics #math #statistics

**Fitting and optimization are one activity — minimize a scalar objective over parameters. Use derivatives if available (Newton family), exploit sum-of-squares structure if fitting (Levenberg–Marquardt), fall back to derivative-free only when forced.** Most "the fit won't converge" problems are starting-point, scaling, or degeneracy problems, not algorithm problems.

# Reference

## Local methods

All Newton-family steps minimize a local quadratic model:

$$\mathbf{x}_{k+1} = \mathbf{x}_k - H^{-1}\nabla f, \qquad H = \text{Hessian (curvature), } \nabla f = \text{gradient}.$$

| method | $H$ | convergence | use when |
|---|---|---|---|
| Newton | exact | quadratic (digits double/iter) | Hessian cheap, near minimum |
| BFGS / L-BFGS | built from gradient history | superlinear | smooth, many parameters (the default) |
| gradient descent | $\mathbb{1}/\alpha$ | linear, rate set by $\kappa(H)$ ([[Condition Number]]) — zigzags in curved valleys | only its stochastic variant (SGD/Adam) earns use: cheap noisy gradients over huge datasets |
| Nelder–Mead / Powell | none | slow | no gradients, noisy objective |
| Bayesian optimization | Gaussian-process surrogate | sample-efficient | objective is an experiment (gate parameters vs measured fidelity) |

Gradients: analytic > automatic differentiation (exact, cheap) > finite differences (half your digits to [[Floating Point and Numerical Error|cancellation]], one call per parameter).

## Least squares

Fitting minimizes $\chi^2(\boldsymbol\theta) = \sum_i r_i^2$, $r_i = [y_i - m(x_i;\boldsymbol\theta)]/\sigma_i$ (residuals weighted by measurement error). The structure: $H \approx J^\top J$ with $J_{i\mu} = \partial r_i/\partial\theta_\mu$ — first derivatives yield an approximate second-derivative method. **Levenberg–Marquardt** (`curve_fit`) damps it adaptively:

$$(J^\top J + \lambda\,\mathbb{1})\,\delta\boldsymbol\theta = -J^\top \mathbf{r}$$

— $\lambda \to 0$: Gauss–Newton (fast near the answer); $\lambda$ large: short gradient step (safe far away). The right default for every nonlinear fit.

**Why fits fail:**

- **Starting values.** Convergence is to the *nearest* minimum. Seed frequencies from an FFT (the $\chi^2$ landscape in frequency oscillates — unseeded sinusoid fits are self-inflicted), rates from log-slopes, centers from peak-finding.
- **Linear parameters** (amplitudes, offsets: $Ae^{-t/\tau} + C$ is linear in $A, C$) have closed-form optima at fixed nonlinear parameters — solve them by linear least squares (variable projection) or at least seed from it. Fully linear models need no iteration: one QR/[[Singular Value Decomposition|SVD]] solve, never the normal equations ($\kappa$ squared).
- **Scaling.** Parameters spanning decades wreck the quadratic model's geometry: rescale to $O(1)$; fit $\log\tau$ for positive scale parameters (positivity free).
- **Degeneracy.** Data not constraining a parameter combination → $J^\top J$ nearly singular → "won't converge" at any tolerance. The covariance says which combination (below).

**Errors and goodness of fit:**

$$C \approx (J^\top J)^{-1} \;\;(\text{at the solution: parameter covariance, valid for Gaussian residuals/local linearity}).$$

Mind `absolute_sigma` in `curve_fit` (without per-point $\sigma_i$ it rescales by residual variance). Near-degenerate or bounded parameters → profile likelihood or [[Bootstrap Resampling|bootstrap]]. Check reduced $\chi^2 \approx 1$, and — more sensitive — residual whiteness ([[Autocorrelation]]): structure in residuals means a wrong model with a good $\chi^2$.

## Global and constrained

Multistart (many seeds, keep the best) is the honest global method in low dimension; heuristics (differential evolution, basin-hopping, CMA-ES, annealing) when multistart keeps finding new minima. Bounds: cheap, use them. General constraints: SLSQP/interior-point — but a reparametrization eliminating the constraint ($\theta = e^\phi$ for positivity, softmax for simplex weights) is usually more robust.

> [!question]- A five-parameter fit converges but two errors come back ±10⁶. What is it saying?
> $(J^\top J)^{-1}$ has a huge eigenvalue: the data leave one combination of those parameters unconstrained — locally degenerate (classic pairs: amplitude × rate when the decay barely starts in the data window; frequency × phase with few oscillations). Never "tighten tolerances": fix one parameter from prior knowledge, reparametrize to the combination the data does constrain (fit $A\tau$, not $A$ and $\tau$), or take data where the degeneracy breaks. The covariance matrix has named the next measurement.

# Connections

- [[Floating Point and Numerical Error]] — conditioning and cancellation underneath
- [[Singular Value Decomposition]] — stable linear least squares; diagnosing degenerate directions
- [[Condition Number]] — gradient-descent zigzag; normal-equation damage
- [[Bootstrap Resampling]] — errors when the Gaussian approximation fails
- [[Autocorrelation]] — residual whiteness as the sharp test
- [[Least Squares and Chi-Squared Fitting]] — the statistics of the objective
- [[FFT in Practice]] — the standard seed for frequencies

---
Source: Nocedal & Wright, *Numerical Optimization*, Ch. 3, 6, 10; Press et al., *Numerical Recipes*, Ch. 15
