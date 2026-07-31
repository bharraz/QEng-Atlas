#statistics #control #numerics

**All state estimation is one recursion: push the belief forward through the dynamics, then multiply by the likelihood of the new measurement.** Every named filter — Kalman, extended and unscented Kalman, particle, HMM forward, grid — is this same recursion with a different choice of how to represent the belief distribution. Learning the general form once means every specific filter reduces to "which representation, and what does it cost."

# Reference

The state $\mathbf{x}_k$ is hidden and evolves stochastically; measurements $\mathbf{z}_k$ are noisy functions of it. Two model pieces define the problem:

- **Transition model** $p(\mathbf{x}_k \mid \mathbf{x}_{k-1})$ — what the physics does, including process noise.
- **Observation model** $p(\mathbf{z}_k \mid \mathbf{x}_k)$ — what the sensor does, including measurement noise.

The object being maintained is the **belief**: the full posterior $p(\mathbf{x}_k \mid \mathbf{z}_{1:k})$, not a point estimate. The recursion alternates two steps.

**Predict** (Chapman–Kolmogorov — propagate and blur):

$$p(\mathbf{x}_k \mid \mathbf{z}_{1:k-1}) = \int p(\mathbf{x}_k \mid \mathbf{x}_{k-1})\; p(\mathbf{x}_{k-1} \mid \mathbf{z}_{1:k-1})\; d\mathbf{x}_{k-1}$$

**Update** (Bayes — sharpen on evidence):

$$p(\mathbf{x}_k \mid \mathbf{z}_{1:k}) = \frac{p(\mathbf{z}_k \mid \mathbf{x}_k)\; p(\mathbf{x}_k \mid \mathbf{z}_{1:k-1})}{p(\mathbf{z}_k \mid \mathbf{z}_{1:k-1})}$$

Read as a cycle of uncertainty: prediction *widens* the distribution (process noise adds ignorance), the measurement *narrows* it (data removes ignorance), and the filter settles where the two balance. Every filter's gain — Kalman's $K$, a particle's weight — is that balance made explicit.

**The denominator is not a nuisance.** $p(\mathbf{z}_k \mid \mathbf{z}_{1:k-1})$ is the *evidence*: how surprising this measurement was under the current model. Accumulating $\sum_k \log p(\mathbf{z}_k|\mathbf{z}_{1:k-1})$ gives the model's log-likelihood, which is how you fit unknown noise parameters, compare competing models, and detect faults (a sudden drop means the data stopped agreeing with your model).

**Assumptions that must hold.** The state is Markov (the future depends on the past only through the present state) and measurements are conditionally independent given the state. If your process has memory — $1/f$ noise is the standard offender ([[Noise Spectra and Coupling to Systems]]) — the fix is to *enlarge the state* so the memory is inside it, not to ignore the violation.

## The filters, as choices of representation

The integral above is exact and almost never tractable. Each named filter is a decision about how to carry the belief through it:

| Filter | Belief represented as | Exact when | Cost / failure mode |
|---|---|---|---|
| [[Kalman Filter]] | mean + covariance | linear dynamics, Gaussian noise | exact and cheap; wrong shape otherwise |
| Extended KF | mean + covariance | — (linearizes about the estimate) | cheap; diverges if curvature is large over the spread |
| Unscented KF | mean + covariance via sigma points | — (matches moments through the nonlinearity) | no Jacobians, better than EKF; still unimodal |
| Grid / HMM forward | probability on a discrete lattice | discrete or discretized state | exact for discrete states; cost explodes with dimension |
| [[Particle Filter]] | weighted samples | asymptotically as $N \to \infty$ | fully general; $1/\sqrt N$ error, dies above ~5–10 dimensions |
| Gaussian mixture | sum of Gaussians | multimodal but locally Gaussian | handles multimodality at moderate cost; component bookkeeping |

The single question that picks the row: **is the posterior well described by one Gaussian bump?** If yes, use a Kalman variant — it is enormously cheaper and, in the linear-Gaussian case, exactly optimal. If the posterior is genuinely multimodal or heavy-tailed, no amount of covariance tuning fixes it, because a mean and covariance cannot represent two hypotheses; you need samples or mixtures.

## Filtering, smoothing, prediction

Same models, different conditioning — worth distinguishing because using the wrong one wastes information:

- **Filtering** $p(\mathbf{x}_k|\mathbf{z}_{1:k})$ — estimate now from data so far. Required for real-time feedback.
- **Prediction** $p(\mathbf{x}_{k+m}|\mathbf{z}_{1:k})$ — run the predict step forward without updates; the belief widens monotonically.
- **Smoothing** $p(\mathbf{x}_k|\mathbf{z}_{1:T})$ — estimate the past given *all* data, forward pass plus backward pass. Strictly more accurate than filtering and the correct choice for offline analysis; using a filter on archived data throws away every measurement after time $k$.

## In the lab

The recursion is the right frame whenever a quantity is estimated repeatedly from noisy partial measurements: tracking a drifting laser or cavity frequency, fusing a fast noisy sensor with a slow accurate one, following a qubit frequency that random-walks, or learning Hamiltonian parameters from binary outcomes. Two habits carry over regardless of which filter you pick: state the transition and observation models explicitly (most filter failures are model failures wearing a numerical disguise), and monitor the innovation sequence $\mathbf{z}_k - \mathbb{E}[\mathbf{z}_k]$ — for a correctly specified filter it is white, and any structure in it means the model is missing dynamics ([[Autocorrelation]]).

> [!question]- Two sensors disagree, and your filter reports a value between them that no sensor measured and the physics forbids. What went wrong at the level of the general recursion?
> Nothing in the recursion — the belief was represented wrongly. A genuinely bimodal posterior ("either sensor A is right or sensor B is") cannot be carried by a mean and covariance, so a Kalman-family filter reports the mean of the two modes: a number with high probability density in the model and zero in reality. The general Bayes filter has no such problem; the failure is entirely in the Gaussian representation. Fix by changing representation (particle filter, Gaussian mixture), or by enlarging the state to include a discrete "which sensor is faulty" variable so the modes become separate hypotheses rather than one smeared distribution.

# Connections

- [[Kalman Filter]] — the linear-Gaussian closed form; the recursion with algebra instead of integrals
- [[Particle Filter]] — the Monte Carlo representation; general at $1/\sqrt N$ cost
- [[Maximum Likelihood Estimation]] — the update step is a likelihood multiplication; the evidence accumulates into a log-likelihood
- [[Monte Carlo Methods]] — the sampling machinery behind the general case
- [[Control Beyond PID]] — estimation feeding control; LQG is this plus LQR
- [[Autocorrelation]] — innovation whiteness as the model-validation test
- [[Noise Spectra and Coupling to Systems]] — when the Markov assumption fails and the state must be enlarged

---
Further reading: Särkkä, *Bayesian Filtering and Smoothing* (2013) — the standard unified treatment, freely available; Barfoot, *State Estimation for Robotics*, Ch. 3–4; Chen, "Bayesian filtering: from Kalman filters to particle filters and beyond" (2003)
