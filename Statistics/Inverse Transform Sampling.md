#statistics #math

**To sample from any distribution, push uniform randoms backwards through its CDF** — the CDF maps the distribution onto [0,1] uniformly, so running it in reverse turns uniform samples into your distribution.

# Reference

Target pdf $f(x)$ with CDF $F(x) = \int_{-\infty}^{x} f(x')\,dx'$:

$$
u \sim \mathrm{Uniform}(0,1), \qquad x = F^{-1}(u) \;\;\Rightarrow\;\; x \sim f
$$

> [!question]- Why does it work?
> $P(x \le a) = P(F^{-1}(u) \le a) = P(u \le F(a)) = F(a)$ — which is the definition of $x$ having CDF $F$. Only needs $F$ monotonic.

**Worked case — exponential waiting times** (photon arrivals, decay):
$$
f(t) = \Gamma e^{-\Gamma t}, \quad F(t) = 1 - e^{-\Gamma t} \;\;\Rightarrow\;\; t = -\frac{\ln u}{\Gamma}
$$
(using $1-u \sim u$)

**Discrete version:** cumulative sum of the probabilities; take the first bin where cumsum ≥ $u$.

**When $F^{-1}$ has no closed form** (Gaussian): use [[Box-Muller Transform]] or [[Rejection Sampling]], or invert numerically — tabulate $F$ on a grid, interpolate backwards.

# Connections

- [[Box-Muller Transform]] — the Gaussian case, where inverting is dodged with a polar-coordinates trick
- [[Rejection Sampling]] — when the CDF won't invert and you'd rather throw darts
- [[Poisson Process]] — its exponential inter-arrival times are sampled exactly as above
- [[Monte Carlo Methods]] — this is the front door: every MC run starts by turning uniforms into the distribution you need
- [[PDF and CDF]] — the change-of-variables identity this whole trick rests on

---
Source: Devroye, *Non-Uniform Random Variate Generation*, Ch. 2 (free online)
