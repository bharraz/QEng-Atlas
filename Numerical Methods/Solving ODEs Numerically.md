#numerics #math

**Integrating $\dot{y} = f(y, t)$ numerically is stepping along the solution with a local polynomial approximation; the three decisions that matter are step size (accuracy vs cost), explicit vs implicit (dictated by stiffness), and whether the integrator must respect structure (energy, unitarity) over long times.** Default answer: adaptive RK45. This page is about recognizing when the default is wrong.

# Reference

**The mechanics.** Euler ($y_{n+1} = y_n + h f_n$) has local error $O(h^2)$, global $O(h)$ — never use it except to understand the concept. **Runge–Kutta** methods sample $f$ at trial points inside the step and combine them to cancel error terms; RK4 is global $O(h^4)$. Production integrators (RK45/Dormand–Prince — `solve_ivp` default, `ode45`) embed two orders, use the difference as a **local error estimate**, and adapt $h$ each step to hold it at your tolerance. Consequences of adaptivity you must respect: set `rtol`/`atol` deliberately (defaults ~$10^{-3}$ are *loose* — sanity-check by tightening 10× and confirming the answer moves less than you care about); and the solver chooses its own time points, so demand output at your times via dense output/`t_eval`, don't force tiny steps.

**Truncation vs roundoff:** total error is truncation ($\sim h^p$) plus roundoff ($\sim \epsilon/h$, see [[Floating Point and Numerical Error]]). Tightening tolerance eventually *increases* error — float64 with a good integrator bottoms out around $10^{-12}$–$10^{-13}$; requesting rtol = $10^{-15}$ is asking for noise.

**Stiffness — the failure you will actually hit.** A problem is stiff when it contains timescales much faster than the dynamics you care about — a damped mode with $\lambda = -10^6$ inside evolution you want on seconds (rate equations with fast/slow channels, RC transients in circuit models, chemical kinetics, master equations with fast decay). Explicit methods must resolve the *fastest* scale to remain stable — not for accuracy, purely for stability (explicit Euler diverges unless $|1 + h\lambda| \leq 1$, i.e. $h < 2/|\lambda|$) — so the step collapses to $10^{-6}$ even though the solution is smooth. The tell: an adaptive explicit solver grinds to absurdly small steps *while the solution looks boring*. The fix: **implicit methods** (backward Euler, BDF, Radau), which solve an equation involving $y_{n+1}$ each step — expensive per step (a Newton solve, needs the Jacobian) but stable at *any* $h$: they step over the fast decay at the pace of the slow physics. In practice: switch `solve_ivp` to `'BDF'`/`'Radau'` or `'LSODA'` (auto-detects), and supply the Jacobian if you can (finite-differencing it costs $N$ extra $f$-calls per step).

**Structure preservation — long-time integrity.** A general-purpose integrator makes an $O(h^p)$ error *per step* with no memory; conserved quantities random-walk or drift secularly. If the answer is a long trajectory of a conservative system, match the integrator to the structure:

- **Hamiltonian systems → symplectic integrators** (leapfrog/Verlet — the MD standard, or higher-order compositions): they exactly conserve a *slightly wrong* Hamiltonian, so energy error stays **bounded, oscillating, forever** instead of drifting. Fixed step required — adaptivity breaks the symplectic property.
- **Quantum evolution → unitary steps.** RK4 on the Schrödinger equation leaks norm. Either renormalize as a diagnostic-and-patch, or use structure: Crank–Nicolson ($(1 + iH h/2)^{-1}(1 - iHh/2)$ — exactly unitary), split-operator FFT for $H = T + V$ (kick–drift–kick with exact sub-exponentials — [[Trotter Product Formula]] as an algorithm), or Magnus-based exponential integrators for driven $H(t)$ (see [[Reference Atlas/Math/Magnus Expansion]] — the point is that the truncated evolution stays *in the group*: unitary regardless of truncation order). Krylov/expm methods handle big sparse $H$.

**Boundary-value problems** (shooting to an eigenvalue, beam propagation with two-point conditions) are *not* stepping problems: use a dedicated BVP solver (`solve_bvp`, collocation) or reformulate; naive shooting is exponentially ill-conditioned in stiff cases.

**Checklist before trusting an ODE result:** converged under tolerance tightening; conserved quantities monitored (they're free error meters — norm, energy, trace of $\rho$); stiffness suspected if steps are tiny while solutions look smooth; long-time runs on structure-preserving schemes; discontinuous drives (pulse edges) handled by restarting the integrator at the discontinuity rather than making the solver find it.

> [!question]- Simulating a driven qubit master equation, your explicit solver takes hours; a colleague's implicit run takes minutes and matches. Why, and what was the giveaway?
> The Lindblad equation is stiff whenever decay rates or detunings far exceed the Rabi-frequency timescale you're resolving — e.g. an adiabatically eliminated but still-present fast decay at $\gamma \sim 10^8\,\mathrm{s^{-1}}$ under dynamics you're watching at $10^4\,\mathrm{s^{-1}}$. The explicit method's step is pinned at $\sim 1/\gamma$ for stability although the fast mode's amplitude is already negligible; the implicit method steps at the physics timescale. The giveaway was available beforehand: eigenvalues of the Liouvillian (or just the ratio of the largest rate to the observation timescale) spanning many decades = stiff, choose implicit from the start.

# Connections

- [[Floating Point and Numerical Error]] — the roundoff floor under the truncation error
- [[Linear ODE Systems]] — the analytic structure ($e^{At}$, eigenvalue timescales) that defines stiffness
- [[Reference Atlas/Math/Magnus Expansion]] — unitarity-preserving time stepping for driven quantum systems
- [[Trotter Product Formula]] — split-operator methods are Trotterization as numerics
- [[Matrix Exponential]] — the exact propagator the good quantum integrators approximate within the group

---
Source: Hairer, Nørsett & Wanner, *Solving ODEs I*; Hairer & Wanner, *Solving ODEs II* (stiff); Press et al., *Numerical Recipes*, Ch. 17; Hairer, Lubich & Wanner, *Geometric Numerical Integration* (symplectic)
