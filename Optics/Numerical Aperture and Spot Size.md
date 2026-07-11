#optics

**Numerical aperture measures the cone of angles a lens accepts or delivers, $\mathrm{NA} = n\sin\theta$, and it is the single number that sets both the smallest spot you can make and the largest solid angle of light you can collect.** Focusing tighter and collecting more photons are the same specification — which is why the same objective is fought over for addressing a single ion and for reading out its fluorescence.

# Reference

**Why angle is the currency:** a focused spot is an interference pattern built from all the plane-wave directions the lens delivers. The transverse wavevector spread available is $\Delta k_\perp \approx k\,\mathrm{NA}$, and Fourier reciprocity ($\Delta x\,\Delta k_\perp \gtrsim 1$) makes the spot size

$$\Delta x \sim \frac{\lambda}{2\,\mathrm{NA}}.$$

Everything else is prefactors depending on what "spot" means:

- **Airy pattern** (uniformly filled aperture): first dark ring at $r = 0.61\,\lambda/\mathrm{NA}$; two points are "resolved" at this separation (Rayleigh criterion).
- **Gaussian beam** (the lab case — see beam waist conventions): focusing a collimated beam of $1/e^2$ radius $w_{\text{in}}$ with a lens of focal length $f$ gives waist
$$w_0 = \frac{\lambda f}{\pi w_{\text{in}}} = \frac{\lambda}{\pi\,\theta_{\text{div}}},$$
i.e. $w_0 \approx \lambda/(\pi\,\mathrm{NA_{used}})$ where $\mathrm{NA_{used}} = w_{\text{in}}/f$ is set by how much of the lens you actually fill. **Underfilling a high-NA objective wastes its NA** — the lens delivers only the angles you send into it.

**The axial cost.** Depth of focus shrinks *quadratically* while the spot shrinks linearly:

$$z_R = \frac{\pi w_0^2}{\lambda} \sim \frac{\lambda}{\mathrm{NA}^2}.$$

Halving the spot quarters the focal depth — high-NA optics are unforgiving in alignment and axial stability, and any interface (vacuum window!) between lens and focus introduces spherical aberration that grows steeply with NA (hence objectives specified "with 4 mm window correction").

**Collection is the same number run backwards.** The fraction of a dipole's photons captured by a lens of half-angle $\theta$ is the solid-angle fraction

$$\eta = \frac{1 - \cos\theta}{2} \approx \frac{\mathrm{NA}^2}{4} \quad (\text{small } \theta, \; n=1).$$

NA 0.1 collects 0.25%; NA 0.6 collects ~10%. Photon-starved measurements (single-ion/NV readout) buy the highest NA that fits the vacuum geometry because $\eta$ pays quadratically, and readout error walks down with every collected photon (see state-detection statistics).

**Immersion and the $n$:** the $n$ in $n\sin\theta$ is the index at the *focus side*. Oil/water immersion (n = 1.5/1.33) beats the air ceiling of NA < 1; solid immersion lenses on diamond (n = 2.4) are how NV collection is rescued from total internal reflection.

**Fibers:** NA $= \sqrt{n_{\text{core}}^2 - n_{\text{clad}}^2}$ defines the acceptance cone for guiding; matching a free-space beam to a single-mode fiber is mode-matching the focused waist to the fiber's mode-field diameter — an NA-matching problem, and the reason coupling efficiency collapses when the focusing NA is wrong in either direction.

**Numbers to carry:** at 370–500 nm (ion/atom wavelengths), NA 0.5 gives $w_0 \sim 0.3\text{–}0.5$ µm — comfortably below typical few-µm ion spacings for individual addressing, with crosstalk set by the Airy wings and aberrations rather than the ideal spot. At NA 0.5, $z_R \sim 1$–2 µm: the ion must sit in focus to µm precision.

> [!question]- Individual addressing crosstalk on the neighboring ion is limited by what, in practice — the Gaussian spot size or something else?
> Rarely the ideal spot. A perfect Gaussian at $w_0 = 0.5$ µm has negligible intensity 5 µm away; measured crosstalk of $10^{-2}$–$10^{-3}$ comes from the *non-Gaussian* reality: Airy rings from aperture truncation, aberrations (window, misalignment) throwing light into shoulders, and scatter. High NA helps the peak, but crosstalk is won in the wings — beam-shaping, aberration correction, and sometimes composite pulses that echo out the residual light.

# Connections

- [[Telescopes and Beam Expanders]] — setting $w_{\text{in}}$ to fill the objective: the knob that realizes the NA
- [[Higher-Order Beam Modes]] — what aberrations and truncation admix into the focus
- [[Optical Cavity Stability]] — the same Gaussian-beam parameters in resonator language
- [[Binomial Errors in State Detection]] — why collection efficiency directly buys readout fidelity
- [[Beam Quality M2]] — imperfect beams focus to $M^2$-times-larger spots at the same NA

---
Source: Novotny & Hecht, *Principles of Nano-Optics*, Ch. 3–4; Siegman, *Lasers*, Ch. 17
