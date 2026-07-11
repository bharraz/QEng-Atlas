#numerics #math #statistics

**Fitting and optimization are the same activity — minimize a scalar objective over parameters — and the practical hierarchy is: use derivative structure if you have it (Newton-family), exploit least-squares structure if the objective is a sum of squared residuals (Levenberg–Marquardt), and only fall back to derivative-free or global methods when the landscape forces you.** Most "the fit won't converge" problems are starting-point, scaling, or parametrization problems, not algorithm problems.

# Reference

## The local-method hierarchy

All Newton-family methods model the objective locally as a quadratic and jump toward its minimum:

$$\mathbf{x}_{k+1} = \mathbf{x}_k - H^{-1}\nabla f,$$

- **Newton**: use the true Hessian $H$ — quadratic convergence (digits *double* per iteration) near the minimum, but needs second derivatives and $H$ may not be positive definite far away.
- **Quasi-Newton (BFGS/L-BFGS)**: build up a Hessian estimate from successive gradients — the default for smooth problems with many parameters ('L-' for when even storing $H$ is too much).
- **Gradient descent**: $H \to \mathbb{1}/\alpha$; only the gradient direction survives. Robust and cheap per step but crawls through curved valleys (its zigzag rate is governed by the Hessian's [[Condition Number|condition number]]). Its stochastic variant (SGD/Adam) rules machine learning because *noisy* gradients over huge datasets are cheap, not because it converges fast.
- **Derivative-free** (Nelder–Mead simplex, Powell): when the objective is noisy or gradients don't exist (e.g. the objective *is an experiment* — but then prefer Bayesian optimization, which models the function with a Gaussian process and spends few evaluations wisely; that's what optimizing gate parameters against measured fidelity wants).

Gradients: analytic if feasible; otherwise automatic differentiation (JAX/PyTorch — exact, cheap) beats finite differences, which lose half your digits ([[Floating Point and Numerical Error|cancellation]]) and cost one function call per parameter.

## Least squares — the structure fitting has

Fitting data means minimizing $\chi^2(\boldsymbol\theta) = \sum_i r_i^2$, $r_i = [y_i - m(x_i;\boldsymbol\theta)]/\sigma_i$. The special structure: the Hessian is approximately $J^\top J$ (Jacobian of residuals only — *first* derivatives give you an approximate *second*-derivative method for free). Gauss–Newton exploits it; **Levenberg–Marquardt** (`curve_fit`, `lsqcurvefit`) adds an adaptive damping $\lambda$:

$$(J^\top J + \lambda\,\mathbb{1})\,\delta\boldsymbol\theta = J^\top \mathbf{r},$$

interpolating between Gauss–Newton ($\lambda \to 0$, fast near the answer) and small-step gradient descent ($\lambda$ large, safe far away). This is the right default for every nonlinear curve fit.

**The parts that actually fail, and their fixes:**

- **Linear vs nonlinear parameters.** If the model is linear in some parameters (amplitudes, offsets: $A e^{-t/\tau} + C$ is linear in $A, C$), those have a *closed-form* optimum for any fixed nonlinear parameters — solve them by linear least squares inside the loop (variable projection) or at minimum give the nonlinear solver good starting values from the linear solve. Purely linear fits (polynomials, sums of fixed functions) need no iteration at all: one QR/[[Singular Value Decomposition|SVD]] solve — and never via the normal equations, which square the condition number.
- **Starting values.** Nonlinear fitting converges to the *nearest* local minimum. Get initial frequencies from an FFT, initial rates from log-slopes, initial centers from peak-finding — thirty seconds of estimation beats any amount of solver tuning. Sinusoid fitting without an FFT-seeded frequency is the classic self-inflicted failure (the $\chi^2$ landscape in frequency oscillates!).
- **Scaling and parametrization.** Parameters differing by 10⁶ in magnitude wreck the geometry (see conditioning) — rescale to $O(1)$, fit $\log\tau$ instead of $\tau$ when it's positive and spans decades (also enforces positivity for free). Strongly correlated parameters (e.g. amplitude and offset with data that doesn't reach the baseline) show up as a nearly singular $J^\top J$: the fit "won't converge" because the data genuinely doesn't constrain a direction — fix the model or the data, not the tolerance.
- **Errors on parameters.** The covariance is $C \approx (J^\top J)^{-1}$ *at the solution*, valid if residuals are Gaussian and the model is locally linear; `curve_fit` returns it (beware `absolute_sigma`: without per-point $\sigma_i$ it rescales by residual variance). Trust intervals from profile likelihood or [[Bootstrap Resampling|bootstrap]] when parameters are near bounds or strongly correlated. Check the fit itself with reduced $\chi^2 \approx 1$ and — more sensitively — *structure in the residuals*: a good fit's residuals are white (see [[Autocorrelation]]).

## Global and constrained

Local methods + multistart (many random/gridded starting points, keep the best) solves most "global" problems in low dimension honestly. True global heuristics — simulated annealing, differential evolution, basin-hopping, CMA-ES — trade guarantees for landscape coverage; use them when multistart keeps finding different minima. Constraints: bounds are cheap (most libraries take them natively — use them, they prevent wandering into unphysical territory); general constraints → SLSQP/interior-point; but a reparametrization that *eliminates* the constraint ($\theta = e^\phi$ for positivity, softmax for weights summing to 1) is usually more robust than constraint machinery.

> [!question]- Your five-parameter fit converges but two parameter errors come back as ±10⁶. What is the fit telling you?
> $(J^\top J)^{-1}$ has a huge eigenvalue: some combination of those two parameters is unconstrained by the data — the model is locally *degenerate* along that direction (classic pairs: amplitude × exponential-rate when the decay barely starts within the data window; frequency and phase with few oscillations). The answer is never "tighten tolerances." Either fix one parameter from other knowledge, reparametrize to the combination the data *does* constrain (e.g. fit $A\tau$ instead of $A$ and $\tau$), or take data where the degeneracy breaks. The covariance matrix told you which experiment to do next.

# Connections

- [[Floating Point and Numerical Error]] — conditioning and cancellation under everything here
- [[Singular Value Decomposition]] — linear least squares done stably; diagnosing degenerate directions
- [[Condition Number]] — why gradient descent zigzags and normal equations hurt
- [[Bootstrap Resampling]] — parameter errors when the Gaussian approximation is dubious
- [[Autocorrelation]] — residual whiteness as the sharp goodness-of-fit test
- [[FFT in Practice]] — the standard source of starting frequencies

---
Source: Nocedal & Wright, *Numerical Optimization*, Ch. 3, 6, 10; Press et al., *Numerical Recipes*, Ch. 15; Transtrum & Sethna, arXiv:1201.5885 (sloppy models and LM practice)
