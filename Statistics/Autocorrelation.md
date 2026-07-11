#statistics #math

**A signal's covariance with a time-shifted copy of itself — the decay of $R(\tau)$ with lag is the signal's memory.** Fast decay = fresh information every sample; slow decay = your "independent" samples aren't.

# Reference

For a stationary, zero-mean signal:

$$
R(\tau) = \langle x(t)\,x(t+\tau)\rangle
$$

$R(0) = \sigma^2$; normalized form $r(\tau) = R(\tau)/R(0)$. The **correlation time** $\tau_c$ (decay scale of $R$) is the memory of the process.

| Process | $R(\tau)$ |
|---|---|
| White noise | $\propto \delta(\tau)$ — no memory at all |
| First-order low-passed white (OU process) | $\sigma^2 e^{-\|\tau\|/\tau_c}$ → Lorentzian PSD |
| Drift / 1/f | decays slower than any single exponential — long memory |

**The error-bar gotcha:** sampling faster than $\tau_c$ doesn't buy statistics. For $N$ samples spaced $\Delta t < \tau_c$,

$$
N_{\text{eff}} \approx \frac{N \Delta t}{2\tau_c}
$$

and the error of the mean is $\sigma/\sqrt{N_{\text{eff}}}$, not $\sigma/\sqrt{N}$. Quoting $\sqrt{N}$ error bars on correlated data is the classic way to lie to yourself mid-measurement.

> [!question]- You double your DAQ rate on the same noise process. Do your error bars improve?
> Only if the new samples are separated by more than $\tau_c$. Below that spacing you're re-measuring the same fluctuation; $N_{\text{eff}}$ is set by measurement duration over $\tau_c$, not by sample count.

# Connections

- [[Wiener-Khinchin Theorem]] — $R(\tau)$ and the PSD are a Fourier pair; two views of one object
- [[Variance and Covariance]] — $R(\tau)$ is covariance applied along the time axis
- [[Flicker Noise]] — the long-memory case where correlations never die and averaging stalls
- [[SNR and Averaging]] — $N_{\text{eff}}$ is why averaging gains saturate

---
Source: Papoulis & Pillai, *Probability, Random Variables and Stochastic Processes* 4th ed., Ch. 9
