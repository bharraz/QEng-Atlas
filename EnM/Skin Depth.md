#EnM

**AC fields only penetrate a conductor to a depth δ before eddy currents cancel them** — so current crowds into a thin surface layer, and the effective cross-section of every wire shrinks as frequency rises.

# Reference

For a good conductor ($\sigma \gg \omega\epsilon$):

$$
\delta = \sqrt{\frac{2}{\mu\sigma\omega}}
$$

$\delta$ = skin depth (m), the $1/e$ decay length of field amplitude into the metal; $\mu = \mu_r\mu_0$ = permeability (H/m) — magnetic metals have $\mu_r \sim 10^3$–$10^5$, which shrinks $\delta$ dramatically and is why steel shields at low frequency where copper cannot; $\sigma$ = conductivity (S/m); $\omega = 2\pi f$ = angular frequency (rad/s). Fields decay as $e^{-z/\delta}$ with a phase lag of one radian per skin depth (amplitude and phase are locked because the wave is diffusive, not propagating).

All three parameters enter as inverse square roots, so $\delta \propto 1/\sqrt{f}$: every factor of 100 in frequency costs a factor of 10 in penetration.

**Copper lookup table** ($\delta \approx 66\,\text{mm}/\sqrt{f/\text{Hz}}$):

| Frequency | δ in copper |
|---|---|
| 60 Hz | 8.5 mm |
| 10 kHz | 0.66 mm |
| 1 MHz | 65 μm |
| 100 MHz | 6.6 μm |
| 1 GHz | 2 μm |

**Consequences:**
- **RF resistance rises as √f** — current uses only a δ-thick shell, so $R_{AC} \approx R_{DC}\,(r/2\delta)$ for a wire of radius $r \gg \delta$. This sets conductor loss in coax and limits Q in coils; silver plating works because only the surface matters.
- **Shielding**: a shield attenuates by ~8.7 dB per skin depth of thickness (plus reflection loss). At 1 MHz, 0.5 mm of copper is ~8δ — excellent. At 60 Hz it's 0.06δ — nearly transparent, which is why low-frequency magnetic fields are the hard shielding case.
- Litz wire beats skin effect below ~1 MHz by braiding insulated strands thinner than δ.

> [!question]- Why does a copper box that kills 100 MHz interference do nothing for 60 Hz magnetic pickup?
> δ(60 Hz) = 8.5 mm — far thicker than the wall, so the field walks through with negligible attenuation and there's little reflection loss for near-field B. You need flux diversion (mu-metal) or smaller loop area, not more copper.

# Connections

- [[Electromagnetic Shielding]] — absorption loss is e^{-t/δ}; skin depth decides what a given wall thickness can block
- [[Plasma Frequency and Drude Model]] — where σ(ω) comes from; skin depth is the low-frequency limit of the metal's complex refractive index
- [[Transmission Lines]] — skin-effect resistance is the dominant √f loss term in coax
- [[LC Resonators]] — coil Q is capped by AC resistance of a δ-thick current shell

---
Source: Jackson, *Classical Electrodynamics*, §5.18 & §8.1
