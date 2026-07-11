#math

**Guess a product solution and the PDE falls apart into ODEs** — if $\psi(x,t) = X(x)T(t)$, each factor's equation depends on only its own variable, so both sides must equal a constant. Those separation constants are the eigenvalues, and the boundary conditions quantize them.

# Reference

**The move**, on $\nabla^2\psi = \frac{1}{c^2}\partial_t^2\psi$ or Schrödinger or Laplace:
$$
\psi = X(x)Y(y)Z(z) \;\Rightarrow\; \frac{X''}{X} + \frac{Y''}{Y} + \frac{Z''}{Z} = \text{const}
$$
A function of $x$ alone equaling a function of $y, z$ alone forces each ratio to be constant: $X'' = -k_x^2 X$, etc. **Boundary conditions turn the constants discrete** — $X(0)=X(L)=0$ gives $k_x = n\pi/L$. That's mode quantization: cavity modes, particle in a box, drumheads, all the same step.

**Separating time from space** in any linear evolution equation gives $T \propto e^{-iEt/\hbar}$ (or $e^{i\omega t}$) and turns the PDE into an eigenvalue problem $H\psi = E\psi$ — stationary states *are* separation of variables.

**When it works:** the coordinate system must match the symmetry of the boundaries — the Helmholtz equation separates in only 11 coordinate systems (Cartesian, cylindrical, spherical, ...). Separating in spherical coordinates manufactures the special functions: $\phi \to e^{im\phi}$, $\theta \to$ Legendre, $r \to$ Bessel/spherical Bessel. Cylindrical gives Bessel $J_m$. The "special functions zoo" is just Laplacian + geometry.

**When it fails:** boundaries that don't fit a separable coordinate surface, non-separable potentials, coupling terms. Then: perturbation theory, numerics, or a smarter basis. General solution = superposition of the separated modes; match the remaining boundary/initial condition by Fourier-expanding in them.

> [!question]- Why must the separation "constant" actually be constant, and what does it become physically?
> After dividing by $XT$, one side depends only on $x$, the other only on $t$; vary $t$ holding $x$ fixed — the $x$ side can't change, so both equal a constant. That constant is the eigenvalue: energy for Schrödinger, $-k^2$ for Helmholtz — the mode label.

# Connections

- [[Sturm-Liouville Theory]] — guarantees the separated ODEs give orthogonal, complete eigenfunctions
- [[Cavity Modes]] — boundary conditions quantizing separation constants, in the lab
- [[Bessel Functions]] — what cylindrical separation produces
- [[Legendre Polynomials and Spherical Harmonics]] — what spherical separation produces
- [[Laplacian]] — the operator being separated, in every coordinate system

---
Source: Boas, *Mathematical Methods in the Physical Sciences*, Ch. 13
