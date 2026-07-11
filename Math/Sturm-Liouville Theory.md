#math

**The reason separated ODEs always hand you an orthogonal, complete basis: they're self-adjoint eigenvalue problems** — Sturm-Liouville is the Hermitian-matrix theorem for differential operators. Real eigenvalues, orthogonal eigenfunctions, completeness — same package as the spectral theorem.

The goal is to find the $\lambda$ eigenvalues and the corresponding eigenfunctions $y(x)$ which are then written in an **orthonormal basis** $y_{n(x)}$ in a $w(x)$ - **weighted inner product hilbert space**

# Reference

**Self-adjoint form** (any second-order linear ODE can be massaged into it):
$$
\frac{d}{dx}\!\left[p(x)\frac{dy}{dx}\right] + q(x)\, y = -\lambda\, w(x)\, y
$$
with $w(x) > 0$ the **weight function**. With suitable boundary conditions the operator is self-adjoint, so:

- **eigenvalues $\lambda_n$ real**, discrete, $\lambda_0 < \lambda_1 < \cdots \to \infty$
- **eigenfunctions orthogonal under the weight:** $\int y_n(x)\, y_m(x)\, w(x)\, dx = \delta_{nm} N_n$
- **complete:** any decent $f(x)$ expands as $f = \sum c_n y_n$ with $c_n = \frac{1}{N_n}\int f\, y_n\, w\, dx$
- $n$-th eigenfunction has $n$ nodes (more wiggles = higher eigenvalue)

All the coefficient functions are continuous, but $p(x) > 0$ and $w(x) > 0$ are further constraints. 

**The named-polynomials table** — each is Sturm-Liouville with its own interval and weight:

| Family                | Interval           | $p(x)$          | $q(x)$   | $w(x)$       | $\lambda_n$                                           | Physics home                  |
| --------------------- | ------------------ | --------------- | -------- | ------------ | ----------------------------------------------------- | ----------------------------- |
| Legendre $P_l$        | $[-1,1]$           | $1-x^2$         | $0$      | $1$          | $l(l+1)$                                              | angular Laplacian, multipoles |
| Hermite $H_n$         | $(-\infty,\infty)$ | $e^{-x^2}$      | $0$      | $e^{-x^2}$   | $2n$                                                  | harmonic oscillator           |
| Laguerre $L_n^k$      | $[0,\infty)$       | $x^{k+1}e^{-x}$ | $0$      | $x^k e^{-x}$ | $n$                                                   | hydrogen radial               |
| Bessel $J_m(k_{mn}x)$ | $[0,a]$            | $x$             | $-m^2/x$ | $x$          | $k_{mn}^2$ (numerical zeros of $J_m$, no closed form) | cylindrical modes             |
| $\sin,\cos$           | $[0,L]$            | $1$             | $0$      | $1$          | $(n\pi/L)^2$                                          | Fourier series                |

**The practical payoff:** don't re-derive orthogonality for each family — it's automatic. But *always include the weight* in inner products; forgetting the $x$ in Bessel orthogonality or the $e^{-x^2}$ in Hermite is the classic error.

Usually the weight is either baked into the normalization, coordinate system, or $\sqrt{w(x)}$ is attached to the basis functions so that the **inner product is always implemented by** $\langle f, g \rangle_w = \int f \ g \ w dx$.

> [!question]- Why are eigenfunctions with different eigenvalues automatically orthogonal?
> Same proof as Hermitian matrices: $\langle y_m, L y_n\rangle = \langle L y_m, y_n\rangle$ by self-adjointness (boundary terms vanish), so $(\lambda_n - \lambda_m)\int y_m y_n w\, dx = 0$. Distinct eigenvalues force the integral to zero — the weight $w$ is baked into the inner product by the equation itself.

This is all analogous to Quantum Mechanics, as in the following comparison:

| Sturm-Liouville                    | Quantum Mechanics                |
| ---------------------------------- | -------------------------------- |
| Self-adjoint differential operator | Hermitian observable (Ĥ, p̂, x̂) |
| Eigenvalue problem Lf = λwf        | Schrödinger equation Ĥψ = Eψ     |
| Weight function w(x)               | Measure on Hilbert space         |
| Orthogonal eigenfunctions          | Orthonormal energy eigenstates   |
| Completeness of eigenfunctions     | Completeness of basis states     |

# Connections

- [[Hermite Polynomials]] — the Gaussian-weight family, QHO eigenfunctions
- [[Legendre Polynomials and Spherical Harmonics]] — the angular family
- [[Bessel Functions]] — the cylindrical family (weight x!)
- [[Separation of Variables]] — where S-L problems come from
- [[Hermitian Matrices]] — the finite-dimensional version of the same theorem

---
Source: Arfken & Weber, *Mathematical Methods for Physicists*, Ch. 8; Boas Ch. 12
