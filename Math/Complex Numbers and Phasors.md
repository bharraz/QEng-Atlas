#math

**Replace $\cos\omega t$ with $e^{i\omega t}$, solve the linear system with algebra instead of trig, take the real part at the end** — legal because real linear systems commute with "take the real part," and every derivative becomes a multiplication by $i\omega$.

# Reference

**The Euler kit:**
$$
e^{i\theta} = \cos\theta + i\sin\theta, \qquad \cos\theta = \frac{e^{i\theta}+e^{-i\theta}}{2}, \qquad \sin\theta = \frac{e^{i\theta}-e^{-i\theta}}{2i}
$$
$|e^{i\theta}|=1$; multiplying by $e^{i\phi}$ rotates by $\phi$; $i = e^{i\pi/2}$ is "advance by 90°."

**Phasor recipe:** write the drive as $\mathrm{Re}[\tilde F e^{i\omega t}]$, assume response $\mathrm{Re}[\tilde x e^{i\omega t}]$, substitute — $d/dt \to i\omega$, so the ODE becomes complex algebra:
$$
(-\omega^2 + i\gamma\omega + \omega_0^2)\,\tilde x = \tilde F/m \;\Rightarrow\; \tilde x = \frac{\tilde F/m}{\omega_0^2-\omega^2 + i\gamma\omega}
$$
$|\tilde x|$ is the amplitude, $\arg\tilde x$ the phase lag — both in one complex number. Impedance analysis is this recipe with $V$ and $I$.

**When you must keep both exponentials:** the moment anything *nonlinear* happens. $\mathrm{Re}[\tilde A]\,\mathrm{Re}[\tilde B] \neq \mathrm{Re}[\tilde A\tilde B]$ — squaring, mixing, saturation, and detection all multiply signals, and the cross terms between $e^{+i\omega t}$ and $e^{-i\omega t}$ are where sum/difference frequencies and DC terms come from. Time-averaged power: $\langle P\rangle = \tfrac{1}{2}\mathrm{Re}[\tilde V\tilde I^{\,*}]$ — the ½ and the conjugate are both mandatory.

The $e^{-i2\omega t}$ term you drop in the rotating wave approximation is exactly the counter-rotating half of a cosine drive — RWA is phasor thinking applied to quantum dynamics.

> [!question]- Why can't you compute power by just multiplying two phasors?
> Multiplication is nonlinear, and phasors silently carry only the $e^{+i\omega t}$ half of the real signal. The product of two real signals contains cross terms ($2\omega$ and DC) that the naive phasor product misrepresents. The fix for time-averaged quantities is $\tfrac12\mathrm{Re}[\tilde A\tilde B^*]$; for actual mixing products, write out both exponentials.

# Connections

- [[Complex Impedance]] — the phasor recipe institutionalized: $Z_C = 1/i\omega C$, $Z_L = i\omega L$
- [[Rotating Wave Approximation]] — dropping the counter-rotating exponential; the quantum version of this note
- [[Driven Damped Harmonic Oscillator]] — the three-line phasor derivation above, unpacked
- [[Fourier Transform]] — phasors are the single-frequency slice of the full decomposition

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §1.7 (Impedance and reactance)
