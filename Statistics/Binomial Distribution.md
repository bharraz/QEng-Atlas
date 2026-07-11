#statistics #math

**N independent yes/no trials with success probability p — the statistics behind every repeated qubit readout.** Measure a qubit N times and count the bright outcomes: that count is binomial, full stop.

# Reference

$$
P(k) = \binom{N}{k} p^k (1-p)^{N-k}, \qquad \langle k\rangle = Np, \quad \mathrm{Var}(k) = Np(1-p)
$$

Estimating $p$: $\hat p = k/N$ with $\sigma_{\hat p} = \sqrt{p(1-p)/N}$ — worst at $p=1/2$, deceptively small near 0 and 1 (a trap; see the state-detection card).

**Limits:**

| regime | limit |
|---|---|
| $N\to\infty$, $Np$ fixed | Poisson($\lambda = Np$) |
| $Np(1-p)\gtrsim 10$ | Gaussian $\mathcal N(Np,\ Np(1-p))$ |

The $p(1-p)$ factor is projection noise in disguise: a qubit at the equator ($p=1/2$) is maximally noisy to measure; near the poles it's quiet. Sensitivity per shot is fundamentally bounded by this variance.

> [!question]- Why does the shot-to-shot variance of qubit readout vanish as p→0 or 1, and why can't you then trust σ̂=0 from your data?
> $\mathrm{Var}=Np(1-p)\to 0$ because outcomes become deterministic. But $\hat p = 0/N$ plugged into the formula gives $\hat\sigma = 0$ — an artifact of estimating p from the same finite sample. Use Wilson or Clopper-Pearson intervals near the boundary.

# Connections

- [[Binomial Errors in State Detection]] — the lab card built on exactly this, including the p≈0,1 fix
- [[Poisson Distribution]] — the rare-event limit
- [[Gaussian Distribution]] — the mid-range limit that justifies normal error bars
- [[Central Limit Theorem]] — why the Gaussian limit exists at all

---
Source: Taylor, *An Introduction to Error Analysis*, Ch. 10
