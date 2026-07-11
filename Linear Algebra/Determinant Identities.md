#linear-algebra #math

**The determinant is the volume scale factor of a linear map — multiplicative where trace is additive.** $\det A = 0$ means the map squashes some direction flat: singular, non-invertible, nontrivial null space.

# Reference

$\det A = \prod_i \lambda_i$ (eigenvalues with multiplicity). Geometrically: signed volume of the image of the unit cube — sign flips mean orientation reversal.

**The kit:**

$$
\det(AB) = \det A \cdot \det B, \qquad \det A^\dagger = (\det A)^*, \qquad \det A^{-1} = \frac{1}{\det A}
$$

$$
\det(cA) = c^n \det A \quad (\text{the classic trap — } n\text{th power, not linear!})
$$

$$
\boxed{\det e^A = e^{\mathrm{Tr}A}}
$$

— the trace–determinant bridge. Proof by eigenvalues: $e^A$ has eigenvalues $e^{\lambda_i}$, so $\det e^A = e^{\sum\lambda_i}$. Consequences: traceless generator ⇒ unit-determinant group (that's the "S" in SU(2): $\mathrm{Tr}(i\theta\hat{n}\cdot\sigma/2)$ traceless ⇒ $\det U = 1$); Liouville's theorem for $\dot{x} = Ax$ (phase-space volume $\propto e^{t\,\mathrm{Tr}A}$).

**Class facts:** $|\det U| = 1$ for unitary (volumes preserved, possibly with a global phase); $\det > 0$ for positive definite; $\det(A \otimes B) = (\det A)^m (\det B)^n$ for $n\times n$, $m \times m$ factors.

**Practical:** never compute $\det$ by cofactor expansion beyond 3×3; use LU factorization ($\det = \prod$ pivots), and prefer $\log\det = \mathrm{Tr}\log$ to dodge overflow — it appears constantly in Gaussian likelihoods.

> [!question]- Why does a traceless Hamiltonian generate evolution with $\det U = 1$, and why is that harmless physically?
> $U = e^{-iHt/\hbar}$, so $\det U = e^{-it\,\mathrm{Tr}H/\hbar} = 1$ when $\mathrm{Tr}H = 0$. A nonzero trace only contributes a global phase $e^{-i\bar{E}t/\hbar}$ — unobservable, which is why you can always shift $H$ traceless (drop the energy offset).

# Connections

- [[Matrix Exponential]] — source of $\det e^A = e^{\mathrm{Tr}A}$ and the traceless ⇒ special-group statement
- [[Trace Identities]] — the additive counterpart; the two meet in the log-det/trace-log identity
- [[Eigenvalues and Eigenvectors]] — $\det = \prod\lambda_i$, and $\det(A - \lambda\mathbb{1}) = 0$ defines the spectrum
- [[Rank and Nullity]] — $\det = 0$ ⇔ rank-deficient ⇔ nontrivial null space

---
Source: Horn & Johnson, *Matrix Analysis*, Ch. 0–1.
