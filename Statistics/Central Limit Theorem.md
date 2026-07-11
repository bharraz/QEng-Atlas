#statistics #math

**Sums of many independent random contributions come out Gaussian, whatever the ingredients** — which is why Gaussians are everywhere: every noise voltage, averaged signal, and fit residual is secretly a sum.

# Reference

For iid $x_i$ with mean $\mu$ and *finite* variance $\sigma^2$:

$$
\bar{x} = \frac{1}{N}\sum_{i=1}^{N} x_i \;\xrightarrow{N\to\infty}\; \mathcal{N}\!\left(\mu,\; \frac{\sigma^2}{N}\right)
$$

**The working consequence: the mean's standard deviation is $\sigma/\sqrt{N}$** — average 100 shots, error bars shrink 10×. This single line underwrites [[SNR and Averaging]] and every "$/\sqrt{N}$" in a lab notebook.

**Conditions and caveats:**
- **Finite variance required.** Heavy tails break it — a Lorentzian (Cauchy) lineshape has no variance; the mean of $N$ Cauchy samples is *exactly as wide as one sample*. Averaging does nothing.
- Independence (or weak enough correlation) — correlated samples give $\sigma/\sqrt{N_{\text{eff}}}$ with $N_{\text{eff}} \ll N$; see [[Autocorrelation]].
- **Convergence is slowest in the tails**: the core looks Gaussian long before the $3$–$5\sigma$ wings do. Outlier rates from real data routinely exceed Gaussian predictions.

> [!question]- You average $N$ samples drawn from a Lorentzian. How does the width of the mean scale with $N$?
> It doesn't — the Cauchy distribution is stable: the sample mean has the same distribution as a single sample. No finite variance, no CLT, no $\sqrt{N}$ gain.

# Connections

- [[Gaussian Distribution]] — the CLT is the reason this distribution owns experimental physics
- [[SNR and Averaging]] — the $\sqrt{N}$ improvement and, crucially, when it fails
- [[Monte Carlo Methods]] — MC error bars are CLT applied to the sample mean
- [[Error Propagation]] — many small independent error sources ⇒ Gaussian total, justifying quadrature sums

---
Source: Casella & Berger, *Statistical Inference* 2nd ed., §5.5
