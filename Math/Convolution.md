#math

**Convolution is smearing: the output is the input blurred by the system's response to a single spike** — every linear time-invariant system does this, which is why one function (the impulse response) characterizes the whole box.

# Reference

$$
(f * g)(t) = \int_{-\infty}^{\infty} f(\tau)\, g(t-\tau)\, d\tau
$$
Commutative, associative; $f * \delta = f$; width of the result ≈ widths added (in quadrature for Gaussians: $\sigma^2 = \sigma_f^2 + \sigma_g^2$).

**Convolution theorem** — the reason anyone can compute these:
$$
\widetilde{f * g} = \tilde{f}\cdot\tilde{g}, \qquad \widetilde{f\cdot g} = \frac{1}{2\pi}\,\tilde{f} * \tilde{g}
$$
Convolution in time = multiplication in frequency, and vice versa. FFT-multiply-inverse-FFT beats direct integration for anything long.

**LTI systems:** output $y = h * x$ where $h$ is the impulse response; equivalently $\tilde{y}(\omega) = H(\omega)\tilde{x}(\omega)$. Filters multiply spectra; in time they smear.

**Instrument response:** every measured spectrum is (true spectrum) ∗ (instrument lineshape) — a laser scan convolves the atomic line with the laser lineshape; a spectrum analyzer convolves with its resolution bandwidth. Voigt profile = Lorentzian (natural) ∗ Gaussian (Doppler). **Deconvolution is ill-posed** — dividing by a small $H(\omega)$ amplifies noise; don't expect to recover what the instrument killed.

**The multiplication direction bites too:** a finite observation window multiplies the signal by a top-hat, so the spectrum gets convolved with a sinc — that's spectral leakage.

> [!question]- You measure a linewidth of 1.2 MHz with a laser whose own linewidth is 0.5 MHz (both Lorentzian). What's the true atomic linewidth?
> Lorentzian widths add under convolution: $\Gamma_{meas} = \Gamma_{atom} + \Gamma_{laser}$, so 0.7 MHz. (Gaussian widths add in quadrature instead — know which regime you're in.)

# Connections

- [[Fourier Transform]] — the convolution theorem is the workhorse property
- [[Green's Functions]] — the driven solution y = ∫G f is a convolution against the source
- [[Dirac Delta]] — the identity element; impulse response defined by it
- [[Laser Linewidth]] — measured lines are convolutions of source and instrument

---
Source: Boas, *Mathematical Methods in the Physical Sciences*, Ch. 8 §10; Bracewell, *The Fourier Transform and Its Applications*
