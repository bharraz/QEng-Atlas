#optics

**Two special angles at an interface: beyond critical, everything reflects (with an evanescent tail); at Brewster, p-polarization transmits perfectly** — one makes fibers and prisms work, the other makes loss-free windows and polarization cleanup.

# Reference

**Critical angle** (internal, $n_1 > n_2$):
$$
\theta_c = \arcsin(n_2/n_1)
$$
Glass→air: **41.8°** — a 45° prism TIRs, which is why prism retroreflectors need no coating. Beyond $\theta_c$, $|r| = 1$ but the field extends into the low-index side as an evanescent wave, decay length
$$
d = \frac{\lambda}{2\pi\sqrt{n_1^2\sin^2\theta - n_2^2}} \sim \lambda/2\pi \text{ scale}
$$
Bring a second interface within a few decay lengths and power tunnels across (**frustrated TIR** — variable attenuators, fingerprint sensors, and the optical analogue of quantum tunneling). Anything touching a TIR surface (dust, oil, fingerprint) frustrates it — TIR surfaces must be clean.

**Brewster's angle:**
$$
\theta_B = \arctan(n_2/n_1)
$$
Air→glass: **56.3°**; at $\theta_B$, $R_p = 0$ exactly — reflected and refracted rays are perpendicular, and dipoles can't radiate along their axis. Reflected light at Brewster is purely s-polarized.

**Lab uses:** Brewster windows (intracavity elements with zero insertion loss for p — gas laser tubes, and why those lasers are polarized); Brewster-cut prisms and laser rods; cheap polarization filtering (a glass plate stack). The residual s-reflection ~15% per surface at $\theta_B$ makes stacked plates a usable polarizer.

> [!question]- A cavity needs an intracavity window with essentially zero loss. What orientation, and what does it cost you?
> Mount it at Brewster's angle for p-polarization: $R_p = 0$, no coating needed, no etalon effects (the s-reflection walks out of the mode). Cost: the cavity now lases/resonates only in p — you've hard-wired the polarization, and the window must be tilted, adding astigmatism to the mode.

# Connections

- [[Fresnel Equations]] — both angles are just features of $r_s(\theta), r_p(\theta)$
- [[Evanescent Waves]] — the field beyond critical angle: no average power flow unless frustrated
- [[Optical Fibers and Fiber Coupling]] — guiding is TIR at the core–cladding step
- [[Polarization of EM Waves]] — Brewster reflection as a polarization purifier

---
Source: Hecht, *Optics*, Ch. 4
