#statistics #math

**Throw darts at a region enclosing the pdf and keep only the ones that land under the curve** — accepted $x$ values land with probability proportional to $f(x)$, so they're distributed as $f$. No CDF, no inversion, and $f$ doesn't even need to be normalized.

# Reference

Target $f(x)$, envelope $g(x)$ you *can* sample, constant $M$ with $f(x) \le M g(x)$ everywhere:

$$
x \sim g, \quad u \sim \mathrm{Uniform}(0,1): \qquad \text{accept } x \text{ if } u \le \frac{f(x)}{M g(x)}
$$

Repeat until accepted. Simplest envelope: a bounding box (uniform $g$) over a finite support.

**Efficiency = acceptance rate = $1/M$** — the ratio of the area under $f$ to the area under $Mg$. A tight envelope is everything; a loose one wastes almost every draw, and in high dimensions the area ratio collapses exponentially.

**When to use over [[Inverse Transform Sampling]]:**
- $F^{-1}$ has no closed form and you don't want to tabulate
- $f$ is known only **up to a normalization constant** (Bayesian posteriors — the killer feature)

> [!question]- Why are the accepted samples distributed as $f$?
> $P(x \in dx \text{ and accept}) = g(x)\,dx \cdot \frac{f(x)}{Mg(x)} = \frac{f(x)}{M}dx$ — the envelope cancels, leaving $f$ times a constant. Conditioning on acceptance restores normalization.

# Connections

- [[Inverse Transform Sampling]] — the alternative when the CDF inverts cleanly; rejection is what you do when it doesn't
- [[Monte Carlo Methods]] — rejection is a standard sample generator feeding MC estimates
- [[Box-Muller Transform]] — the Gaussian-specific dodge; its Marsaglia polar variant is itself a small rejection step

---
Source: Devroye, *Non-Uniform Random Variate Generation*, Ch. 2 (free online)
