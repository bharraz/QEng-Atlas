#optics

**A lens gathers light from a point at its focus only within a cone; the half-angle $\theta$ of that cone, multiplied by the refractive index $n$ of the medium at the focus, is the numerical aperture, $\mathrm{NA} = n\sin\theta$.** That one number sets the smallest spot the lens can focus a beam to, how far along the beam that spot stays in focus, and what fraction of an emitter's light the lens collects — so focusing a laser to a small spot and collecting the light of a single emitter — an atom, ion, molecule, or color center — come down to the same lens property.

# Reference

$$
\mathrm{NA} = n\sin\theta \approx \frac{D}{2f} \quad (\text{small angles, } n = 1)
$$

- $\theta$ — half-angle of the cone of light at the focus (rad): set by the lens aperture
- $n$ — refractive index of the medium at the focus (dimensionless): 1 in air or vacuum
- $D$ — diameter of the lens's clear aperture, or of the beam filling it (m)
- $f$ — focal length (m)

Lens catalogues often quote the f-number $N = f/D$ instead; for small angles $\mathrm{NA} \approx 1/(2N)$, so an f/2 lens has NA ≈ 0.25.

**Why the $n$ is there:** Snell's law keeps $n\sin\theta$ unchanged when light crosses a flat interface, so a flat vacuum window or cover slip does not change the NA; it is the conserved measure of the cone. It is also the largest transverse wavevector the lens passes, in units of the vacuum wavevector: $k_\perp^{\max} = k_0\,\mathrm{NA}$, with $k_0 = 2\pi/\lambda$ and $\lambda$ the vacuum wavelength.

**Picture:** a focused spot is the interference pattern of all the plane waves the lens sends toward the focus. A wider cone supplies a wider spread of transverse wavevectors, $\Delta k_\perp \approx k_0\,\mathrm{NA}$, and Fourier reciprocity ($\Delta x\,\Delta k_\perp \gtrsim 1$) then allows a narrower spot:

$$\Delta x \sim \frac{\lambda}{2\,\mathrm{NA}}.$$

Run the light backwards and the same cone is what the lens accepts from an emitter at the focus.

**What the NA sets** (scale given for λ = 400 nm and NA = 0.5):

| Quantity | Formula | Scales as | At λ = 400 nm, NA 0.5 |
|---|---|---|---|
| resolvable separation: first dark ring of the Airy pattern of a uniformly filled lens (Rayleigh criterion) | $0.61\,\lambda/\mathrm{NA}$ | $1/\mathrm{NA}$ | 0.49 µm |
| waist ($1/e^2$ radius) of a focused Gaussian beam | $\lambda/(\pi\,\mathrm{NA_{used}})$ | $1/\mathrm{NA}$ | 0.25 µm |
| Rayleigh range: distance over which the beam stays within $\sqrt2\,w_0$ | $\lambda/(\pi\,\mathrm{NA_{used}}^2)$ | $1/\mathrm{NA}^2$ | 0.51 µm |
| fraction of an isotropic emitter's light collected | $(1 - \cos\theta)/2$ | $\approx \mathrm{NA}^2/4$ | 6.7% |

Across common atomic and ionic transition wavelengths (370–500 nm) at NA 0.5, the waist is 0.24–0.32 µm and the Rayleigh range 0.47–0.64 µm. At NA ≳ 0.5 the Gaussian-beam formulas are paraxial estimates; the real focus is somewhat larger and, for linear polarization, slightly elongated along the polarization. Neighbouring emitters in ion chains and atom arrays sit a few micrometres apart, so above NA ≈ 0.3 the ideal spot is already small compared with the spacing, and what limits individual addressing is the light outside the ideal spot (see the question below).

**NA of the lens vs NA the beam uses.** A Gaussian beam fills only the angles it is sent in with. Focusing a collimated beam with a lens of focal length $f$ gives

$$
w_0 = \frac{\lambda f}{\pi w_{\text{in}}} = \frac{\lambda}{\pi\,\theta_{\text{div}}}
$$

- $w_{\text{in}}$ — $1/e^2$ radius of the collimated beam at the lens (m)
- $w_0$ — $1/e^2$ radius of the focused waist (m)
- $\theta_{\text{div}}$ — far-field divergence half-angle of the focused beam (rad)

i.e. $w_0 \approx \lambda/(\pi\,\mathrm{NA_{used}})$ where $\mathrm{NA_{used}} = w_{\text{in}}/f$ is set by how much of the lens the beam fills ([[Gaussian Beams]]). **Underfilling a high-NA objective wastes its NA** — the lens delivers only the angles you send into it. Overfilling clips the beam on the aperture, adds Airy rings, and loses power. The beam radius at the lens is set with a telescope ([[Telescopes and Beam Expanders]]).

**The axial cost.** Depth of focus shrinks *quadratically* while the spot shrinks linearly:

$$z_R = \frac{\pi w_0^2}{\lambda} \sim \frac{\lambda}{\mathrm{NA}^2}.$$

Halving the spot quarters the focal depth, so high-NA optics demand micrometre-level focus adjustment and axial stability. Any interface between lens and focus (a vacuum window, for example) adds spherical aberration that grows steeply with NA, which is why objectives used through a window are specified for its thickness ("corrected for a 4 mm window").

**Collection is the same number run backwards.** The fraction of an isotropic emitter's photons captured by a lens of half-angle $\theta$ is the solid-angle fraction

$$\eta = \frac{1 - \cos\theta}{2} \approx \frac{\mathrm{NA}^2}{4} \quad (\text{small } \theta, \; n=1).$$

NA 0.1 collects 0.25%; NA 0.6 collects ~10%. A dipole emitter is not isotropic: with the lens looking perpendicular to the dipole axis, it collects up to 1.5× more than the isotropic estimate at small NA. Photon-counting measurements (single atoms, ions, or color centers) use the highest NA the vacuum geometry allows, because the photon count — and with it the readout error ([[Binomial Errors in State Detection]]) — improves as NA². A cavity around the emitter is the alternative when no lens can collect enough ([[Ion-Cavity Coupling]]).

**Immersion and the $n$:** the $n$ in $n\sin\theta$ is the index at the *focus side*. Oil or water immersion (n = 1.5/1.33) exceeds the NA < 1 limit of a lens in air. Solid immersion lenses on diamond (n = 2.4) are how NV collection overcomes total internal reflection: without one, most of the light inside the diamond strikes the surface beyond the critical angle and never leaves.

**Fibers:** a step-index fiber guides light that meets the core–cladding boundary beyond the critical angle for [[Total Internal Reflection and Brewster Angle|total internal reflection]]; translated to the cone outside the fiber, that acceptance is $\mathrm{NA} = \sqrt{n_{\text{core}}^2 - n_{\text{clad}}^2}$.
- For a single-mode fiber the quoted NA is only the acceptance limit: the light that couples is the fiber's own mode, so choose the coupling lens from the mode-field diameter, not from the NA.
- A collimated beam of radius $w_{\text{in}}$ is matched to a mode of radius $w_m$ (half the mode-field diameter) by a lens of focal length $f = \pi w_{\text{in}} w_m/\lambda$ ([[Optical Fibers and Fiber Coupling]]).
- Matching the focused waist to the mode is a [[Mode Matching|mode-matching]] problem, and coupling efficiency collapses when the focusing NA is wrong in either direction.

**Imaging onto a camera:** the image of a point emitter is the Airy pattern, of radius $0.61\lambda/\mathrm{NA}$ at the object, magnified by the imaging magnification $M$. For the camera to resolve it, that radius should span at least two pixels: $M \gtrsim 2p\,\mathrm{NA}/(0.61\lambda)$ for pixel size $p$.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| beam radius at the lens, and the lens focal length | $\mathrm{NA_{used}} = w_{\text{in}}/f$, hence the expected waist |
| focused spot size (knife edge, or a second objective imaging the focus onto a camera) compared with $\lambda/(\pi\,\mathrm{NA_{used}})$ | a larger spot means aberration (window, tilt, lens used at the wrong distances) or a beam with $M^2 > 1$ ([[Beam Quality M2]]) |
| camera image of a point emitter (a single atom, ion, or color center, or a sub-resolution bead) | the point-spread function directly: its width gives the effective imaging NA, its asymmetry the aberrations |
| detected count rate compared with scattering rate × $(1-\cos\theta)/2$ × detector efficiency | how much of the collection cone reaches the detector |

> [!question]- When one emitter in an array (an ion in a chain, an atom in a tweezer array) is addressed with a focused beam, what limits the crosstalk on its neighbour — the Gaussian spot size or something else?
> Rarely the ideal spot. A perfect Gaussian with $w_0 = 0.5$ µm has negligible intensity 5 µm away; measured crosstalk of $10^{-2}$–$10^{-3}$ comes from departures from a Gaussian: Airy rings from truncation at the aperture, aberrations (window, misalignment) that put light into the shoulders of the spot, and scattered light. Higher NA sharpens the peak, but crosstalk is set by the wings — reduced by beam shaping, aberration correction, and sometimes composite pulses that cancel the effect of the residual light.

# Connections

- [[Gaussian Beams]] — waist, Rayleigh range, and divergence of the focused beam
- [[Telescopes and Beam Expanders]] — setting $w_{\text{in}}$ to fill the objective: the knob that realizes the NA
- [[Diffraction]] — the Airy pattern of a circular aperture
- [[Higher-Order Beam Modes]] — what aberrations and truncation admix into the focus
- [[Optical Cavity Stability]] — the same Gaussian-beam parameters in resonator language
- [[Optical Fibers and Fiber Coupling]] — fiber acceptance NA and the mode-field diameter
- [[Mode Matching]] — coupling a focused beam into a fiber or cavity mode
- [[Total Internal Reflection and Brewster Angle]] — the critical angle behind fiber NA and trapped light in high-index hosts
- [[Binomial Errors in State Detection]] — why collection efficiency sets readout fidelity
- [[Ion-Cavity Coupling]] — collecting with a cavity instead of a lens
- [[Beam Quality M2]] — imperfect beams focus to $M^2$-times-larger spots at the same NA

---
Source: Novotny & Hecht, *Principles of Nano-Optics*, Ch. 3–4; Siegman, *Lasers*, Ch. 17
