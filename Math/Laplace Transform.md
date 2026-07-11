#math

**The Fourier transform for systems with a beginning and with damping** — $s = \sigma + i\omega$ lets the kernel $e^{-st}$ tame growing or stepped signals that have no Fourier transform, and it turns initial-value ODE problems into polynomial algebra.

# Reference

$$
F(s) = \int_0^\infty f(t)\, e^{-st}\, dt
$$
Converges for $\mathrm{Re}(s)$ large enough (right of all poles) — the region of convergence; you rarely think about it until a signal grows exponentially.

**Key pairs:**

| $f(t)$ | $F(s)$ |
|---|---|
| $1$ (step) | $1/s$ |
| $t^n$ | $n!/s^{n+1}$ |
| $e^{-at}$ | $1/(s+a)$ |
| $\sin\omega t$, $\cos\omega t$ | $\omega/(s^2+\omega^2)$, $s/(s^2+\omega^2)$ |
| $e^{-at}\sin\omega t$ | $\omega/((s+a)^2+\omega^2)$ |
| $\delta(t)$ | $1$ |

**The killer property** — derivatives become multiplication *and initial conditions ride along free*:
$$
\mathcal{L}[\dot{f}] = sF(s) - f(0), \qquad \mathcal{L}[\ddot{f}] = s^2 F(s) - s f(0) - \dot{f}(0)
$$
So an ODE with initial conditions → algebraic equation in $s$ → partial fractions → invert by table. Poles of $F(s)$ are the system's natural frequencies: $s = -\gamma/2 \pm i\omega_1$ means decaying oscillation; pole in the right half-plane means instability.

**$s = i\omega$ recovers Fourier** (steady-state response), which is why the transfer function $H(s)$ evaluated on the imaginary axis is the Bode plot. Control theory lives in the $s$-plane: pole locations = stability, imaginary axis = the measurement.

> [!question]- Where do the poles of the transfer function live for a stable, underdamped system, and what does each coordinate mean?
> In the left half-plane, off-axis: $s = -\gamma/2 \pm i\omega_1$. Real part = decay rate (distance from the axis = stability margin), imaginary part = ringing frequency. Crossing into the right half-plane = oscillation that grows — the loop is unstable.

# Connections

- [[Transfer Functions and Bode Plots]] — H(s) on the imaginary axis is the measured response
- [[Linear ODE Systems]] — same pole/eigenvalue story in matrix form
- [[Fourier Transform]] — the s = iω boundary case for signals that neither grow nor start
- [[Driven Damped Harmonic Oscillator]] — the canonical worked example of poles = resonances

---
Source: Boas, *Mathematical Methods in the Physical Sciences*, Ch. 8 §8–10
