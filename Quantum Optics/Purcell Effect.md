#quantum-optics

**An excited atom decays by emitting into the electromagnetic modes around it, so its decay rate depends on how many modes are available at its frequency, and a cavity changes that number.** Fermi's golden rule says $\Gamma \propto \rho(\omega)$; a resonant cavity piles the density of states into a Lorentzian, enhancing decay on resonance and suppressing it off.

# Reference

Purcell factor for an emitter at an antinode, dipole aligned, on resonance:

$$
F_P = \frac{\Gamma_\mathrm{cav}}{\Gamma_\mathrm{free}} = \frac{3}{4\pi^2}\left(\frac{\lambda}{n}\right)^3 \frac{Q}{V}
$$

- $F_P$ — Purcell factor (dimensionless decay-rate enhancement)
- $\Gamma_\mathrm{cav}, \Gamma_\mathrm{free}$ — the emitter's decay rates with and without the cavity (s⁻¹)
- $\lambda$ — free-space emission wavelength (m)
- $n$ — refractive index, so $\lambda/n$ is the wavelength in the medium
- $Q = \omega/\kappa$ — cavity quality factor (dimensionless): optical cycles a photon survives; sets the mode-density peak width
- $V$ — mode volume (m³): the field's effective volume, $\int \epsilon|E|^2 dV / \max(\epsilon|E|^2)$

The structure is one factor of concentration in each domain: $(\lambda/n)^3/V$ concentrates the field in space, $Q$ concentrates the mode density in frequency, and $F_P$ is their product — halve $V$ or double $Q$ and you gain the same factor 2. Note $F_P = 2C$: Purcell enhancement is cooperativity expressed as a decay rate.

**Picture:** a cavity piles the electromagnetic modes into a narrow band, so emission into that band speeds up and emission outside it slows down.

**Both directions work.** Detuned cavity or photonic bandgap ⇒ $\rho(\omega)$ *below* free space ⇒ inhibited emission; excited atoms between close mirrors demonstrably live longer. The vacuum modes aren't a fixed backdrop — you can renovate them.

**The main practical benefit is directionality as well as speed:** the enhanced decay all goes into the one cavity mode, so the fraction of photons emitted into the collectable mode is

$$
\beta = \frac{F_P}{F_P + 1} = \frac{2C}{2C+1}
$$

versus a few percent to about 10% collected from free-space emission by a lens of [[Numerical Aperture and Spot Size|NA]] 0.4–0.6, before the further loss of coupling into a single-mode fiber. This is how ion-photon and atom-photon network nodes overcome the solid-angle problem ([[Ion-Cavity Coupling]]).

**Validity:** the formula assumes the emitter linewidth is narrower than the cavity's. For a broad emitter (room-temperature solid-state, Doppler-broadened vapor) the *emitter* linewidth replaces $Q$ — effectively use the smaller of the two, and $F_P$ collapses accordingly.

> [!question]- Why does a cavity with the same $Q$ but 10× smaller mode volume give 10× the Purcell factor, physically?
> The vacuum zero-point field per mode scales as $\mathcal{E}_0 = \sqrt{\hbar\omega/2\varepsilon_0 V}$ — squeezing the mode concentrates vacuum fluctuations at the atom, and spontaneous emission is stimulated emission by the vacuum.

# Connections

- [[Cavity QED]] — $F_P = 2C$; Purcell enhancement is what the bad-cavity regime still provides
- [[Spontaneous Emission and Linewidth]] — the free-space rate being modified
- [[Fermi's Golden Rule]] — the $\rho(E)$ dependence that makes the entire effect possible
- [[Vacuum Fluctuations]] — what the cavity is reshaping
- [[Superradiance and Subradiance]] — speeding up emission by correlating the emitters instead of reshaping the vacuum
- [[Ion-Cavity Coupling]] — the trapped-ion network node built on this enhancement

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 10
