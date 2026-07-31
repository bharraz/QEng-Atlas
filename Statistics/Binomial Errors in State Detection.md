#statistics #math

**Estimating a probability from $k$ successes in $N$ shots: $\hat p = k/N$ with error $\sqrt{p(1-p)/N}$ — but near $p = 0$ or $1$ the naive formula collapses to zero and lies.** Exactly the regime where qubit readout lives (fidelities near 1).

# Reference

$$
\hat{p} = \frac{k}{N}, \qquad \sigma_{\hat p} = \sqrt{\frac{\hat p(1 - \hat p)}{N}}
$$

$k$ = successes counted; $N$ = shots; $\hat p$ = estimated probability (dimensionless). The $p(1-p)$ numerator is the variance of a single Bernoulli trial, and dividing by $N$ is the usual variance-of-the-mean — so $\sigma \propto 1/\sqrt{N}$ as always, but with a prefactor that *vanishes at the extremes*. Error is largest at $p = 1/2$ ($\sigma = 1/2\sqrt N$) and the Gaussian approximation holds for $Np(1-p) \gtrsim 10$; note this means the required shot count depends on where $p$ sits, not just on the precision you want.

**The edge failure:** $k = 0$ or $k = N$ gives $\sigma = 0$ — a 100%-confident fidelity claim from finite data. Never quote it. Use instead:
- **Wilson interval** (good default): center $\tilde p = \frac{k + z^2/2}{N + z^2}$, half-width $\frac{z}{N + z^2}\sqrt{\frac{k(N-k)}{N} + \frac{z^2}{4}}$, with $z = 1$ for 68%. Never returns zero width, respects $[0,1]$.
- **Clopper–Pearson**: exact coverage from binomial tails; conservative; the referee-proof choice.
- **Rule of three:** $k = 0$ in $N$ shots ⇒ 95% upper bound $p < 3/N$. ($0$ errors in 1000 shots does *not* mean $p_{\text{err}} < 10^{-4}$.)

**Quantum projection noise** is this same formula wearing quantum clothes: measuring $N$ atoms/ions each in superposition with excitation probability $p$, the projection of each onto an eigenstate is a Bernoulli trial — fluctuation $\sqrt{p(1-p)/N}$, maximal at the Ramsey fringe side ($p = 1/2$). It's the standard quantum limit for clocks and the noise floor of every population measurement.

> [!question]- 500 shots, zero errors observed. Quote the gate/detection error.
> Not "$0 \pm 0$". Rule of three: $p < 3/500 = 6 \times 10^{-3}$ at 95% confidence (Wilson/Clopper–Pearson give the same scale). Zero observed events bounds, it doesn't measure — to *measure* an error of $10^{-3}$ you need $\gtrsim$ several $\times 10^3$ shots with events in them.

# Connections

- [[Binomial Distribution]] — the underlying pmf, and its Gaussian limit that fails at the edges
- [[Confidence Intervals]] — Wilson and Clopper–Pearson are the boundary-respecting constructions
- [[State and Gate Fidelity]] — the quantity these error bars get attached to
- [[Shot Noise]] — projection noise as the counting-statistics cousin

---
Source: Itano et al., "Quantum projection noise," *Phys. Rev. A* **47**, 3554 (1993)
