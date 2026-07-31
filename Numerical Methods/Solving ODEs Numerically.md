#numerics #math

**Integrating $\dot y = f(y, t)$ is stepping with a local polynomial approximation. Three decisions matter: step size (accuracy vs cost), explicit vs implicit (dictated by stiffness), and whether the integrator must respect structure — energy, unitarity — over long times.** Default: adaptive RK45. This page is recognizing when the default is wrong.

# Reference

**Orders and adaptivity.** A method of order $p$ has local error $O(h^{p+1})$, global $O(h^p)$: Euler $p = 1$ (conceptual only), RK4 $p = 4$. Production integrators (RK45/Dormand–Prince; `solve_ivp`, `ode45`) embed orders 4 and 5, use their difference as a per-step error estimate, and adapt $h$ to hold it at tolerance. Set `rtol`/`atol` deliberately (defaults ~$10^{-3}$ are loose; tighten 10× and confirm the answer moves less than you care about); get output at your times via dense output, not forced small steps.

**Error floor.** Total error = truncation $O(h^p)$ + roundoff $O(\epsilon/h)$ ([[Floating Point and Numerical Error]]): float64 bottoms out near $10^{-12}$–$10^{-13}$; rtol $= 10^{-15}$ requests noise.

**Stiffness.** Explicit stability requires resolving the *fastest* eigenvalue of the Jacobian even after its mode has decayed:

$$|1 + h\lambda| \leq 1 \;\Rightarrow\; h < 2/|\lambda_{\max}| \quad (\text{explicit Euler; all explicit methods similar}),$$

so a decayed mode with $\lambda = -10^6\,\mathrm{s^{-1}}$ pins $h \sim$ µs under second-scale dynamics. The tell: an adaptive explicit solver grinding at tiny steps while the solution looks smooth. Fix: **implicit** methods (backward Euler, BDF, Radau) solve for $y_{n+1}$ each step — a Newton solve needing the Jacobian, but stable at any $h$: they step at the pace of the slow physics. In practice: `'BDF'`/`'Radau'`/`'LSODA'`, and supply the Jacobian (finite-differencing it costs $N$ extra $f$-calls per step). Stiff-by-construction cases: rate equations with fast/slow channels, master equations with strong decay, circuit transients ([[Linear ODE Systems]] — eigenvalue spread *is* the stiffness ratio).

**Structure preservation.** A generic integrator's per-step error has no memory; conserved quantities random-walk or drift secularly.

- **Hamiltonian → symplectic** (leapfrog/Verlet, higher-order compositions): exactly conserve a slightly-wrong Hamiltonian, so energy error stays bounded and oscillatory forever instead of drifting. Fixed step required — adaptivity breaks the property.
- **Quantum → unitary.** RK4 on Schrödinger leaks norm. Crank–Nicolson is exactly unitary:
$$U_{\text{step}} = \left(1 + \tfrac{i}{2}Hh\right)^{-1}\left(1 - \tfrac{i}{2}Hh\right);$$
split-operator FFT handles $H = T + V$ with exact sub-exponentials ([[Trotter Product Formula]]); Magnus-based exponential integrators handle driven $H(t)$ with the truncation staying *in the group* — unitary at every order ([[Magnus Expansion]]); Krylov `expm_multiply` for large sparse $H$ ([[Exact Diagonalization and Sparse Methods]]).

**Boundary-value problems** (shooting to an eigenvalue, two-point conditions): not stepping problems — collocation (`solve_bvp`); naive shooting is exponentially ill-conditioned when stiff.

**Checklist:** converged under tolerance tightening; conserved quantities monitored (free error meters: norm, energy, $\mathrm{Tr}\rho$); tiny-steps-smooth-solution → suspect stiffness; long conservative runs → structure-preserving scheme; discontinuous drives → restart the integrator at the discontinuity.

> [!question]- An explicit solver takes hours on a driven master equation; an implicit run takes minutes and agrees. What was knowable in advance?
> The Liouvillian's rate spread. A decay at $\gamma \sim 10^8\ \mathrm{s^{-1}}$ under dynamics observed at $10^4\ \mathrm{s^{-1}}$ pins the explicit step at $\sim 1/\gamma$ for stability although the fast mode's amplitude is long dead; the implicit method steps at the physics. Rates spanning many decades = stiff = choose implicit before running anything.

# Connections

- [[Floating Point and Numerical Error]] — the roundoff floor under truncation
- [[Linear ODE Systems]] — eigenvalue timescales; stiffness quantified
- [[Magnus Expansion]] — unitarity-preserving stepping for driven systems
- [[Trotter Product Formula]] — split-operator as algorithm
- [[Matrix Exponential]] — the exact propagator the quantum integrators approximate

---
Source: Hairer & Wanner, *Solving ODEs I–II*; Hairer, Lubich & Wanner, *Geometric Numerical Integration*
