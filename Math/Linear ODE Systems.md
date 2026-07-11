#math

**Any set of coupled linear ODEs is $\dot{\mathbf{x}} = A\mathbf{x}$, and the solution is $e^{At}\mathbf{x}_0$ — so solving it means diagonalizing $A$, and each eigenvalue is a mode with its own decay rate and frequency.** Turns dynamics into an eigenvalue problem.

# Reference

$$
\dot{\mathbf{x}} = A\mathbf{x} \;\Rightarrow\; \mathbf{x}(t) = e^{At}\mathbf{x}_0 = \sum_i c_i\, e^{\lambda_i t}\,\mathbf{v}_i
$$

where $\lambda_i, \mathbf{v}_i$ are eigenpairs of $A$ and $c_i$ come from expanding $\mathbf{x}_0$ in the eigenbasis. **Read stability off the eigenvalues:** $\mathrm{Re}\,\lambda < 0$ decays, $\mathrm{Re}\,\lambda > 0$ grows (system unstable if *any* eigenvalue does), $\mathrm{Im}\,\lambda$ oscillates. Complex $\lambda$ come in conjugate pairs for real $A$: damped ringing.

**Higher-order equations fold in:** $\ddot x + \gamma\dot x + \omega_0^2 x = 0$ becomes first-order in the state $(x, \dot x)$ — the companion-matrix trick. Its eigenvalues $\lambda = -\gamma/2 \pm \sqrt{\gamma^2/4 - \omega_0^2}$ reproduce underdamped/overdamped directly.

**Coupled modes = diagonalize:** coupled oscillators (ions in a chain, coupled cavities, RLC networks) look messy in physical coordinates; in the eigenbasis they are independent 1D problems. Mode frequencies = eigenvalues, mode shapes = eigenvectors, and you drive/cool/measure *modes*, not coordinates.

**Driven version** (variation of parameters — the Green's-function form):
$$
\dot{\mathbf{x}} = A\mathbf{x} + \mathbf{f}(t) \;\Rightarrow\; \mathbf{x}(t) = e^{At}\mathbf{x}_0 + \int_0^t e^{A(t-t')}\,\mathbf{f}(t')\,dt'
$$

**Defective $A$ gotcha:** repeated eigenvalue without enough eigenvectors → $t\,e^{\lambda t}$ terms. Critical damping is exactly this: the companion matrix at $\gamma = 2\omega_0$ is defective.

> [!question]- Why does critical damping produce a $t\,e^{-\gamma t/2}$ solution instead of two exponentials?
> At $\gamma = 2\omega_0$ the two eigenvalues merge and the matrix becomes defective — only one eigenvector survives, so one solution's worth of directions is missing. The Jordan block supplies the replacement: $t\,e^{\lambda t}$. Degenerate eigenvalues with a full eigenbasis (normal matrices) never do this.

# Connections

- [[Matrix Exponential]] — $e^{At}$ is the whole solution; diagonal case makes the mode picture literal
- [[Normal Modes of Ion Chains]] — the flagship application: diagonalize the coupling, get COM/stretch/…
- [[Diagonalization]] — when it works, when it fails (defective matrices), and why that's critical damping
- [[Laplace Transform]] — the other standard route: turns the same system into algebra in $s$

---
Source: Strogatz, *Nonlinear Dynamics and Chaos*, Ch. 5 (Linear systems)
