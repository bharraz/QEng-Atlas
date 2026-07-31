#statistics #control

**The Kalman filter is the optimal way to track a state you can't measure directly: alternate "predict" (push your estimate through the dynamics model, uncertainty grows) and "update" (blend in the new measurement, weighted by how much you trust it vs the prediction).** It is the linear-Gaussian special case of [[Recursive Bayesian Filtering]] — the general recursion's integrals collapse to algebra because a Gaussian pushed through a linear map stays Gaussian — and the formal answer to every ad-hoc question about how hard to smooth your data.

# Reference

Model: state $\mathbf{x}_k = A\mathbf{x}_{k-1} + \mathbf{w}$ (process noise $Q$), measurement $\mathbf{z}_k = H\mathbf{x}_k + \mathbf{v}$ (noise $R$). Track the estimate $\hat{\mathbf{x}}$ *and its covariance* $P$:

**Predict:** $\hat{\mathbf{x}} \to A\hat{\mathbf{x}}$, $\quad P \to APA^\top + Q$
**Update:** $\hat{\mathbf{x}} \to \hat{\mathbf{x}} + K(\mathbf{z} - H\hat{\mathbf{x}})$, with the Kalman gain

$$K = PH^\top(HPH^\top + R)^{-1}$$

— literally *(prediction uncertainty)/(total uncertainty)*: noisy sensor or confident model → small $K$, trust the model; volatile dynamics ($Q$ large) → large $K$, chase the data. A running average, exponential smoothing, and PLL-style tracking are all special cases with hand-picked constant $K$; the filter computes the time-varying optimal one.

Uses in the lab: laser/cavity drift tracking, fusing a fast noisy sensor with a slow accurate one, extracting a frequency that random-walks (the drift model lives in $A$, $Q$), feedback on an estimated state ([[Control Beyond PID|LQG]] = Kalman + LQR). Nonlinear dynamics → extended (linearize) or unscented (sample) variants; genuinely multimodal or non-Gaussian posteriors → [[Particle Filter]], which drops the Gaussian assumption entirely at Monte Carlo cost; offline data → run the smoother (forward + backward pass) instead, it's strictly better when causality doesn't matter.

The honest cost: performance is only "optimal" relative to the declared $Q$ and $R$ — and $Q$ is usually a guess. Tune it by whitening: the innovation sequence $\mathbf{z} - H\hat{\mathbf{x}}$ of a well-tuned filter is white ([[Autocorrelation]] flat); structure in it means the model is missing dynamics.

# Connections

- [[Control Beyond PID]] — LQG: this filter feeding an optimal controller
- [[Maximum Likelihood Estimation]] — the Bayesian-update machinery underneath
- [[Autocorrelation]] — innovation whiteness as the tuning criterion
- [[Allan Variance]] — the noise taxonomy (white vs random-walk) that populates $Q$ and $R$
- [[Particle Filter]] — the same recursion without the Gaussian assumption
- [[Recursive Bayesian Filtering]] — the general algorithm this is a special case of

---
Source: Kalman, *J. Basic Eng.* 82, 35 (1960); Simon, *Optimal State Estimation*, Ch. 5
