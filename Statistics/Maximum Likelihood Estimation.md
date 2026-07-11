#statistics #math

**Pick the parameters that make your actual data most probable** — maximize $L(\theta) = \prod_i p(x_i|\theta)$. Least squares is just the special case where every $p$ is Gaussian; MLE is what you fall back on when it isn't.

# Reference

$$
\ln L(\theta) = \sum_i \ln p(x_i \mid \theta), \qquad \hat{\theta} = \arg\max_\theta \ln L
$$

(Log turns products into sums and leaves the maximum alone.) Parameter errors come from the curvature at the peak:

$$
\sigma_\theta^2 = \left(-\frac{\partial^2 \ln L}{\partial \theta^2}\right)^{-1}_{\hat\theta}
$$

— sharper peak, better-determined parameter (inverse Fisher information; matrix version gives the full covariance).

**Gaussian special case:** $p \sim e^{-(y_i - f_i)^2/2\sigma_i^2}$ ⇒ $\ln L = -\chi^2/2 + \text{const}$ — maximizing likelihood *is* [[Least Squares and Chi-Squared Fitting]], and $\Delta\chi^2 = 1 \Leftrightarrow \Delta\ln L = -1/2$.

**The Poisson caveat (low-count histograms — fluorescence detection, photon counting):** fit the Poisson likelihood, *not* $\chi^2$ with $\sigma_i = \sqrt{n_i}$. The $\sqrt{n_i}$ weights are wrong at small $n_i$ (a downward-fluctuating bin claims tiny error and drags the fit down; empty bins claim $\sigma = 0$), biasing amplitudes low by $O(1/n)$. Poisson $\ln L = \sum_i (n_i \ln \mu_i - \mu_i)$ costs nothing to implement.

Asymptotically MLE is unbiased and saturates the minimum possible variance — for finite $N$, check with [[Bootstrap Resampling]] or simulation.

> [!question]- Why does χ²-fitting a low-count histogram with $\sigma_i = \sqrt{n_i}$ bias the result low?
> Bins that fluctuate *down* get assigned smaller errors and thus more weight than bins fluctuating up — the fit preferentially follows downward fluctuations. Poisson likelihood weights by the model $\mu_i$, not the noisy data, killing the bias.

# Connections

- [[Least Squares and Chi-Squared Fitting]] — the Gaussian special case everyone uses daily
- [[Confidence Intervals]] — $\Delta\ln L = -1/2$ contours generalize the $\Delta\chi^2 = 1$ rule
- [[Poisson Distribution]] — the statistics of the counting data where MLE earns its keep
- [[Quantum State Tomography]] — MLE reconstruction keeps the density matrix physical

---
Source: Cowan, *Statistical Data Analysis*, Ch. 6
