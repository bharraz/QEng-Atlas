#quantum-optics

**Empty modes still fluctuate: each carries zero-point energy $\hbar\omega/2$ and quadrature variance $1/4$, and this "nothing" pushes on things you can measure.** The vacuum is the ground state of the field oscillators, and ground states of oscillators are Gaussians, not zeros.

# Reference

$$
\langle 0|\hat E|0\rangle = 0, \qquad \langle 0|\hat E^2|0\rangle = E_0^2 = \frac{\hbar\omega}{2\epsilon_0 V}, \qquad \langle \Delta X_1^2\rangle = \langle \Delta X_2^2\rangle = \tfrac14
$$

— the symmetric minimum-uncertainty circle at the phase-space origin.

**Measurable consequences:**

| Effect | Mechanism |
|---|---|
| Spontaneous emission | emission rate $\propto (n+1)$; the $+1$ is vacuum "stimulating" decay into empty modes |
| Lamb shift | electron jitter in the vacuum field splits $2S_{1/2}$–$2P_{1/2}$ by $\sim$1 GHz |
| Casimir force | plates restrict the mode set → net inward pressure |
| Shot noise | vacuum entering every open port of a detection scheme sets the noise floor |

**Vacuum noise is the shot-noise origin:** homodyne with nothing at the signal port still shows variance $1/4$ — the "shot-noise level" is a vacuum quadrature measurement. [[Squeezed States]] squash the circle below $1/4$ in one quadrature (paying in the other), which is why squeezing means sub-shot-noise.

> [!question]- The $\hbar\omega/2$ per mode is unobservable — so what makes vacuum *fluctuations* observable?
> Differences and correlations, never the absolute offset: change the mode structure (cavity, plates → Purcell, Casimir) or couple a dipole to the fluctuating field (spontaneous emission, Lamb shift). You measure gradients of the zero-point energy and its noise, not the energy itself.

# Connections

- [[Spontaneous Emission and Linewidth]] — the everyday lab manifestation: decay triggered by empty modes
- [[Squeezed States]] — reshaping the vacuum uncertainty circle; sub-vacuum noise in one quadrature
- [[Field Quantization of Light]] — where $E_0$ and the half-quantum come from
- [[Photodetection and Shot Noise]] — the detection-side face of the same fluctuations
- [[Purcell Effect]] — engineer the vacuum mode density, change the decay rate

---
Source: Milonni, *The Quantum Vacuum*, Ch. 2–3
