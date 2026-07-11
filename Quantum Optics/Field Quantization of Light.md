#quantum-optics

**Expand the EM field in cavity modes and each mode amplitude obeys a harmonic-oscillator Hamiltonian — quantize those oscillators and light is quantized.** A photon is one quantum of excitation of a delocalized mode, not a bullet flying through space.

# Reference

Single mode (volume $V$, polarization $\hat\epsilon$), from the mode expansion of $\mathbf A$:

$$
\hat{\mathbf E} = E_0\, \hat\epsilon \left( a\, e^{i(kz-\omega t)} + a^\dagger e^{-i(kz-\omega t)} \right), \qquad E_0 = \sqrt{\frac{\hbar\omega}{2\epsilon_0 V}}
$$

where $E_0$ is the zero-point field amplitude and each mode carries $H = \hbar\omega(a^\dagger a + \tfrac12)$. Full field = sum over $(\mathbf k, \hat\epsilon)$.

**Quadratures** $X_1 = (a+a^\dagger)/2$, $X_2 = (a-a^\dagger)/2i$ are the mode's dimensionless position and momentum; $[X_1, X_2] = i/2$ gives $\Delta X_1 \Delta X_2 \ge 1/4$ — field amplitude and phase can't both be sharp.

**Numbers** ($\lambda = 1\,\mu$m): $E_0 \approx 0.1$ V/m for $V = 1$ cm³, but $\sim$3 kV/m for a $(10\,\mu\text{m})^3$ mode. The $1/\sqrt{V}$ is why cavity QED wants tiny mode volumes — atom-field coupling is $g = d E_0/\hbar$.

**Photon = excitation, not bullet:** a single photon occupies the entire mode. "Where is the photon" only means something once you build a localized wavepacket from a superposition of modes.

> [!question]- Why does $E_0$ scale as $1/\sqrt{V}$?
> The zero-point energy per mode is fixed at $\hbar\omega/2$, and $\epsilon_0 E_0^2 V \sim \hbar\omega/2$ — the same half-quantum of energy spread over a bigger volume means a weaker field per photon.

# Connections

- [[Second Quantization]] — the general machinery this note applies to the EM field
- [[Vacuum Fluctuations]] — $\langle E \rangle = 0$ but $\langle E^2 \rangle = E_0^2$: the empty mode still shakes
- [[Quantum Harmonic Oscillator]] — each mode is exactly this, with $x, p \to X_1, X_2$
- [[Cavity QED]] — where the $1/\sqrt{V}$ in $E_0$ becomes an engineering target

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 2
