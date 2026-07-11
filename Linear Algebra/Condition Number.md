#linear-algebra #math

**The condition number $\kappa = \sigma_{\max}/\sigma_{\min}$ measures how much a matrix amplifies relative error when you invert it** — solving $Ax = b$ can magnify fractional input error by up to $\kappa$, no matter how good your solver is.

# Reference

$$
\kappa(A) = \|A\|\,\|A^{-1}\| = \frac{\sigma_{\max}}{\sigma_{\min}}, \qquad \frac{\|\delta x\|}{\|x\|} \lesssim \kappa(A)\, \frac{\|\delta b\|}{\|b\|}
$$

$\kappa = 1$ for unitaries (they don't distort at all); $\kappa \to \infty$ as $A$ approaches singular. **Rule of thumb: you lose $\log_{10}\kappa$ digits of precision.** In double precision ($\sim 16$ digits), $\kappa \gtrsim 10^{16}$ means the answer is numerically meaningless — and $\kappa \sim 10^8$ already halves your digits.

**Geometric picture:** $A$ maps the unit sphere to an ellipsoid with axes $\sigma_i$. Large $\kappa$ = a very squashed ellipsoid; inverting stretches the squashed direction back out, amplifying any noise that landed along it.

**Ill-conditioned fitting** — the place you actually meet this: nearly-degenerate model parameters (two decay constants close together, polynomial fits with a bad basis) give a design matrix or Hessian with tiny $\sigma_{\min}$. Symptoms: fit parameters swing wildly run-to-run while the fit curve barely changes, huge anti-correlated error bars. Fixes: reparametrize (orthogonal polynomials, centered variables), regularize, or accept that the data only constrains the well-conditioned combinations.

Note $\kappa(A^\dagger A) = \kappa(A)^2$ — forming normal equations squares the condition number, which is why QR or SVD beats solving $A^\dagger A x = A^\dagger b$ directly.

> [!question]- Why do the normal equations lose you twice as many digits as QR on the same least-squares problem?
> They work with $A^\dagger A$, whose singular values are $\sigma_i^2$, so $\kappa(A^\dagger A) = \kappa(A)^2$ — squaring the condition number doubles the lost digits $\log_{10}\kappa$.

# Connections

- [[Singular Value Decomposition]] — $\kappa$ is read directly off the extreme singular values
- [[Least Squares and Chi-Squared Fitting]] — ill-conditioning is why fits with correlated parameters go haywire
- [[Pseudo-Inverse]] — truncating small singular values is the standard rescue for ill-conditioned inversion
- [[Matrix Norms]] — $\kappa$ is a product of operator norms; other norms give other (equivalent-in-spirit) condition numbers

---
Source: Trefethen & Bau, *Numerical Linear Algebra*, Lectures 12-14
