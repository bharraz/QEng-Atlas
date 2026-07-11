#linear-algebra #math

**The pseudo-inverse $A^+$ is the closest thing to $A^{-1}$ for matrices that aren't square or aren't invertible: invert the singular values you can, kill the ones you can't.** Applying it to $Ax = b$ hands you the least-squares solution automatically.

# Reference

From the SVD $A = U\Sigma V^\dagger$:
$$
A^+ = V\,\Sigma^+ U^\dagger, \qquad \Sigma^+ = \mathrm{diag}(1/\sigma_1, \dots, 1/\sigma_r, 0, \dots)
$$
— transpose the shape, invert nonzero singular values, leave zeros as zeros.

**What $x = A^+ b$ gives you, by case:**
- **Overdetermined** (tall $A$, more equations than unknowns — every fitting problem): the $x$ minimizing $\|Ax - b\|^2$. Equivalent to the normal-equations solution $x = (A^\dagger A)^{-1} A^\dagger b$ when $A$ has full column rank, but numerically better behaved.
- **Underdetermined** (wide $A$): among the infinitely many exact solutions, the one of minimum norm $\|x\|$.
- **Invertible:** $A^+ = A^{-1}$, nothing new.

**The practical knob — truncated SVD:** when $A$ is ill-conditioned, tiny $\sigma_i$ turn into huge $1/\sigma_i$ that amplify noise in $b$. Set a cutoff and zero out $1/\sigma_i$ below it (this is Tikhonov regularization's blunt cousin). You trade a little bias for a lot of variance — standard move in tomography reconstruction and deconvolution.

In quantum-info practice: linear inversion state tomography is literally $\rho = A^+ \vec{p}$ on the measured probabilities, and its notorious noise sensitivity is exactly the small-singular-value amplification above.

> [!question]- Why does $A^+ b$ minimize $\|Ax - b\|$ for a tall matrix $A$?
> In the SVD basis the residual splits into components along range$(A)$ (which $x$ can cancel, and $A^+$ does, mode by mode via $1/\sigma_i$) and components orthogonal to it (which no $x$ can touch). Zeroing the reachable part is optimal; the orthogonal remainder is the least-squares residual.

# Connections

- [[Singular Value Decomposition]] — the pseudo-inverse is defined and computed through it
- [[Least Squares and Chi-Squared Fitting]] — $A^+$ is the linear least-squares solution in closed form
- [[Condition Number]] — small singular values are why naive inversion explodes; truncation is the fix
- [[Quantum State Tomography]] — linear-inversion reconstruction is a pseudo-inverse applied to measurement data

---
Source: Trefethen & Bau, *Numerical Linear Algebra*, Lecture 11
