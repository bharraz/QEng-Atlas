#statistics #math

**Waiting times of memoryless processes — the chance of decay in the next instant never depends on how long you've already waited.** Excited-state lifetimes, photon inter-arrival times, time-to-failure of anything with constant hazard rate.

# Reference

$$
f(t) = \Gamma e^{-\Gamma t}, \qquad \langle t\rangle = \frac{1}{\Gamma}, \quad \sigma_t = \frac{1}{\Gamma}
$$

Mean equals standard deviation — an exponential is intrinsically "100% noisy," which is why one decay event tells you almost nothing about τ and you always fit ensembles.

**Memorylessness:** survival $P(t>u)=e^{-\Gamma u}$ and $P(t > s+u \mid t>s) = P(t>u)$. The exponential is the *only* continuous distribution with this property — it's equivalent to a constant decay rate.

**Poisson connection:** waiting times between events of a rate-λ [[Poisson Process]] are exponential with Γ=λ, and conversely — same physics, two views.

**Sampling:** $t = -\ln(u)/\Gamma$ — the one inverse-CDF everyone has memorized.

**Fit gotcha:** a lifetime histogram truncated by a finite detection window biases τ short unless the window is in the fit model.

> [!question]- Your ion has already survived 3 lifetimes in the excited state. What's its expected *remaining* time there?
> Still $1/\Gamma$ — memorylessness means survivors are statistically fresh. No aging.

# Connections

- [[Poisson Process]] — exponential waits generate Poisson counts and vice versa
- [[Inverse Transform Sampling]] — this is its cleanest worked example
- [[Spontaneous Emission and Linewidth]] — the physics ($\tau = 1/\Gamma$) that makes lifetimes exponential

---
Source: Bevington & Robinson, *Data Reduction and Error Analysis*, Ch. 2
