#statistics #math

**An interval built so that, over many repeated experiments, it contains the true value a stated fraction of the time** — the error bar is a statement about the *procedure's* hit rate, not a probability that the truth sits inside this one interval.

# Reference

Gaussian coverage dictionary:

| Interval | Coverage |
|---|---|
| $\pm 1\sigma$ | 68.3% |
| $\pm 1.96\sigma$ | 95% |
| $\pm 2\sigma$ | 95.4% |
| $\pm 3\sigma$ | 99.7% |

Physics quotes 1σ by default; much of the rest of science quotes 95% — check before comparing numbers across fields.

**From a fit: the $\Delta\chi^2$ rule.** The 1σ interval for *one* parameter is where $\chi^2$ rises by 1 from its minimum ($\Delta \ln L = -1/2$), *re-minimizing over all other parameters at each step* (the **profile**). Joint 68% region for two parameters: $\Delta\chi^2 = 2.30$, not 1 — the classic error-ellipse mistake. Bayesian alternative: **marginalize** (integrate the posterior over nuisance parameters); agrees with profiling for Gaussian likelihoods, diverges when they're skewed.

**Error-bar language:** $x = 1.234(5)$ means 1σ on the last digit(s); asymmetric intervals $x = 1.23^{+0.05}_{-0.02}$ signal a non-parabolic likelihood — don't symmetrize them. Near a physical boundary ($p \approx 0$, $n \geq 0$) naive $\pm\sigma$ leaks into forbidden territory; use exact constructions.

> [!question]- Two parameters from one fit: you want the 68% region for the pair. Why is $\Delta\chi^2 = 1$ wrong?
> $\Delta\chi^2 = 1$ gives 68% coverage per single parameter (its 1D projection). The joint 2D 68% contour requires $\Delta\chi^2 = 2.30$ (χ² with 2 dof). Using 1 undercovers — your ellipse is too small and both parameters look better-known than they are.

# Connections

- [[Least Squares and Chi-Squared Fitting]] — where the $\Delta\chi^2$ contours come from
- [[Bootstrap Resampling]] — intervals without analytic likelihoods
- [[Binomial Errors in State Detection]] — the boundary case ($p \to 0, 1$) where Gaussian intervals fail hard
- [[Error Propagation]] — carrying a 1σ interval through downstream analysis

---
Source: Particle Data Group, *Review of Particle Physics*, "Statistics" review section
