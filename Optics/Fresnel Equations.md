#optics

**Reflection and transmission amplitudes at an interface follow from demanding the EM boundary conditions ($E_\parallel$, $H_\parallel$ continuous) hold at the surface** — the two polarizations satisfy them differently, hence Brewster physics.

# Reference

For incidence $\theta_i$, refraction $\theta_t$ (Snell: $n_1\sin\theta_i = n_2\sin\theta_t$):

$$
r_s = \frac{n_1\cos\theta_i - n_2\cos\theta_t}{n_1\cos\theta_i + n_2\cos\theta_t}, \qquad
r_p = \frac{n_2\cos\theta_i - n_1\cos\theta_t}{n_2\cos\theta_i + n_1\cos\theta_t}
$$

($s$ = E-field perpendicular to plane of incidence, $p$ = in-plane.) Power: $R = |r|^2$, $T = 1 - R$.

**Normal incidence:**
$$
R = \left(\frac{n_1 - n_2}{n_1 + n_2}\right)^2
$$
**Glass ($n=1.5$): 4% per surface** — the number behind ghost beams, etalon fringes, and why an uncoated window costs 8%. Silicon ($n \approx 3.5$): ~31%.

**Phase flips:** going into denser medium ($n_1 < n_2$), $r_s < 0$ — π phase flip for s-pol at all angles; $r_p$ changes sign at Brewster. External vs internal reflection differ — sign conventions bite, fix them before chasing a sign in an interferometer.

**Angle behavior:** $R_p \to 0$ at Brewster's angle then rises steeply; $R_s$ rises monotonically; both → 1 at grazing (why any surface mirrors at grazing incidence). Beyond critical angle (internal): $|r| = 1$ with polarization-dependent phase — the basis of Fresnel-rhomb waveplates.

> [!question]- Why does p-polarized reflection vanish at one angle but s never does?
> At Brewster incidence the refracted and would-be reflected rays are perpendicular; the transmitted medium's dipoles oscillate along the p-reflected direction and dipoles don't radiate along their own axis. s-dipoles are always perpendicular to the reflection direction, so they always radiate into it.

# Connections

- [[Electromagnetic Boundary Conditions]] — the two continuity equations these are solved from
- [[Total Internal Reflection and Brewster Angle]] — the two special angles, with the lab uses
- [[Dielectrics and Polarizability]] — where $n$ comes from microscopically
- [[Optical Fibers and Fiber Coupling]] — the 4%-per-tip reflection that APC connectors defeat

---
Source: Hecht, *Optics*, Ch. 4
