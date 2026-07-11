#statistics #math

**Variance is the mean squared spread; covariance is how two variables' fluctuations move together** — and the covariance matrix packages both, so linear combinations of noisy quantities propagate by pure matrix algebra.

# Reference

$$
\mathrm{Var}(X) = \langle X^2\rangle - \langle X\rangle^2, \qquad
\mathrm{Cov}(X,Y) = \langle XY\rangle - \langle X\rangle\langle Y\rangle
$$

The workhorse identity — where correlated errors enter or cancel:

$$
\mathrm{Var}(aX + bY) = a^2\,\mathrm{Var}(X) + b^2\,\mathrm{Var}(Y) + 2ab\,\mathrm{Cov}(X,Y)
$$

Sum of *anticorrelated* variables: the cross term subtracts (common-mode rejection in one line). Independent ⇒ $\mathrm{Cov}=0$; the converse fails (uncorrelated ≠ independent, except jointly Gaussian).

**Covariance matrix:** $\Sigma_{ij} = \mathrm{Cov}(x_i, x_j)$ — symmetric, positive semidefinite, diagonal = variances. For any linear map, $\mathrm{Cov}(A\mathbf{x}) = A\Sigma A^{\mathsf T}$. This is what a fitter hands back: parameter errors are $\sqrt{\Sigma_{ii}}$, and the off-diagonals tell you which parameters trade off against each other.

**Correlation coefficient:** $\rho = \mathrm{Cov}(X,Y)/\sigma_X\sigma_Y \in [-1, 1]$ — the dimensionless version; $|\rho| \to 1$ means one variable is a deterministic linear function of the other.

> [!question]- A fit returns two parameters with $\rho = -0.95$. What does that mean for quoting them separately?
> Their errors are almost entirely a shared trade-off (a sloppy direction in parameter space). Quoting $\sigma_1$ and $\sigma_2$ alone overstates the uncertainty of any combination like the sum — you must carry the covariance, or reparametrize along the eigenvectors of $\Sigma$.

# Connections

- [[Error Propagation]] — its general formula is this note's $A\Sigma A^{\mathsf T}$ with $A = \nabla f$
- [[Autocorrelation]] — covariance of a signal with its own time-shifted self
- [[Positive Semidefinite Matrices]] — every covariance matrix is one; eigendecomposition gives principal axes
- [[Least Squares and Chi-Squared Fitting]] — parameter covariance matrix from the fit curvature

---
Source: Casella & Berger, *Statistical Inference* 2nd ed., §4.5
