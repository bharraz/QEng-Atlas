#quantum-optics #AMO #ions

**A trapped ion emits its photon in all directions, so a lens beside the trap collects only a few percent of it; put the ion between two mirrors instead and one optical mode — the cavity mode — receives a fraction $2C/(2C+1)$ of the emission, set by the cooperativity $C$, and the photon leaves through one mirror already in a single spatial mode that couples into an optical fiber.** This is how an ion's quantum state is handed to a photon, for single-photon sources and for entangling ions in separate traps.

# Reference

**Free space versus cavity.** A lens of numerical aperture NA captures the fraction $(1 - \cos\theta)/2$, with $\sin\theta = \mathrm{NA}$, of an isotropic emitter: about 4% at NA 0.4 and 10% at NA 0.6 ([[Numerical Aperture and Spot Size]]), before the further loss of coupling into a single-mode fiber. With a cavity, the probability that the photon reaches the fiber is

$$
\eta = \frac{2C}{2C+1}\cdot\frac{\kappa_\text{out}}{\kappa}\cdot\eta_\text{path}
$$

- $C = g^2/\kappa\Gamma$ — cooperativity ([[Cavity QED]]): fraction $2C/(2C+1)$ of the emission enters the mode
- $g$, $\Gamma$ — ion–mode coupling (rad/s) and the ion's free-space emission rate (s⁻¹)
- $\kappa$ — total cavity field decay rate (s⁻¹)
- $\kappa_\text{out}$ — the part of $\kappa$ through the output mirror (s⁻¹)
- $\eta_\text{path}$ — mode matching into the fiber and optical losses after the cavity

The rest of $\kappa$ is the other mirror's transmission plus absorption and scatter in both mirrors, so a single-sided cavity (one mirror far more transmissive than the other) is needed for $\kappa_\text{out}/\kappa$ near 1.

**What sets $C$ for an ion.** $C \propto \mathcal F/w_0^2$ for finesse $\mathcal F$ and mode waist $w_0$, independent of the cavity length ([[Cavity QED]]); shorter cavities raise $g$, and smaller waists and higher finesse raise $C$. Both push dielectric mirror surfaces toward the ion, and dielectrics near an ion:
- charge up (from UV light and photoelectrons);
- shift the trap's RF null (the point where the trapping RF field vanishes);
- add micromotion and heating ([[Paul Traps]]).

Ion cavities therefore keep the mirrors farther from the ion than neutral-atom cavities do — millimetres to centimetres for conventional mirrors, a few hundred micrometres for mirrors on laser-machined fiber tips — and usually reach $C$ of order one, with $g$ below $\Gamma$, rather than strong coupling. A long cavity reaches its $C$ with low $\kappa$, so its photons are long (duration $\gtrsim 1/\kappa$) and the repetition rate is limited accordingly.

**Picture:** the mirrors act as a collector that reuses the same small solid angle many times. The mode intercepts only a fraction $\sim \lambda^2/w_0^2$ of the ion's emission on one pass, but the light passes the ion a number of times proportional to $\mathcal F$, and $C$ is roughly the product.

**Generating the photon: a cavity-assisted Raman transition.** The photon is not produced by simple decay into the cavity. A laser drives a [[Raman Transitions|Raman transition]] through a short-lived excited level $|e\rangle$, with the cavity supplying the second leg:

- the drive laser couples the initial level to $|e\rangle$ with Rabi frequency $\Omega$
- the cavity couples $|e\rangle$ to a long-lived final level with coupling $g$
- both are detuned by $\Delta$ from $|e\rangle$, with the two-photon resonance condition met

In ⁴⁰Ca⁺, for example, the drive is at 393 nm (S₁/₂ → P₃/₂) and the cavity photon at 854 nm (P₃/₂ → D₅/₂). The scheme gives control the plain decay does not:

| Property of the photon | Set by |
|---|---|
| frequency | the drive laser (two-photon resonance), so it can be tuned onto the cavity resonance |
| temporal shape | the drive pulse, through the effective coupling $g\Omega/2\Delta$; shaped photons from two nodes can be made to overlap for interference |
| exactly one photon | the ion ends in a long-lived level the drive does not address |
| polarization entangled with the ion | two Raman paths ending in different Zeeman sublevels, emitting different polarizations |
| efficiency | still $C$: detuning suppresses free-space scattering and cavity emission by the same factor |

With $\Delta = 0$ and a slowly ramped drive, the same transfer is vacuum-stimulated Raman adiabatic passage, STIRAP with the cavity vacuum as one beam ([[EIT and STIRAP]]).

**Where the ion sits.** The cavity field is a standing wave with a Gaussian profile:

$$
g(\mathbf r) = g_0 \cos(kz)\, e^{-(x^2+y^2)/w_0^2}
$$

- $g_0$ — coupling at an antinode on the cavity axis (rad/s)
- $z$ — position along the cavity axis (m); $x, y$ — transverse position (m)
- $k = 2\pi/\lambda$ — wavenumber of the cavity light (m⁻¹)

The ion must sit at an antinode along the axis and on the axis transversely. Its motion along the axis averages $\cos^2(kz)$ over the ion's spread and lowers the effective $C$ — the cavity counterpart of the [[Lamb-Dicke Regime]].

**Two ions in one mode** act as one emitter in the bright Bell state, coupled with $\sqrt2\,g$, and decouple from the mode in the dark one; which Bell state is bright depends on the sign of $\cos(kz)$ at each ion ([[Superradiance and Subradiance]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| cavity transmission linewidth, or ring-down time | $\kappa$; with the free spectral range (FSR), the finesse ([[Fabry-Perot Cavity]]) |
| photon count rate as the ion is moved along the axis (by shifting the trap with DC electrodes) | the standing wave: maxima locate antinodes, and the fringe contrast measures how well the ion is localized (temperature, micromotion) |
| count rate as the ion is moved transversely | the mode waist and the ion's overlap with it |
| arrival-time histogram of photons after each drive pulse | the photon's temporal shape; its integral, corrected for detector and path losses, gives the extraction efficiency |
| $g^{(2)}(0)$ of the output ([[Photon Statistics and g2]]) | whether one photon is emitted per pulse ($g^{(2)}(0) \approx 0$) |
| photon polarization, conditioned on the ion's measured final state | the ion–photon entanglement fidelity |
| micromotion before and after UV exposure or ion loading | whether the mirrors are charging |

**Entangling ions in separate traps.** Each ion emits a photon entangled with it; the two photons meet on a beamsplitter, and particular detector coincidences herald an entangled ion pair — a Bell-state measurement made by [[Hong-Ou-Mandel Interference]]. Detecting both photons makes the success probability scale as $\eta^2$, which is why extraction efficiency sets networking rates; schemes that detect a single photon scale as $\eta$ but need phase-stable optical paths. Free-space collection with a high-NA lens is the main alternative to a cavity: a simpler trap, lower efficiency per photon, and photons whose duration is set by the excited-state lifetime rather than by a drive pulse.

**Wavelength.** Cavity photons come out at an ionic transition (854 nm for Ca⁺), where optical fiber loses about 3 dB/km against about 0.2 dB/km at 1550 nm. Long links convert the photon to a telecom wavelength by difference-frequency generation in a nonlinear waveguide, which preserves its quantum state.

> [!question]- Why don't ion experiments shrink the cavity until $g$ exceeds $\Gamma$, as neutral-atom experiments do?
> Shrinking the cavity brings dielectric mirrors close to the ion, where charging and stray fields push it off the RF null and heat it. And a photon source does not need strong coupling: the extraction probability depends on $C$, not on $g/\Gamma$, and $C \propto \mathcal F/w_0^2$ does not depend on the cavity length. A longer, high-finesse cavity with a small waist reaches the same $C$ with the mirrors kept away from the ion; the cost is a lower $\kappa$, hence longer photons.

# Connections

- [[Cavity QED]] — $g$, $\kappa$, $\Gamma$, $C$ and the coupling regimes
- [[Purcell Effect]] — why the mode receives $2C/(2C+1)$ of the emission
- [[Raman Transitions]] — the two-leg transition that generates the photon
- [[EIT and STIRAP]] — the adiabatic version, with the cavity vacuum as one beam
- [[Paul Traps]] — why dielectrics near the ion cause micromotion and heating
- [[Lamb-Dicke Regime]] — ion localization relative to a standing wave
- [[Superradiance and Subradiance]] — two ions as bright and dark states of one mode
- [[Hong-Ou-Mandel Interference]] — the two-photon interference that heralds remote entanglement
- [[Photon Statistics and g2]] — checking that the output is one photon per pulse
- [[Numerical Aperture and Spot Size]] — the free-space alternative
- [[Remote Entanglement and Quantum Networks]] — heralding schemes and repeaters across platforms

---
Source: T. E. Northup & R. Blatt, "Quantum information transfer using photons," *Nature Photon.* 8, 356 (2014); A. Reiserer & G. Rempe, "Cavity-based quantum networks with single atoms and optical photons," *Rev. Mod. Phys.* 87, 1379 (2015); M. Keller et al., *Nature* 431, 1075 (2004); A. Stute et al., *Nature* 485, 482 (2012)
