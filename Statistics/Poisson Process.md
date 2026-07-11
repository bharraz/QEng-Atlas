#statistics #math

**Independent events arriving at constant rate $\lambda$ with no memory** — counts in any window are Poisson, gaps between events are exponential, and nothing that happened before changes what happens next. The model under photon counting, radioactive decay, and dark counts.

# Reference

Counts in time $T$:

$$
N(T) \sim \mathrm{Poisson}(\lambda T): \qquad P(N = n) = \frac{(\lambda T)^n e^{-\lambda T}}{n!}, \qquad \langle N\rangle = \mathrm{Var}(N) = \lambda T
$$

Waiting times between events: exponential, $f(t) = \lambda e^{-\lambda t}$, **memoryless** — the expected wait to the next photon is $1/\lambda$ *regardless of how long you've already waited*. (Sample as $t = -\ln u/\lambda$; this is how you simulate one.)

**Two closure properties worth knowing cold:**
- **Thinning:** keep each event independently with probability $p$ (detector quantum efficiency, beamsplitter) → still Poisson, rate $p\lambda$. **A lossy detector changes the rate, not the statistics** — you can't fix Poisson noise downstream, and sub-Poissonian light survives loss only partially.
- **Merging:** sum of independent Poisson processes → Poisson, rate $\sum_i \lambda_i$ (signal + dark counts + stray light: still Poisson, rates add).

$\mathrm{Var} = \mathrm{mean}$ is the fingerprint: measured variance above $\lambda T$ ⇒ rate fluctuations or bunching; below ⇒ dead time or genuinely nonclassical light.

> [!question]- Your photon counter has 20% efficiency. Does the missed 80% distort the counting statistics?
> No — thinning a Poisson process gives an exactly Poisson process at $0.2\lambda$. You lose rate (hence SNR $\propto \sqrt{p}$), but the variance/mean ratio stays 1. That's also why detector loss degrades but doesn't destroy the classical-light baseline in $g^{(2)}$ measurements.

# Connections

- [[Exponential Distribution]] — the memoryless waiting-time law between events
- [[Poisson Distribution]] — the count statistics in any fixed window
- [[Shot Noise]] — this process in a current: white noise with $S_I = 2eI$
- [[Inverse Transform Sampling]] — exponential gaps make simulation two lines

---
Source: Gallager, *Stochastic Processes: Theory for Applications*, Ch. 2
