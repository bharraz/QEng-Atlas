#statistics #control #numerics

**Represent the state's probability distribution by a swarm of weighted samples instead of a mean and covariance: propagate each sample through the (possibly nonlinear) dynamics, reweight by how well it explains the new measurement, and resample.** It is [[Recursive Bayesian Filtering]] with the belief represented by samples rather than by a mean and covariance — the [[Kalman Filter]] with the Gaussian assumption removed, bought with computation rather than algebra.

# Reference

State the same estimation problem: hidden state $\mathbf{x}_k$ evolving as $p(\mathbf{x}_k|\mathbf{x}_{k-1})$, observed through $p(\mathbf{z}_k|\mathbf{x}_k)$. The posterior is approximated by $N$ samples ("particles") with weights:

$$p(\mathbf{x}_k \mid \mathbf{z}_{1:k}) \approx \sum_{i=1}^{N} w_k^{(i)}\, \delta\!\left(\mathbf{x}_k - \mathbf{x}_k^{(i)}\right), \qquad \sum_i w_k^{(i)} = 1.$$

The cycle, matching Kalman's predict/update:

1. **Propagate** — draw each particle forward through the dynamics, $\mathbf{x}_k^{(i)} \sim p(\mathbf{x}_k|\mathbf{x}_{k-1}^{(i)})$, noise included. No linearization, no Jacobian.
2. **Weight** — multiply by the likelihood of the observation, $w_k^{(i)} \propto w_{k-1}^{(i)}\, p(\mathbf{z}_k|\mathbf{x}_k^{(i)})$, then normalize. Particles that predicted the measurement well gain weight.
3. **Resample** — draw $N$ new particles with replacement in proportion to weight, resetting all weights to $1/N$.

**Why step 3 is not optional.** Without it, weight concentrates on a handful of particles within a few iterations — *degeneracy* — and the effective sample size $N_{\text{eff}} = 1/\sum_i (w^{(i)})^2$ collapses toward 1, meaning the swarm is doing the work of one particle. Standard practice: resample when $N_{\text{eff}} < N/2$, using systematic or stratified resampling (lower variance than naive multinomial). The cost is **sample impoverishment** — repeated copies of the same particle lose diversity — mitigated by adding small jitter (regularization) or by resampling only when needed.

**Accuracy scales as Monte Carlo, not as a series.** Error falls as $1/\sqrt{N}$ regardless of dimension for a fixed problem, but the $N$ *needed* grows sharply with state dimension: particle filters are the tool of choice up to ~5–10 dimensions and degrade badly above that (the weights' variance grows exponentially with dimension). This is the practical dividing line against Gaussian methods, not any statement about nonlinearity.

## When it beats the alternatives

| Situation | Use |
|---|---|
| Linear dynamics, Gaussian noise | [[Kalman Filter]] — optimal and vastly cheaper |
| Mildly nonlinear, still unimodal | Extended KF (linearize) or unscented KF (deterministic sigma points) |
| Multimodal posterior, hard nonlinearity, non-Gaussian noise | **Particle filter** |
| Offline data, causality not required | Smoother (forward–backward pass) — strictly better than filtering |

The distinguishing capability is **multimodality**: a Kalman filter carries one mean and covariance and therefore one hypothesis, so when the data admit two candidate states it reports the average of them — a value that may be physically impossible. A particle swarm simply carries both clusters until evidence kills one.

## Where it shows up

- **Adaptive Bayesian experiment design in quantum labs**: tracking a qubit frequency, a Rabi rate, or Hamiltonian parameters from binary measurement outcomes. The likelihood $p(\text{outcome}|\theta)$ is a sinusoid in the parameters, so the posterior is genuinely multimodal early on — exactly the Kalman failure case. The same machinery chooses the *next* measurement to maximize information gain, which is Bayesian experimental design over the particle cloud ([[Fisher Information and the Cramér-Rao Bound]] supplies the objective).
- **Phase estimation and frequency tracking** where wrapping makes the posterior multimodal by construction.
- **Non-Gaussian noise environments**: a bath dominated by a few strongly-coupled two-level fluctuators produces telegraph, not Gaussian, statistics ([[Noise Spectra and Coupling to Systems]]) — a filter assuming Gaussian process noise misestimates systematically.
- Classically: robot localization, target tracking, and any system with hard constraints (a particle that violates a constraint simply gets zero weight — no machinery required).

**Implementation notes that matter.** Work in log-weights and normalize with a log-sum-exp to avoid underflow ([[Floating Point and Numerical Error]]); the propagation step is embarrassingly parallel while the resampling step is a global reduction, so that step dominates on GPUs ([[Performance Optimization]]); seed independent RNG streams per worker ([[Monte Carlo Methods]]); and validate against a Kalman filter on a linear-Gaussian test case, where the two must agree.

> [!question]- A particle filter tracking a qubit frequency converges quickly, then abruptly locks onto a value that is badly wrong and never recovers. What happened?
> Sample impoverishment after premature resampling. Early measurements produced a multimodal posterior; aggressive resampling deleted every particle in the true mode before enough data accumulated to distinguish the modes, and since particles are only ever propagated forward with local noise, no particle can be regenerated in a region the swarm has abandoned. The filter is then confidently wrong with a small spread. Fixes: resample only when $N_{\text{eff}}$ falls below threshold, add regularization jitter after resampling, increase $N$, or broaden the prior — and treat a rapidly shrinking spread as a warning rather than a sign of success.

# Connections

- [[Recursive Bayesian Filtering]] — the general recursion; this page is one choice of representation
- [[Kalman Filter]] — the linear-Gaussian special case; same predict/update skeleton
- [[Monte Carlo Methods]] — the sampling machinery and its $1/\sqrt{N}$ convergence
- [[Maximum Likelihood Estimation]] — the likelihood being evaluated per particle
- [[Bootstrap Resampling]] — the same resample-with-replacement operation, used for error bars instead of tracking
- [[Fisher Information and the Cramér-Rao Bound]] — the objective when the filter also chooses the next measurement
- [[Control Beyond PID]] — state estimation as the front end of feedback
- [[Noise Spectra and Coupling to Systems]] — non-Gaussian noise as the reason to leave Kalman behind

---
Further reading: Doucet & Johansen, "A tutorial on particle filtering and smoothing" (2011); Arulampalam et al., *IEEE Trans. Signal Process.* 50, 174 (2002); Granade et al., "Robust online Hamiltonian learning," *New J. Phys.* 14, 103013 (2012) — particle filtering for qubit parameter estimation
