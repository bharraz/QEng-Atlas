#optics

**$M^2$ says how many times faster your real beam diverges than an ideal Gaussian with the same waist** — it multiplies the waist–divergence product, and it never improves with passive optics.

# Reference

$$
w_0\,\theta = M^2\,\frac{\lambda}{\pi}, \qquad w(z) = w_0\sqrt{1 + \left(\frac{M^2 \lambda z}{\pi w_0^2}\right)^2}
$$

A real beam propagates like a Gaussian with an *embedded* effective wavelength $M^2\lambda$. Consequences: focused spot from a given lens is $M^2\times$ bigger, and single-mode fiber or cavity coupling caps out — roughly, coupling efficiency $\lesssim 1/M^2$ since only the fundamental-mode content couples.

**Measurement (ISO 11146):** focus the beam with a lens, measure width at ~10 points through the focus (several $z_R$ each side), fit the hyperbola above for $w_0$, $z_0$, $M^2$ simultaneously. Widths must be **second-moment** ($4\sigma$) widths — camera with background carefully subtracted; a knife edge works but underestimates wings.

**Gotchas:**
- Never quote $M^2$ from a single far-field measurement — you need waist *and* divergence.
- Second moments are hypersensitive to baseline offset in the wings (a few counts of background across a big sensor can double your $M^2$).
- $M^2 \ge 1$, equality only for pure TEM$_{00}$; single-mode diode lasers ~1.1–1.3, multimode pump diodes 10–100s. Astigmatic beams get separate $M_x^2$, $M_y^2$.

> [!question]- Why can't a telescope, aperture, or any lens system reduce $M^2$?
> $M^2$ is proportional to the beam's phase-space area (étendue for coherent beams), which linear ABCD optics preserves — a lens trades waist against divergence but their product is invariant. Only losing the offending light (spatial filter through a pinhole, coupling into single-mode fiber) "improves" it — by throwing power away.

# Connections

- [[Gaussian Beams]] — the $M^2 = 1$ ideal whose formulas this generalizes with $\lambda \to M^2\lambda$
- [[Mode Matching]] — $M^2 > 1$ is exactly the higher-order-mode content that won't couple
- [[Higher-Order Beam Modes]] — $M^2$ of a pure TEM$_{mn}$ is $2m{+}1$ ($x$) and $2n{+}1$ ($y$); mixtures average
- [[Optical Fibers and Fiber Coupling]] — the single-mode fiber as the ultimate spatial filter

---
Source: Siegman, "How to (Maybe) Measure Laser Beam Quality," OSA TOPS Vol. 17 (1998)
