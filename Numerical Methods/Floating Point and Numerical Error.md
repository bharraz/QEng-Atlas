#numerics #math

**A float is scientific notation in binary with a fixed-size mantissa: ~16 significant digits (float64), relative precision $\epsilon \approx 2.2\times10^{-16}$. Every numerical disaster is one of two things: subtracting nearly equal numbers (cancellation, which deletes your significant digits), or feeding a well-behaved algorithm an ill-conditioned problem (where no algorithm can help).** Separating those two — algorithm error vs problem sensitivity — is the core skill.

# Reference

**The model:** every stored number and every operation is correct to relative error $\epsilon$: $\mathrm{fl}(x \circ y) = (x \circ y)(1 + \delta)$, $|\delta| \leq \epsilon$. Absolute spacing between representable numbers grows with magnitude — floats near $10^{16}$ are spaced by ~1 (adding 1 to $10^{16}$ does *nothing*). Integers are exact up to $2^{53}$; decimal fractions like 0.1 are *not* representable (binary), which is why `0.1 + 0.2 != 0.3` and why you never compare floats with == (compare $|a - b| < \text{tol}\cdot|b|$, and think about whether tol is relative or absolute).

**Catastrophic cancellation — the one mechanism to internalize.** Subtracting nearly equal numbers doesn't create error; it *promotes* existing relative error: if $x$ and $y$ agree to $k$ digits, $x - y$ has $k$ fewer significant digits than its inputs. Classic hits and their standard fixes:

- Quadratic formula with $b^2 \gg 4ac$: the root $(-b + \sqrt{b^2 - 4ac})/2a$ cancels. Fix: compute the *big* root stably, get the small one from $x_1 x_2 = c/a$.
- $1 - \cos\theta$ for small $\theta$: use $2\sin^2(\theta/2)$. Similarly `expm1`, `log1p` exist because $e^x - 1$ and $\ln(1+x)$ cancel near 0.
- **Variance in one pass**, $\langle x^2\rangle - \langle x\rangle^2$: cancels violently when the mean dwarfs the spread (e.g. timestamps). Fix: subtract a running mean first (Welford's algorithm) — this *will* bite you in data analysis.
- **Numerical differentiation** is cancellation by construction: $[f(x+h) - f(x)]/h$ has truncation error $\sim h$ and roundoff error $\sim \epsilon/h$; the optimum $h \sim \sqrt{\epsilon} \approx 10^{-8}$ leaves you only *half* your digits (centered difference: $h \sim \epsilon^{1/3}$, 2/3 of the digits). Needing accurate derivatives is a reason to change method (automatic differentiation, complex-step $\mathrm{Im}\,f(x + ih)/h$ — no cancellation, full precision).

**Accumulation:** summing $N$ terms naively grows error $\sim N\epsilon$ (worse if magnitudes are disparate — small terms added to a large sum vanish entirely). Sort small-to-large, sum hierarchically (pairwise — what NumPy does), or use Kahan compensated summation. Rule of thumb: $10^8$ additions in float32 ($\epsilon \approx 10^{-7}$) can have *no* digits left — use float64 for accumulators even if data is float32.

**Conditioning vs stability — whose fault is the wrong answer?**

- The **condition number** $\kappa$ is a property of the *problem*: how much a relative input perturbation is amplified in the output (see [[Condition Number]]). Expect to lose $\log_{10}\kappa$ digits *no matter what algorithm you use*: the inputs themselves are only known to $\epsilon$.
- **Stability** is a property of the *algorithm*: a backward-stable algorithm returns the exact answer to a slightly-wrong problem (wrong by $\sim\epsilon$). Total error $\sim \kappa\,\epsilon$.
- Diagnosis: if a stable algorithm gives garbage, the problem is ill-conditioned — *reformulate the problem* (regularize, rescale, change parametrization), don't shop for algorithms. Fitting a high-degree polynomial in the monomial basis ($\kappa$ astronomically large) vs Chebyshev basis (fine) is the canonical example: same fit, different conditioning.

**Linear algebra corollaries** (where most conditioning is met in practice): never compute $A^{-1}b$ — solve $Ax = b$ (factorization is cheaper and more stable). Never form the normal equations $A^\top A x = A^\top b$ for least squares if you can help it — that *squares* $\kappa$; use QR or [[Singular Value Decomposition|SVD]] (the SVD also tells you the conditioning and gives the [[Pseudo-Inverse|pseudo-inverse]] with rank control). If a matrix is symmetric/Hermitian, say so to the solver ($\texttt{eigh}$ not $\texttt{eig}$): the structured algorithm is faster *and* guarantees real eigenvalues.

**Sanity practices:** rescale problems to natural units so quantities are $O(1)$ (a Hamiltonian in Hz next to times in seconds mixes $10^{9}$ scales — work in angular frequency × time, dimensionless); check results at two precisions (float32 vs float64 disagreement localizes roundoff problems); perturb the inputs by $\epsilon$-scale noise and watch the output — an empirical condition number.

> [!question]- Your simulation conserves energy to 8 digits at short times, but energy drifts steadily after 10⁶ steps. Roundoff or physics?
> Steady *drift* is usually algorithm, not roundoff: roundoff error is nearly random and accumulates as $\sqrt{N}\epsilon$ (random walk), which after $10^6$ steps of float64 is still ~$10^{-13}$ — invisible. A secular linear drift means the integrator itself doesn't respect the conserved quantity (see [[Solving ODEs Numerically]] — non-symplectic integrators pump energy). Test: halve the step; roundoff error *grows* with more steps, truncation-induced drift *shrinks* as a power of $h$. The direction of change under refinement fingers the culprit.

# Connections

- [[Condition Number]] — the problem-sensitivity number, in its linear-algebra home
- [[Singular Value Decomposition]] — the stable workhorse for least squares and rank decisions
- [[Pseudo-Inverse]] — regularized inversion when conditioning is bad
- [[Solving ODEs Numerically]] — truncation error, the *other* error source, and its trade against this one
- [[FFT in Practice]] — numerically superb ($O(\epsilon\log N)$ error) precisely because it avoids cancellation

---
Source: Goldberg, "What Every Computer Scientist Should Know About Floating-Point Arithmetic," *ACM Comp. Surv.* 23, 5 (1991); Trefethen & Bau, *Numerical Linear Algebra*, Lec. 12–15; Higham, *Accuracy and Stability of Numerical Algorithms*
