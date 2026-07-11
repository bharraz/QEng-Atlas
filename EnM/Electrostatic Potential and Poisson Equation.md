#EnM

**Static E is curl-free, so it's a gradient: $\mathbf{E}=-\nabla V$, and Gauss's law becomes Poisson's equation — all of electrostatics is one scalar PDE plus boundary conditions.** Uniqueness means any solution you find, by whatever trick, is *the* solution.

# Reference

$$
\nabla^2 V = -\frac{\rho}{\varepsilon_0}, \qquad \nabla^2 V = 0 \ \text{(charge-free: Laplace)}
$$

**Uniqueness theorem:** specify $V$ on the boundaries (or total charge on each conductor) and the interior solution is unique. This is the license behind [[Method of Images]], separation of variables, relaxation solvers, and guessing.

**Laplace solutions have no interior extrema** — $V$ at any point equals its average over any surrounding sphere. Consequences:
- **Earnshaw's theorem:** no stable electrostatic trap for a charge in free space; every "minimum" is a saddle. This is *why* Paul traps need RF ([[Paul Traps]]) and Penning traps need a B field.
- Numerically: Laplace smooths — relax toward the neighbor average and you converge.
- Potentials from distant electrodes are always smooth, gentle functions near your ion; only low-order multipole terms survive at the center.

**Boundary-value intuition for electrode design:** conductors are equipotentials; field lines meet them normally; sharp features concentrate field ($E\sim V/r_{\text{curvature}}$ — the lightning-rod effect, and the breakdown-voltage limiter in tight trap geometries).

> [!question]- Why can't a clever arrangement of static electrodes ever hold an ion in stable 3D equilibrium?
> Stability in all three directions needs $V$ to have a true minimum, i.e. $\nabla^2 V>0$ there — but Laplace demands $\nabla^2 V=0$ in vacuum: curvatures must sum to zero, so confinement in two axes forces anti-confinement in the third. Hence RF pseudopotentials.

# Connections

- [[Laplacian]] — the operator and its average-value interpretation
- [[Method of Images]] — solution-by-guessing licensed by uniqueness
- [[Paul Traps]] — Earnshaw's theorem is the founding constraint of ion trapping
- [[Multipole Expansion]] — the systematic form of "smooth potential near the center"
- [[Green's Functions]] — Poisson's equation solved by superposing point-charge responses

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 2.3 & 3.1
