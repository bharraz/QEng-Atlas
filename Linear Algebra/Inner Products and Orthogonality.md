#linear-algebra #math

**The inner product is what turns a bare vector space into geometry** — it defines lengths, angles, and "how much of $u$ is in $v$," and in QM it *is* the probability amplitude $\langle u|v\rangle$.

# Reference

Axioms (physicist convention, antilinear in the *first* slot): $\langle u|v\rangle = \langle v|u\rangle^*$, linear in $|v\rangle$, and $\langle v|v\rangle \ge 0$ with equality only for $v=0$.

**Cauchy-Schwarz** — the inequality behind every uncertainty relation:
$$
|\langle u|v\rangle|^2 \le \langle u|u\rangle \langle v|v\rangle
$$

**Orthonormal basis** $\{|e_i\rangle\}$: $\langle e_i|e_j\rangle = \delta_{ij}$, and any vector expands as $|v\rangle = \sum_i \langle e_i|v\rangle\, |e_i\rangle$ — components are just projections, no linear system to solve. That's the whole point of orthogonality: **coefficients decouple**.

**Functions are vectors too** ($L^2$): $\langle f|g\rangle = \int f^*(x)\,g(x)\,dx$, possibly with a weight $w(x)$. Fourier coefficients, Hermite expansions, and $\langle x|\psi\rangle$ are all the same projection move in this space.

> [!question]- Why does an orthonormal basis make expansion coefficients trivial to find?
> Hit $|v\rangle = \sum_j c_j|e_j\rangle$ with $\langle e_i|$: orthonormality kills every term but one, so $c_i = \langle e_i|v\rangle$ directly. Non-orthogonal bases require inverting the Gram matrix instead.

# Connections

- [[Gram-Schmidt Orthogonalization]] — how to manufacture an orthonormal basis from any linearly independent set
- [[Fourier Series]] — sines and cosines as an orthonormal basis on $L^2$; coefficients are inner products
- [[Dirac Notation]] — bra-ket is inner-product notation elevated to a full calculus
- [[Sturm-Liouville Theory]] — where the weighted inner products and orthogonal eigenfunctions come from
- [[Hermitian Matrices]] — self-adjointness $\langle x, Ay\rangle = \langle Ax, y\rangle$ is defined relative to the inner product

---
Source: Axler, *Linear Algebra Done Right*, Ch. 6
