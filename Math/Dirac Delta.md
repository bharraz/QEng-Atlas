#math

**δ(x) is the machine that evaluates a function at a point when integrated against it** — an infinitely tall, infinitely narrow spike of unit area. It only means anything under an integral; treat it as a rule, not a function.

# Reference

**Defining property:**
$$
\int f(x)\,\delta(x-a)\, dx = f(a)
$$

**Composition rule** — zeros of the argument each contribute, weighted by the slope there:
$$
\delta(f(x)) = \sum_i \frac{\delta(x-x_i)}{|f'(x_i)|}, \qquad \text{so } \delta(ax) = \frac{\delta(x)}{|a|}
$$
This is where Jacobians in density-of-states and lineshape calculations come from.

**3D:** $\delta^3(\mathbf{r}) = \delta(x)\delta(y)\delta(z)$; in curvilinear coordinates divide by the volume-element factor, e.g. $\delta^3(\mathbf{r}-\mathbf{r}_0) = \frac{1}{r^2\sin\theta}\delta(r-r_0)\delta(\theta-\theta_0)\delta(\phi-\phi_0)$. The one to memorize: $\nabla^2\frac{1}{r} = -4\pi\,\delta^3(\mathbf{r})$ — point charges, Green's functions of Poisson.

**As a limit of sequences** (all unit-area, width → 0): Gaussian $\frac{1}{\sigma\sqrt{2\pi}}e^{-x^2/2\sigma^2}$, Lorentzian $\frac{\epsilon/\pi}{x^2+\epsilon^2}$, sinc $\frac{\sin(Nx)}{\pi x}$. The sinc form is why long pulses have narrow spectra.

**Fourier representation** (used constantly):
$$
\delta(x) = \frac{1}{2\pi}\int_{-\infty}^{\infty} e^{ikx}\, dk
$$
— this is the completeness/orthogonality statement of plane waves, and the step that collapses one integral in every convolution-theorem and Fermi-golden-rule derivation.

> [!question]- A resonance condition sits inside an integral as $\delta(E_f - E_i - \hbar\omega)$ with $E_f$ depending on $k$. What does the delta actually do?
> It picks out the $k$ satisfying the resonance and pays a Jacobian $1/|dE_f/dk|$ — that factor *is* the density of states. The composition rule $\delta(f(x)) = \sum \delta(x-x_i)/|f'(x_i)|$ is the whole mechanism.

# Connections

- [[Fourier Transform]] — δ ↔ 1 is the anchor pair; the exponential representation above
- [[Green's Functions]] — G is defined as the response to a delta source
- [[Divergence]] — ∇·(r̂/r²) = 4πδ³, the point-charge identity
- [[Convolution]] — delta is the identity element: f∗δ = f

---
Source: Griffiths, *Introduction to Electrodynamics*, §1.5; Arfken & Weber Ch. 1
