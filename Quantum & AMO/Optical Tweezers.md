#AMO

**A red-detuned, tightly focused laser beam is a trap for a single atom: the AC Stark shift turns "more intensity" into "lower potential energy," so the focus becomes a 3D well a few hundred µK deep.** One tweezer is a trap; a thousand of them, imaged and rearranged, are the register of neutral-atom quantum computing — and the whole platform's character (stochastic loading, µK depths, state-dependent potentials) follows from the trap physics on this page.

# Reference

**Trap potential from the AC Stark shift** (far-detuned atom — [[Dipole Approximation]], [[Stark Effect and Light Shifts]]):

$$U_{\text{dip}}(\mathbf r) = -\frac{3\pi c^2}{2\omega_0^3}\frac{\Gamma}{\Delta}\,I(\mathbf r), \qquad \Gamma_{\text{sc}}(\mathbf r) = \frac{3\pi c^2}{2\hbar\omega_0^3}\left(\frac{\Gamma}{\Delta}\right)^2 I(\mathbf r),$$

$U_{\text{dip}}$ = trap potential energy (J; usually quoted as depth $U_0/k_B$ in µK or mK); $\Gamma_{\text{sc}}$ = photon scattering rate (s⁻¹); $I(\mathbf r)$ = local intensity (W/m²); $\omega_0$ = atomic resonance frequency and $\Gamma$ = its natural linewidth (both rad/s), fixed by the atom; $\Delta = \omega_L - \omega_0$ = detuning (rad/s), the one free design parameter. Red detuning ($\Delta < 0$) makes $U_{\text{dip}} < 0$ at high intensity: the intensity maximum becomes a potential minimum.

The prefactor $3\pi c^2/2\omega_0^3$ is just the atom's resonant cross-section bookkeeping; everything actionable is in $I/\Delta$ versus $I/\Delta^2$. The ratio is the design rule:

$$\frac{\hbar\Gamma_{\text{sc}}}{|U_{\text{dip}}|} = \frac{\Gamma}{|\Delta|}$$

— at fixed depth, more detuning (paid for with more power, $U \propto I/\Delta$) buys proportionally less scattering. Hence FORTs run hundreds of nm from resonance (852/1064 nm for Rb/Cs on D lines at 780/852 nm... i.e. the *trap* wavelength sits far red of *every* strong transition), where an atom scatters a photon every ~seconds instead of every µs.

**Geometry** ([[Gaussian Beams]], [[Numerical Aperture and Spot Size]]): $w_0 \approx \lambda/\pi\mathrm{NA}$, $I_0 = 2P/\pi w_0^2$, $z_R = \pi w_0^2/\lambda$. NA 0.5–0.9 pushes $w_0$ to 0.5–1 µm; a few mW then gives $U_0/k_B \sim$ 0.1–1 mK. **Trap frequencies** from the harmonic expansion:

$$\omega_r = \sqrt{\frac{4U_0}{m w_0^2}}, \qquad \omega_z = \sqrt{\frac{2U_0}{m z_R^2}}, \qquad \frac{\omega_z}{\omega_r} = \frac{\lambda}{\sqrt{2}\,\pi w_0}$$

$\omega_r, \omega_z$ = radial and axial trap frequencies (rad/s); $U_0$ = trap depth (J); $m$ = atomic mass (kg); $w_0$ = beam waist (m); $z_R = \pi w_0^2/\lambda$ = Rayleigh range (m). These are just $\omega = \sqrt{\text{curvature}/m}$ with the curvature of the intensity profile: the trap is stiff over $w_0$ radially but only over $z_R \gg w_0$ axially. Note $\omega \propto \sqrt{U_0}/w_0 \propto \sqrt{P}/w_0^2$ — tightening the focus buys trap frequency far faster than raising power does.

— typically $\omega_r/2\pi \sim$ 20–150 kHz, $\omega_z$ ~5× softer: the trap is a cigar along the beam, because intensity falls off over $w_0$ radially but over the much longer $z_R$ axially. The softness of these traps relative to ion traps (MHz) is the platform's defining constraint: Lamb-Dicke parameters are marginal, thermal motion matters, and everything wants ground-state cooling.

**Orders of magnitude to carry:** depth mK ≫ atom temperature (10–50 µK post-loading) ≫ trap-frequency scale (µK-equivalent ~ kHz×ħ/k_B ~ 50 nK per kHz... i.e. $\bar n \sim 10$ thermally); photon recoil per scattering event heats by $T_{\text{rec}} \sim 200$ nK — a budget of ~10³–10⁴ scattering events before boiling out, which is what "seconds of trap lifetime at big detuning" means.

## From one trap to a machine

- **Arrays** are made by splitting one beam: **AODs** (RF tones → one trap per tone, µs-fast steering, but 1D-ish and frequency-crowded — see [[Acousto-Optic Modulator]]) and **SLMs** (holographic, arbitrary 2D/3D geometry, ~ms update). The standard machine uses SLM for the static array + AOD for the moving tweezer that rearranges.
- **Loading is stochastic by construction:** in a µm-scale trap, light-assisted collisions during loading eject atoms *in pairs*, so occupancy parity collapses to 0 or 1 (~50–60%; enhanced loading schemes reach ~90%). Determinism is restored afterwards: fluorescence-image the array (which sites won?), then move winners into the target pattern — **rearrangement, not loading, is what makes defect-free arrays of hundreds to ~1000 atoms possible**, and it must beat the vacuum-limited loss rate (another [[Vacuum Engineering|UHV]] argument).
- **Imaging an atom you'd rather not heat:** collect fluorescence while simultaneously cooling (PGC/Λ-enhanced gray molasses in the trap), and mind that trap light shifts the imaging transition — image either in a magic trap or strobed (trap and imaging light alternated faster than $\omega_r$).
- **State-dependence is both bug and feature.** $U \propto \alpha(\lambda)$ differs between internal states: qubit levels see differential light shifts (dephasing from intensity noise — the tweezer version of the [[Raman Transitions|Raman]] $\delta_{\text{AC}}$ problem), solved at **magic wavelengths** where two states' polarizabilities cross. The catastrophic case: **Rydberg states have negative polarizability** at standard trap wavelengths (a free-electron response) — the trap *expels* them. Standard practice is blinking the traps off during the µs Rydberg pulse ([[Rydberg Atoms and Blockade]]); the refined fix is trapping at a wavelength magic between ground and Rydberg, or bottle-beam (dark) traps that hold both.
- **Heating budget:** photon scattering sets the floor; the usual dominant excess is **parametric heating** from intensity noise at $2\omega_{\text{trap}}$ (modulating the spring constant — energy doubles per fluctuation cycle at that frequency, see [[Noise Spectroscopy and Filter Functions|the filter-function logic]] applied classically) and pointing noise at $\omega_{\text{trap}}$. Hence low-RIN lasers, intensity servos ([[Control Beyond PID|feedback]] on a photodiode), and quiet mounts.
- **Thermometry without absorption imaging:** release-and-recapture (drop the trap for µs, recapture probability vs time fits $T$) or sideband spectroscopy once resolved ($\omega_r > \Gamma_{\text{eff}}$ — the same [[Resolved Sideband Cooling|red/blue asymmetry]] as ions).

> [!question]- Why is the axial trap frequency always softer than the radial one, and why does that matter?
> $\omega_z/\omega_r = \lambda/(\sqrt{2}\pi w_0)$, and diffraction never lets $w_0$ go much below $\sim\lambda/2$, so the ratio is stuck near ~1/4–1/6. Physically, the intensity curvature radially is set by $w_0$ but axially by $z_R = \pi w_0^2/\lambda \gg w_0$ — the same diffraction that limits the waist stretches the focus. Consequences: axial ground-state cooling is the hard direction; axial position spread dominates Rydberg-gate Doppler dephasing and atom-atom distance fluctuations ($C_6/r^6$ noise); and imaging depth-of-focus vs axial motion is a real alignment budget.

# Connections

- [[Stark Effect and Light Shifts]] — the trapping potential *is* the AC Stark shift; magic wavelengths
- [[Numerical Aperture and Spot Size]] — the optics that set $w_0$, hence everything
- [[Gaussian Beams]] — waist, Rayleigh range, intensity profile
- [[Rydberg Atoms and Blockade]] — what the array is *for*; the anti-trapped Rydberg problem
- [[Magneto-Optical Traps]] — the reservoir the tweezers load from
- [[Resolved Sideband Cooling]] / [[Lamb-Dicke Regime]] — ground-state cooling in a 100 kHz trap is marginal-η territory
- [[Acousto-Optic Modulator]] — array generation and the moving rearrangement tweezer
- [[Paul Traps]] — the contrast case: eV-deep, MHz-stiff, charged
- [[Binomial Errors in State Detection]] — 0-vs-1 imaging discrimination

---
Source: Grimm, Weidemüller & Ovchinnikov, "Optical dipole traps for neutral atoms," *Adv. At. Mol. Opt. Phys.* 42, 95 (2000); Kaufman & Ni, "Quantum science with optical tweezer arrays," *Nat. Phys.* 17, 1324 (2021)
