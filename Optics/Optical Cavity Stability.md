#optics

**A two-mirror cavity supports a confined Gaussian mode iff $0 \le g_1 g_2 \le 1$, with $g_i = 1 - L/R_i$** — stability means a ray (and the beam's $q$) reproduces itself instead of walking off the mirrors.

# Reference

$$
g_i = 1 - \frac{L}{R_i}, \qquad 0 \le g_1 g_2 \le 1
$$

$L$ = mirror separation (m); $R_i$ = radius of curvature of mirror $i$ (m, positive for concave); $g_i$ = dimensionless stability parameter, essentially "how strongly this mirror refocuses relative to how far the beam had to travel." $g = 1$ is a flat mirror (no refocusing), $g = 0$ means $R = L$ (mirror exactly at the focus), $g < 0$ means the beam over-focuses before returning. The product $g_1g_2$ is what matters because stability is a round-trip property, and the boundaries $0$ and $1$ are where the round trip stops being a stable orbit.

Equivalent to the round-trip ABCD matrix having $|A+D| \le 2$ (bounded ray orbits). The stable Gaussian mode is the $q$ that maps to itself in one round trip; its waist for a symmetric cavity ($R_1 = R_2 = R$):

$$
w_0^2 = \frac{L\lambda}{2\pi}\sqrt{\frac{2R}{L} - 1}
$$

with the waist at center and mode size on the mirrors growing as you approach instability.

| Geometry | $g_1g_2$ | Character |
|---|---|---|
| Planar ($R = \infty$) | 1 | Marginal — huge mode, alignment-critical |
| Confocal ($R = L$) | 0 | Center of the diagram — most forgiving, transverse modes degenerate in pairs |
| Concentric ($R = L/2$) | 1 | Marginal — tiny waist, blows up on the mirrors |
| Hemispherical (flat + $R \gtrsim L$) | ~0–1 | Common lab choice: waist on the flat mirror |

**Edge cases are traps:** planar, confocal, and concentric all sit *on* boundaries or degeneracies — real cavities are built slightly off these points (e.g. near-confocal) so the mode is well-defined and transverse modes are split, not accidentally degenerate.

**Transverse mode spacing** comes with the geometry: $\Delta\nu_{\rm trans} = \frac{\mathrm{FSR}}{\pi}\arccos(\pm\sqrt{g_1 g_2})$ — measure it on a scan and you've measured your $g_1g_2$.

> [!question]- Your cavity's transmission gets progressively more misalignment-sensitive and the spots on the mirrors grow as you lengthen it toward $L = R_1 + R_2$. Why?
> You're approaching the concentric stability edge $g_1g_2 \to 1$: the eigenmode's mirror spot size diverges and the mode axis becomes hypersensitive to mirror tilt (the axis passes through the two centers of curvature, which are nearly coincident). Stability isn't binary in practice — the margin sets alignment tolerance.

# Connections

- [[Fabry-Perot Cavity]] — stability gives the mode; finesse and FSR give the spectrum on top of it
- [[Gaussian Beams]] — the self-reproducing $q$ defines waist and spot sizes from pure geometry
- [[Ray Transfer Matrices]] — $|A+D| \le 2$ round-trip criterion is the same statement
- [[Higher-Order Beam Modes]] — $g_1g_2$ sets their frequency splitting via the Gouy phase

---
Source: Siegman, *Lasers*, Ch. 19
