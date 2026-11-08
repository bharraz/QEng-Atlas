#statistics #math

**You record a frequency (or any slowly drifting quantity) over time and want to know how stable it is; the ordinary variance fails, because drift and flicker make it grow without bound as you take more data. The Allan variance is the variance of the *difference* between consecutive $\tau$-averages instead — differencing removes that divergence — and the slope of $\sigma_y(\tau)$ vs $\tau$ on a log-log plot fingerprints the noise type.**

# Reference

For fractional frequency (or any drifting observable) averaged over adjacent bins of length $\tau$:

$$
\sigma_y^2(\tau) = \tfrac{1}{2}\left\langle (\bar{y}_{k+1} - \bar{y}_k)^2 \right\rangle
$$

- $y$ — the observable, usually *fractional* frequency $y = \Delta\nu/\nu_0$ (dimensionless): makes $\sigma_y$ comparable across clocks
- $\bar y_k$ — its average over the $k$-th bin of duration $\tau$
- $\tau$ — averaging time (s), the independent variable: an Allan deviation is a *curve*, never one number
- $\sigma_y$ — the Allan *deviation*, the square root

The factor $\tfrac12$ is chosen so that for white noise $\sigma_y^2(\tau)$ equals the ordinary variance of the mean, making the two agree where both are valid.

**Picture:** compare each block average with the next: drift slow compared with the block length nearly cancels in the difference, so the curve shows how stable the quantity is at each averaging time.

The standard variance of a drifting signal grows without bound as you take more data — it's measuring the drift, not the noise. The first difference is insensitive to a constant offset and converges for every noise type down to random-walk FM.

**The log-log slope table** (slope of $\sigma_y(\tau)$, i.e. the Allan *deviation*; PM = noise in the phase, FM = noise in the frequency, and $S_y(f)$ is the power spectral density of $y$):

| Noise type | $S_y(f)$ | $\sigma_y(\tau)$ slope |
|---|---|---|
| White PM | $f^{2}$ | $\tau^{-1}$ |
| Flicker PM | $f^{1}$ | $\approx\tau^{-1}$ (log corr.) |
| White FM | $f^{0}$ | $\tau^{-1/2}$ |
| Flicker FM | $f^{-1}$ | $\tau^{0}$ (flat floor) |
| Random-walk FM | $f^{-2}$ | $\tau^{+1/2}$ |
| Linear drift | — | $\tau^{+1}$ |

White PM and flicker PM are nearly degenerate here — use the *modified* Allan variance to separate them.

**Reading the curve:** slope $-1/2$ region = still winning by averaging (white FM); the minimum = **optimal averaging time** and the flicker floor = best stability you will ever get; upturn = drift/random walk taking over, at which point more averaging actively hurts.

> [!question]- Your Allan deviation goes flat at $\tau = 30$ s. What does averaging for 10 minutes gain?
> Nothing — you've hit the flicker-FM floor; stability no longer improves with $\tau$ and may degrade once drift's $\tau^{+1}$ takes over. Measure in ~30 s blocks and fix the drift (or interleave a reference) instead.

# Connections

- [[Flicker Noise]] — the noise that creates the floor and defeats the standard variance
- [[Power Spectral Density]] — the frequency-domain dual; each PSD power law maps to a slope above
- [[SNR and Averaging]] — Allan analysis answers "how long should I average" quantitatively
- [[Laser Linewidth]] — oscillator stability characterization is this tool's home turf
- [[Noise Spectra and Coupling to Systems]] — the spectral taxonomy the slope table maps onto

---
Source: Riley, *Handbook of Frequency Stability Analysis*, NIST SP 1065
