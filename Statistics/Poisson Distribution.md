#statistics #math

**Counting independent random events at a fixed mean rate — variance equals mean, so counting noise is always $\sqrt{N}$.** Photon counts, dark counts, radioactive decays: if arrivals don't care about each other, this is their distribution.

# Reference

$$
P(k) = \frac{\lambda^k e^{-\lambda}}{k!}, \qquad \langle k\rangle = \mathrm{Var}(k) = \lambda
$$

**The working consequence:** relative fluctuation $\sigma/\langle k\rangle = 1/\sqrt{\lambda}$ — collect 100 photons for 10% noise, 10⁴ for 1%. This is shot noise in count form.

**Limits:**
- Binomial → Poisson when $N\to\infty$, $p\to 0$ with $Np=\lambda$ fixed (many tries, rare success).
- Poisson → Gaussian $\mathcal N(\lambda,\lambda)$ for $\lambda \gtrsim 20$; below that the asymmetry is real — don't put symmetric error bars on 3 counts.

**Fitting gotcha:** for low-count histograms, maximize the Poisson likelihood instead of minimizing χ² with $\sigma_i=\sqrt{n_i}$ — bins that fluctuate low get tiny "errors" and drag the fit down.

> [!question]- State detection collects on average 25 photons when bright, ~0 when dark. With a perfect detector, what still limits discrimination?
> The Poisson spread of the bright count ($\sigma=5$) overlapping the dark distribution — the tails set the misclassification error, and only more photons (or arrival-time analysis) shrink it.

# Connections

- [[Shot Noise]] — the current/optical-power incarnation of $\mathrm{Var}=\langle N\rangle$
- [[Poisson Process]] — the underlying time process whose fixed-window counts are Poisson
- [[Binomial Distribution]] — the parent distribution in the rare-event limit
- [[Coherent States]] — laser light has exactly Poissonian photon statistics
- [[Maximum Likelihood Estimation]] — the right way to fit low-count data

---
Source: Bevington & Robinson, *Data Reduction and Error Analysis*, Ch. 2
