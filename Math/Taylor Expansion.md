#math

**Find the small dimensionless parameter, expand in it, keep the leading term that does physics** — half of theoretical physics is choosing what's small and truncating honestly.

# Reference

**The standard kit** (about $x=0$, to the orders you actually use):

| Expansion | Series | Converges |
|---|---|---|
| $(1+x)^n$ | $1 + nx + \frac{n(n-1)}{2}x^2$ | $\|x\|<1$ (any real $n$) |
| $e^x$ | $1 + x + \frac{x^2}{2} + \frac{x^3}{6}$ | all $x$ |
| $\sin x$ | $x - \frac{x^3}{6}$ | all $x$ |
| $\cos x$ | $1 - \frac{x^2}{2} + \frac{x^4}{24}$ | all $x$ |
| $\ln(1+x)$ | $x - \frac{x^2}{2}$ | $\|x\|<1$ |
| $\frac{1}{1-x}$ | $1 + x + x^2$ | $\|x\|<1$ |
| $\sqrt{1+x}$, $\frac{1}{\sqrt{1+x}}$ | $1 + \frac{x}{2} - \frac{x^2}{8}$, $\;1 - \frac{x}{2} + \frac{3x^2}{8}$ | binomial with $n=\pm\frac12$ |

$(1+x)^n \approx 1+nx$ is the single most-used line: it covers relativistic corrections, impedance mismatches, index changes, error propagation.

**When truncation is safe:** the *next* term must be small compared to the ones you kept, over the whole range you use — not just at one point. Odd functions expanded around symmetric points lose every other term (this is why sideband spectra in $\eta = kx_0$ come in clean orders: carrier at $\eta^0$, first sidebands at $\eta^1$). If your answer at leading order is exactly zero, the second-order term *is* the physics — don't call it negligible (light shifts, second-order Doppler).

**Small-parameter checklist:** $v/c$, $\Omega/\omega$, $kx_0$ (Lamb-Dicke $\eta$), $d/r$ (multipole), $\Delta/\omega_0$. Nondimensionalize first; "small" only means something for a dimensionless number.

> [!question]- Your leading-order answer came out zero. What now?
> Go one order deeper — the first nonvanishing term is the physics, not a correction. Classic cases: quadratic Zeeman on clock states, second-order Doppler, light shift as second-order perturbation. Zero at first order usually means a symmetry is protecting you, and the next order tells you how well.

# Connections

- [[Multipole Expansion]] — Taylor in $d/r$; each order is a physical moment
- [[Lamb-Dicke Regime]] — $e^{i\eta(a+a^\dagger)}$ expanded in $\eta$: the orders are carrier and sidebands
- [[Time-Independent Perturbation Theory]] — the quantum version: energies as a series in the coupling
- [[Error Propagation]] — first-order Taylor is where $\sigma_f^2 = \sum(\partial f/\partial x_i)^2\sigma_i^2$ comes from

---
Source: Bender & Orszag, *Advanced Mathematical Methods*, Ch. 3 (asymptotic expansions); any calculus text for the kit

