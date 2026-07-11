#linear-algebra #math

**Turn any linearly independent set into an orthonormal basis by subtracting off, from each new vector, its projections onto everything you've already built.** What's left is by construction orthogonal to all of it.

# Reference

Given $\{v_1, v_2, \dots\}$, build $\{e_1, e_2, \dots\}$:
$$
u_k = v_k - \sum_{j<k} \langle e_j | v_k \rangle\, e_j, \qquad e_k = \frac{u_k}{\|u_k\|}
$$

Each $e_k$ spans the same space as $\{v_1,\dots,v_k\}$ — the procedure preserves the nested subspaces, just re-coordinatizes them orthogonally.

**QR in one line:** running Gram-Schmidt on the columns of $A$ gives $A = QR$ with $Q$ orthonormal columns and $R$ upper triangular (the $R$ entries are the projection coefficients you subtracted).

**Numerical gotcha:** classical GS is unstable — when $v_k$ is nearly in the span of the others, you subtract two almost-equal vectors and roundoff destroys orthogonality. **Modified GS** (subtract projections one at a time, updating $v_k$ after each) fixes most of it; Householder QR is the fully robust route. If your "orthonormal" basis fails $\langle e_i|e_j\rangle \approx 0$ checks, this is why.

**In practice** this is how you orthogonalize degenerate eigenvectors, build orthogonal polynomials (Hermite, Legendre are GS on $1, x, x^2, \dots$ with different weights), and orthonormalize mode functions.

> [!question]- Why does classical Gram-Schmidt lose orthogonality numerically, and what's the fix?
> Near-linearly-dependent inputs make $u_k$ the small difference of large vectors — catastrophic cancellation amplifies roundoff into non-orthogonality. Modified GS re-projects against the running remainder instead of the original $v_k$, keeping errors from compounding.

# Connections

- [[Inner Products and Orthogonality]] — the projections being subtracted are inner products; GS presupposes that structure
- [[Basis Change]] — GS is a triangular change of basis to an orthonormal one
- [[Sturm-Liouville Theory]] — the classical orthogonal polynomials are GS with a weight function
- [[Least Squares and Chi-Squared Fitting]] — QR is the numerically sane way to solve least-squares problems

---
Source: Trefethen & Bau, *Numerical Linear Algebra*, Lectures 7-8
