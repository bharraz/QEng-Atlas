#statistics #reference

**Map of the Statistics folder, and a refresher on the handful of things that are basic, constantly used, and constantly got wrong.**

# Reference

## The reminders

**Error bars.** Quote which one you mean — they answer different questions:

| Quantity | Formula | Answers |
|---|---|---|
| Standard deviation $\sigma$ | spread of the data | how scattered is a *single* measurement |
| **Standard error** $\sigma/\sqrt N$ | spread of the *mean* | how well do I know the average |
| Confidence interval | $\bar x \pm t\,\sigma/\sqrt N$ | a range with a stated coverage |

Averaging $N$ shots shrinks the error bar as $\sqrt N$, never faster, and only if the samples are independent and the variance is finite ([[Central Limit Theorem]], [[SNR and Averaging]]).

**The $\sqrt N$ fails in three named ways**, and every one of them shows up in the lab:

- **Correlated samples** — the effective count is $N_{\text{eff}} \ll N$; use the autocorrelation time to find it ([[Autocorrelation]]).
- **Heavy tails** — a Lorentzian has no variance, and the mean of $N$ samples is exactly as wide as one sample. Averaging does nothing.
- **Drift** — the thing you are averaging is not stationary, so more data gives bias, not precision ([[Allan Variance]]).

**Adding errors.** Independent contributions add **in quadrature**, $\sigma^2 = \sum\sigma_i^2$ — so the largest term dominates and improving anything else is wasted effort. Correlated ones do not; they add linearly and can cancel ([[Error Propagation]]).

**Counting experiments are Poisson**, so the error on $N$ counts is $\sqrt N$ and the fractional error is $1/\sqrt N$ ([[Poisson Distribution]], [[Shot Noise]]). A binary outcome measured $N$ times is binomial, with error $\sqrt{p(1-p)/N}$ — which vanishes as $p\to0$ or $1$, so near-perfect fidelities need special treatment ([[Binomial Errors in State Detection]]).

**Significant figures on an error bar:** one, or two if the leading digit is 1. Then round the value to match. Quoting `0.4271 ± 0.0836` claims precision the data does not contain.

**$\chi^2/\mathrm{dof}$ is the fit diagnostic.** Around 1 means the model and the error bars are mutually consistent; $\gg 1$ means a bad model *or* underestimated errors; $\ll 1$ means overestimated errors — which is just as wrong and much less often noticed ([[Least Squares and Chi-Squared Fitting]]).

**Correlation is not covariance is not independence.** Zero covariance does not imply independence except for Gaussians. Fit parameters are almost always correlated, and quoting their individual errors without the covariance matrix overstates what you know ([[Variance and Covariance]]).

## The folder

**Foundations**

| Page | For |
|---|---|
| [[PDF and CDF]] | densities vs. cumulatives; sampling and quantiles |
| [[Variance and Covariance]] | second moments, correlation, the covariance matrix |
| [[Central Limit Theorem]] | why Gaussians are everywhere, and the conditions that break it |
| [[Error Propagation]] | quadrature sums, the Jacobian rule, when it fails |

**Distributions you will meet**

| Page | Shows up as |
|---|---|
| [[Gaussian Distribution]] | almost everything, via the CLT |
| [[Poisson Distribution]] / [[Poisson Process]] | photon counts, arrivals, rare events |
| [[Binomial Distribution]] | yes/no outcomes over repeated shots |
| [[Exponential Distribution]] | waiting times, lifetimes, decay |

**Estimation and fitting**

| Page | For |
|---|---|
| [[Maximum Likelihood Estimation]] | the general estimator, and its error from the curvature |
| [[Least Squares and Chi-Squared Fitting]] | the Gaussian special case; goodness of fit |
| [[Confidence Intervals]] | what an interval claims |
| [[Bootstrap Resampling]] | error bars when the analytic route is hopeless |
| [[Fisher Information and the Cramér-Rao Bound]] | the floor no estimator beats |

**Noise: describing it**

| Page | For |
|---|---|
| [[Power Spectral Density]] | the units and conventions that trip everyone |
| [[Autocorrelation]] / [[Wiener-Khinchin Theorem]] | time domain ↔ frequency domain for noise |
| [[Allan Variance]] | which noise type dominates at which averaging time; where drift takes over |
| [[Noise Spectra and Coupling to Systems]] | converting a spectrum into a decoherence or heating rate |

**Noise: the physical sources**

[[Johnson-Nyquist Noise]] (thermal, resistive) · [[Shot Noise]] (counting, Poissonian) · [[Flicker Noise]] ($1/f$, from many two-state switchers) · [[SNR and Averaging]] (what averaging can and cannot fix)

**Simulation and inference**

| Page | For |
|---|---|
| [[Monte Carlo Methods]] | sampling-based estimates and their CLT error bars |
| [[Inverse Transform Sampling]] / [[Rejection Sampling]] / [[Box-Muller Transform]] | how to generate the samples |
| [[Recursive Bayesian Filtering]] | the general predict-update recursion |
| [[Kalman Filter]] | its linear-Gaussian special case |
| [[Particle Filter]] | its sampling-based general case |

> [!question]- You average 100 shots and the error bar drops by 10. You average 10,000 and it barely improves. What happened?
> The $\sqrt N$ gain has run out against something that does not average down — drift, or correlated samples. Plot the Allan deviation: white noise falls as $\tau^{-1/2}$ and drift turns it back upward, and the minimum is the optimal averaging time. Past that point, average less and interleave a reference measurement instead.

# Connections

- [[(Guide) Thinking Mathematically]] — necessary vs. sufficient, and the review battery for a result
- [[(Guide) Debugging Method]] — rule 2 needs statistics: a 1% failure rate needs counting, not anecdote
- [[Noise Spectra and Coupling to Systems]] — the bridge from a measured spectrum to a physical rate
- [[Optimization and Curve Fitting]] — the numerics behind the fitting pages
- [[Standard Quantum Limit and Spin Squeezing]] — where the $\sqrt N$ argument meets quantum limits

---
Source: Taylor, *An Introduction to Error Analysis*, Ch. 1–5; Barlow, *Statistics: A Guide to the Use of Statistical Methods in the Physical Sciences*
