#math

**Decompose a signal into the oscillations it's made of** — the FT asks "how much $e^{i\omega t}$ is in $f(t)$?" for every $\omega$. Narrow in time ⇔ wide in frequency, always.

# Reference

**Convention (declare yours, factors of 2π breed here):**
$$
\tilde{f}(\omega) = \int_{-\infty}^{\infty} f(t)\, e^{-i\omega t}\, dt, \qquad
f(t) = \frac{1}{2\pi}\int_{-\infty}^{\infty} \tilde{f}(\omega)\, e^{i\omega t}\, d\omega
$$
Physicists usually put the $2\pi$ on the inverse (or split $1/\sqrt{2\pi}$ each way); with $f$ in Hz the $2\pi$ vanishes. Spatial convention flips sign: $e^{+i\mathbf{k}\cdot\mathbf{r} - i\omega t}$ for a forward-going wave.

**Key pairs** (the ones you actually look up):

| $f(t)$ | $\tilde{f}(\omega)$ | note |
|---|---|---|
| $e^{-t^2/2\sigma^2}$ | $\sigma\sqrt{2\pi}\, e^{-\sigma^2\omega^2/2}$ | Gaussian ↔ Gaussian; widths reciprocal |
| $e^{-t/\tau}\,\Theta(t)$ | $\dfrac{\tau}{1+i\omega\tau}$ | decay ↔ Lorentzian ($\lvert\tilde f\rvert^2$); natural linewidth |
| top-hat, width $T$ | $T\,\mathrm{sinc}(\omega T/2)$ | square pulse ↔ sinc; Rabi lineshape |
| $\delta(t)$ | $1$ | impulse contains all frequencies |
| $e^{i\omega_0 t}$ | $2\pi\,\delta(\omega-\omega_0)$ | pure tone |

Modulation shifts: $f(t)e^{i\omega_0 t} \leftrightarrow \tilde{f}(\omega-\omega_0)$. Derivatives multiply: $\dot{f} \leftrightarrow i\omega\tilde{f}$.

**Parseval/Plancherel:** $\int |f(t)|^2 dt = \frac{1}{2\pi}\int |\tilde{f}(\omega)|^2 d\omega$ — energy is basis-independent.

**Time–bandwidth:** $\Delta t\, \Delta\omega \geq \tfrac{1}{2}$ (Gaussian saturates it). Same inequality is quantum uncertainty, laser linewidth vs coherence time, and Fourier-limited pulses. A $\tau$-long measurement can't resolve features narrower than $\sim 1/\tau$.

> [!question]- Why does an exponentially decaying oscillation have a Lorentzian spectrum, and what sets its FWHM?
> $e^{i\omega_0 t - t/\tau}\Theta(t)$ transforms to $\tau/(1 + i(\omega-\omega_0)\tau)$; its modulus squared is a Lorentzian centered at $\omega_0$ with FWHM $\Delta\omega = 2/\tau$. Faster decay = broader line — the natural-linewidth mechanism.

# Connections

- [[Convolution]] — multiplication in one domain is convolution in the other
- [[Power Spectral Density]] — |FT|² per unit time, the measurable spectrum
- [[Laser Linewidth]] — decay ↔ Lorentzian pair in the wild
- [[Dirac Delta]] — the anchor pairs and the completeness integral
- [[Fourier Series]] — the periodic special case; FT is its continuum limit
- [[Bandwidth]]

---
Source: Boas, *Mathematical Methods in the Physical Sciences*, Ch. 7
