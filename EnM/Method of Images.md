#EnM

**Replace a conductor with a fictitious charge that reproduces the boundary condition — uniqueness guarantees the fields in your region are exact.** The conductor's induced surface charge really does act, in your half of space, like a mirror charge.

# Reference

**Grounded plane** — charge $q$ at height $d$: image $-q$ at $-d$.
$$
V(\mathbf{r}) = \frac{q}{4\pi\varepsilon_0}\left(\frac{1}{|\mathbf{r}-\mathbf{d}|} - \frac{1}{|\mathbf{r}+\mathbf{d}|}\right), \qquad F = -\frac{q^2}{4\pi\varepsilon_0 (2d)^2}
$$
Always attractive; the induced surface charge integrates to exactly $-q$.

**Grounded sphere** (radius $R$, charge at distance $a$): image $q' = -qR/a$ at distance $R^2/a$ from the center — the one-liner worth memorizing.

**When it works:** when a small set of point charges happens to make the boundary an equipotential. Planes, spheres, wedges of angle $\pi/n$ (finite image sets), parallel planes (infinite image ladder). It's a guess validated by uniqueness, not a general algorithm.

**Trap-electrode intuition:** an ion at distance $d$ from an electrode surface *is* the image problem — it induces $-q$ worth of surface charge and feels the image attraction. Moving ion ⇒ moving image ⇒ **induced currents in the electrodes**: this is how ions couple to trap circuitry (pickup detection, resistive cooling) and, with lossy electrodes, where anomalous heating enters. Also why "grounded" electrode surfaces with patch potentials still push the ion around: the boundary condition is whatever the surface actually is, not what the schematic says.

> [!question]- An ion oscillates at frequency $\omega$ a distance $d$ above an electrode. Why does the electrode circuit see a current?
> The induced image/surface charge must track the ion, so charge $\sim q\,\delta x/d$ sloshes through the electrode's connection to ground each cycle — an induced current $\propto q\dot{x}/d$. Load that with a resonant circuit and you can detect or damp the motion.

# Connections

- [[Electrostatic Potential and Poisson Equation]] — the uniqueness theorem that makes the trick legal
- [[Paul Traps]] — electrode boundary conditions, induced charges, ion–electrode coupling
- [[Multipole Expansion]] — the complementary far-from-source expansion
- [[Capacitance and Inductance]] — image method computes wire-over-ground-plane capacitance

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 3.2
