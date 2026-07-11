#math

**The polynomial correction factors that turn a Gaussian into the harmonic oscillator's excited states** — QHO eigenfunctions are $\psi_n \propto H_n(x)\, e^{-x^2/2}$: Gaussian envelope, Hermite wiggles, $n$ nodes.

# Reference

**First few:**
$$
H_0 = 1, \quad H_1 = 2x, \quad H_2 = 4x^2 - 2, \quad H_3 = 8x^3 - 12x
$$
Parity alternates: $H_n(-x) = (-1)^n H_n(x)$.

**Recursion** (how you actually generate them):
$$
H_{n+1}(x) = 2x\, H_n(x) - 2n\, H_{n-1}(x), \qquad H_n'(x) = 2n\, H_{n-1}(x)
$$
Generating function: $e^{2xt - t^2} = \sum_n H_n(x)\, t^n/n!$.

**Orthogonality — Gaussian weight** (Sturm-Liouville on $(-\infty,\infty)$ with $w = e^{-x^2}$):
$$
\int_{-\infty}^{\infty} H_n(x)\, H_m(x)\, e^{-x^2} dx = 2^n n!\sqrt{\pi}\; \delta_{nm}
$$

**QHO eigenfunctions** (with $\xi = x/x_0$, $x_0 = \sqrt{\hbar/m\omega}$):
$$
\psi_n(x) = \frac{1}{\sqrt{2^n n!}}\left(\frac{m\omega}{\pi\hbar}\right)^{1/4} H_n(\xi)\, e^{-\xi^2/2}
$$
The weight function is the ground state squared — the polynomials encode how excitation reshapes the Gaussian. Highest-power term dominates at large $n$: the wavefunction piles up at the turning points, recovering the classical distribution.

**Same math, optical version:** Hermite–Gaussian beam modes TEM$_{mn}$ have transverse profiles $H_m(\sqrt{2}x/w)H_n(\sqrt{2}y/w)\, e^{-(x^2+y^2)/w^2}$ — the paraxial wave equation is the 2D Schrödinger equation in disguise, so cavities emit oscillator eigenfunctions in space. A misaligned or mismatched Gaussian couples into TEM$_{10}$/TEM$_{20}$ exactly like a displaced oscillator populates $n=1, 2$.

> [!question]- Why do QHO eigenfunctions and laser cavity transverse modes share the same functional form?
> The paraxial Helmholtz equation maps onto the time-dependent Schrödinger equation ($z \leftrightarrow t$), whose transverse confinement is harmonic for a stable cavity — same eigenvalue problem, same Hermite-Gaussian solutions. Mode order maps to oscillator quantum number, including the mode-dependent Gouy phase ↔ energy.

# Connections

- [[Quantum Harmonic Oscillator]] — these are its position-space eigenfunctions
- [[Higher-Order Beam Modes]] — TEM_mn profiles are 2D Hermite-Gaussians
- [[Sturm-Liouville Theory]] — the e^{−x²}-weight family in the polynomial table
- [[Ladder Operators]] — the algebraic route that avoids touching these entirely

---
Source: Griffiths, *Introduction to Quantum Mechanics*, §2.3; Arfken Ch. 13
