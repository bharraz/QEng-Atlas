#optics

**In an anisotropic crystal the refractive index depends on polarization** — one axis sees $n_o$, the orthogonal one $n_e$, so the two components accumulate different phase. Every waveplate, PM fiber, and Pockels cell is this one fact, engineered.

# Reference

Uniaxial crystal: ordinary ray (polarization ⊥ optic axis) sees $n_o$ regardless of propagation direction; extraordinary ray sees $n_e(\theta)$ interpolating between $n_o$ (along axis) and $n_e$ (perpendicular). Accumulated retardance over length $L$:
$$
\Gamma = \frac{2\pi}{\lambda}\,(n_e - n_o)\,L
$$

| Crystal | $n_o$ | $n_e$ | note |
|---|---|---|---|
| Quartz | 1.544 | 1.553 | weakly positive — thin waveplates |
| Calcite | 1.658 | 1.486 | strongly negative — polarizers, displacers |
| LiNbO₃ | 2.29 | 2.20 | plus Pockels effect — EOMs |

**Walk-off:** for the extraordinary ray, $\mathbf{S} \nparallel \mathbf{k}$ — energy walks sideways (∼degrees in calcite) even at normal incidence. This is how beam-displacing polarizers work, and why tightly focused beams through thick birefringent optics come out ugly.

**Stress birefringence — the accidental waveplate.** Isotropic glass under stress becomes birefringent. Over-torqued mirror mounts, squeezed vacuum-window seals, and pinched fiber all quietly rotate your polarization; if your "clean" polarization drifts with temperature or mounting torque, suspect this before anything exotic. (PM fiber turns the bug into a feature: built-in stress rods pin the axes.)

> [!question]- Why does a tilted birefringent plate change its retardance?
> Tilting changes both the path length through the plate and the angle to the optic axis, hence $n_e(\theta)$. That's the knob you turn to trim a waveplate to exact quarter/half retardance — and why a multi-order plate is so temperature- and angle-touchy.

# Connections

- [[Waveplates]] — cut birefringence to exactly $\Gamma = \pi$ or $\pi/2$ and you have the standard polarization tools
- [[Jones Calculus]] — retarder matrices are how birefringent elements compose on paper
- [[Electro-Optic Modulator]] — Pockels effect = voltage-controlled birefringence
- [[Optical Fibers and Fiber Coupling]] — PM fiber is deliberate stress birefringence; launch on-axis or beat between the axes

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 6 (polarization optics)
