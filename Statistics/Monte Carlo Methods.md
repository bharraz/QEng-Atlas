#statistics #math

**Turn an integral or error budget into an average over random samples** — the estimate is just the sample mean, and its error shrinks as $1/\sqrt{N}$ *regardless of dimension*, which is why MC beats grid quadrature the moment the problem has more than a few variables.

# Reference

$$
\int f(x)\,p(x)\,dx \;\approx\; \frac{1}{N}\sum_{i=1}^{N} f(x_i), \qquad x_i \sim p
$$

with statistical error

$$
\sigma_{\text{est}} = \frac{\sigma_f}{\sqrt{N}}, \qquad \sigma_f^2 = \mathrm{Var}[f(x)]
$$

estimated from the samples themselves. Compare grid methods: error $\sim N^{-k/d}$ — dead by $d \gtrsim 4$. MC's $N^{-1/2}$ doesn't care about $d$ (it's the [[Central Limit Theorem]] at work).

**Lab workflow:** propagate errors through any nasty pipeline by drawing inputs from their error distributions, pushing each draw through the full analysis, and reading $\sigma$ off the output histogram. Works where linearized [[Error Propagation]] fails.

**Importance sampling:** sample from $q$ concentrated where $|f|p$ is large, weight each sample by $p/q$ — same mean, smaller $\sigma_f$.

> [!question]- Why doesn't the $1/\sqrt{N}$ error scaling degrade with dimension?
> The estimate is a mean of iid random variables; CLT gives $\sigma/\sqrt{N}$ with no reference to how many coordinates each sample has. Dimension hides in $\sigma_f$ (a constant), not in the $N$-scaling.

# Connections

- [[Inverse Transform Sampling]] — the front door: turning uniforms into the distributions you need
- [[Rejection Sampling]] — the sampler for awkward or unnormalized distributions
- [[Bootstrap Resampling]] — Monte Carlo where the "distribution" is your own dataset
- [[Central Limit Theorem]] — the source of the $1/\sqrt{N}$ guarantee

---
Source: Press et al., *Numerical Recipes* 3rd ed., Ch. 7
