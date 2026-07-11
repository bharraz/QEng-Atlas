#statistics #math

**Fake new datasets by resampling your real one with replacement, redo the analysis on each, and read the error bar off the spread** — the data stands in for the unknown distribution, and the computer replaces the propagation algebra.

# Reference

Algorithm, for any estimator $\hat\theta$ (median, fit parameter, whole pipeline):

1. Draw $N$ points **with replacement** from your $N$ data points (duplicates expected — each draw omits ~37% of points).
2. Compute $\hat\theta^*_b$ on the resample.
3. Repeat $B \sim 10^3$ times.
4. $\sigma_{\hat\theta} = \mathrm{std}(\hat\theta^*_1, \ldots, \hat\theta^*_B)$; percentiles of the $\hat\theta^*$ histogram give asymmetric intervals.

**When to reach for it:** analytic error propagation is hopeless or dishonest — medians and quantiles, estimators with correlations you can't write down, multi-stage pipelines (calibrate → filter → fit → extract), or checking that a fitter's quoted errors are real.

**Parametric variant:** generate synthetic datasets from the *fitted model* + noise model instead of resampling data — better for small $N$, and doubles as a fit-bias check (does $\langle\hat\theta^*\rangle$ come back shifted from the input?).

**Caveats:** correlated data breaks the iid assumption — resample *blocks* longer than the correlation time, or whole repetitions instead of single shots. Fails for extreme-value statistics (max, support edges). Small $N$: the resamples only know about values you actually saw.

> [!question]- Time-series data with correlation time $\tau_c$: why does the naive bootstrap lie, and in which direction?
> Resampling single points treats correlated samples as independent, so each resample is too diverse in information content — err, effectively overcounts $N$. The spread of $\hat\theta^*$ underestimates the true error (same $N$ vs $N_{\text{eff}}$ sin as naive $\sqrt{N}$ bars). Fix: block bootstrap with blocks $\gg \tau_c$.

# Connections

- [[Monte Carlo Methods]] — the bootstrap is MC with the empirical distribution as the sampler
- [[Confidence Intervals]] — percentile intervals when the likelihood is unavailable or skewed
- [[Autocorrelation]] — dictates the block size for correlated data
- [[Maximum Likelihood Estimation]] — bootstrap validates (or exposes) its asymptotic error formulas at finite $N$

---
Source: Efron & Tibshirani, *An Introduction to the Bootstrap*, Ch. 6
