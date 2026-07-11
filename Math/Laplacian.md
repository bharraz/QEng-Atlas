#math

**∇² measures how f at a point compares to its neighborhood average** — $\nabla^2 f > 0$ means f sits below the average of its surroundings (a local dip). It's div of grad: net outflow of the gradient field.

# Reference

$$
\nabla^2 f = \nabla\cdot(\nabla f) = \frac{\partial^2 f}{\partial x^2} + \frac{\partial^2 f}{\partial y^2} + \frac{\partial^2 f}{\partial z^2}
$$

Quantitatively: the average of $f$ over a small sphere of radius $\epsilon$ exceeds $f$ at the center by $\frac{\epsilon^2}{6}\nabla^2 f + O(\epsilon^4)$.

**Cylindrical and spherical** (full table in [[Curvilinear Coordinates]]):
$$
\nabla^2 f = \frac{1}{s}\frac{\partial}{\partial s}\!\left(s\frac{\partial f}{\partial s}\right) + \frac{1}{s^2}\frac{\partial^2 f}{\partial \phi^2} + \frac{\partial^2 f}{\partial z^2}
$$
$$
\nabla^2 f = \frac{1}{r^2}\frac{\partial}{\partial r}\!\left(r^2\frac{\partial f}{\partial r}\right) + \frac{1}{r^2\sin\theta}\frac{\partial}{\partial\theta}\!\left(\sin\theta\frac{\partial f}{\partial\theta}\right) + \frac{1}{r^2\sin^2\theta}\frac{\partial^2 f}{\partial\phi^2}
$$
Radial shortcut in spherical: $\frac{1}{r^2}\partial_r(r^2 \partial_r f) = \frac{1}{r}\partial_r^2(rf)$ — the substitution $u = rf$ that makes hydrogen's radial equation 1D.

**Where it runs the show:** Laplace/Poisson $\nabla^2 V = -\rho/\varepsilon_0$; the wave equation $\nabla^2 f = \frac{1}{c^2}\partial_t^2 f$; diffusion $\partial_t f = D\nabla^2 f$; kinetic energy $-\frac{\hbar^2}{2m}\nabla^2$ in Schrödinger. Harmonic functions ($\nabla^2 f = 0$) equal their neighborhood average exactly — hence no interior extrema, hence Earnshaw's theorem killing static 3D traps.

> [!question]- Why can't you trap a charged particle with static fields alone?
> A trap needs a potential minimum in empty space, i.e. $V$ below its neighborhood average — but in vacuum $\nabla^2 V = 0$, so $V$ exactly equals its neighborhood average everywhere. No minima (Earnshaw). Paul traps dodge this with time-dependent fields.

# Connections

- [[Electrostatic Potential and Poisson Equation]] — ∇²V = −ρ/ε₀ and its uniqueness machinery
- [[Electromagnetic Wave Equation]] — the Laplacian is the spatial half of the wave operator
- [[Curvilinear Coordinates]] — the full coordinate table
- [[Separation of Variables]] — how ∇² actually gets solved in practice
- [[Divergence]] — ∇² = div grad, the composition that defines it

---
Source: Griffiths, *Introduction to Electrodynamics*, §1.2.7 & §3.1
