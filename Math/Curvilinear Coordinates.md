#math

**The lookup card: vector calculus in cylindrical and spherical, with all the metric factors in the right places.** The unit vectors move with the point — that's where every extra term comes from.

# Reference

**Cylindrical $(s, \phi, z)$** — $s$ = distance from axis. $dV = s\, ds\, d\phi\, dz$; $d\mathbf{l} = ds\,\hat{s} + s\,d\phi\,\hat{\phi} + dz\,\hat{z}$.

$$
\nabla f = \frac{\partial f}{\partial s}\hat{s} + \frac{1}{s}\frac{\partial f}{\partial \phi}\hat{\phi} + \frac{\partial f}{\partial z}\hat{z}
$$
$$
\nabla\cdot\mathbf{A} = \frac{1}{s}\frac{\partial (s A_s)}{\partial s} + \frac{1}{s}\frac{\partial A_\phi}{\partial \phi} + \frac{\partial A_z}{\partial z}
$$
$$
\nabla\times\mathbf{A} = \left(\frac{1}{s}\frac{\partial A_z}{\partial \phi} - \frac{\partial A_\phi}{\partial z}\right)\hat{s} + \left(\frac{\partial A_s}{\partial z} - \frac{\partial A_z}{\partial s}\right)\hat{\phi} + \frac{1}{s}\left(\frac{\partial (s A_\phi)}{\partial s} - \frac{\partial A_s}{\partial \phi}\right)\hat{z}
$$
$$
\nabla^2 f = \frac{1}{s}\frac{\partial}{\partial s}\!\left(s\frac{\partial f}{\partial s}\right) + \frac{1}{s^2}\frac{\partial^2 f}{\partial \phi^2} + \frac{\partial^2 f}{\partial z^2}
$$

**Spherical $(r, \theta, \phi)$** — $\theta$ = polar angle from $z$ (physics convention!). $dV = r^2\sin\theta\, dr\, d\theta\, d\phi$; $d\mathbf{l} = dr\,\hat{r} + r\,d\theta\,\hat{\theta} + r\sin\theta\,d\phi\,\hat{\phi}$.

$$
\nabla f = \frac{\partial f}{\partial r}\hat{r} + \frac{1}{r}\frac{\partial f}{\partial \theta}\hat{\theta} + \frac{1}{r\sin\theta}\frac{\partial f}{\partial \phi}\hat{\phi}
$$
$$
\nabla\cdot\mathbf{A} = \frac{1}{r^2}\frac{\partial (r^2 A_r)}{\partial r} + \frac{1}{r\sin\theta}\frac{\partial(\sin\theta\, A_\theta)}{\partial \theta} + \frac{1}{r\sin\theta}\frac{\partial A_\phi}{\partial \phi}
$$
$$
\nabla\times\mathbf{A} = \frac{1}{r\sin\theta}\left(\frac{\partial(\sin\theta\, A_\phi)}{\partial\theta} - \frac{\partial A_\theta}{\partial\phi}\right)\hat{r} + \frac{1}{r}\left(\frac{1}{\sin\theta}\frac{\partial A_r}{\partial\phi} - \frac{\partial(r A_\phi)}{\partial r}\right)\hat{\theta} + \frac{1}{r}\left(\frac{\partial(r A_\theta)}{\partial r} - \frac{\partial A_r}{\partial\theta}\right)\hat{\phi}
$$
$$
\nabla^2 f = \frac{1}{r^2}\frac{\partial}{\partial r}\!\left(r^2\frac{\partial f}{\partial r}\right) + \frac{1}{r^2\sin\theta}\frac{\partial}{\partial\theta}\!\left(\sin\theta\frac{\partial f}{\partial\theta}\right) + \frac{1}{r^2\sin^2\theta}\frac{\partial^2 f}{\partial\phi^2}
$$

**Gotchas:** unit vectors are position-dependent — never pull $\hat{r}, \hat{\phi}$ through a derivative or integrate them componentwise without converting to Cartesian. $\nabla^2$ of a *vector* field is not the Laplacian of each curvilinear component; use $\nabla^2\mathbf{A} = \nabla(\nabla\cdot\mathbf{A}) - \nabla\times(\nabla\times\mathbf{A})$. Math texts swap $\theta \leftrightarrow \phi$.

> [!question]- Where do the $1/s$ and $1/r\sin\theta$ factors in the gradient come from?
> The gradient's component along a direction is $df$ per unit *length*, and a step $d\phi$ moves you an arc length $s\,d\phi$ (or $r\sin\theta\,d\phi$) — the metric factor converts coordinate change to physical distance.

# Connections

- [[Gradient]] — what the metric factors mean physically
- [[Laplacian]] — the radial-part tricks and where each form gets used
- [[Bessel Functions]] — what separation in cylindrical coordinates spits out
- [[Legendre Polynomials and Spherical Harmonics]] — what separation in spherical spits out
- [[Separation of Variables]] — why the coordinate system must match the boundary

---
Source: Griffiths, *Introduction to Electrodynamics*, front cover / §1.4
