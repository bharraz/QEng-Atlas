#group-theory #quantum #math

**Once the Hamiltonians of a problem generate a finite-dimensional Lie algebra, evolution reduces from an operator equation on Hilbert space to a handful of scalar ODEs — or to exact algebraic identities.**

Determining whether and how the algebra closes is [[Dynamical Lie Algebras and Closure]]. Here the algebra is assumed to close into $\mathfrak g$ with basis $\{X_1,\dots,X_d\}$, $d = \dim\mathfrak g$, and structure constants $[X_i,X_j] = \sum_k c_{ij}^{\,k}X_k$.

# Reference

## Method selection

| Situation | Method |
|---|---|
| $\mathfrak g$ abelian | $U = \exp\int A\,dt$ directly |
| $\mathfrak g$ nilpotent (Heisenberg) | Magnus terminates; explicit integrals ([[Magnus Expansion]]) |
| $\mathfrak g$ solvable | Wei–Norman, quadratures only |
| $\mathfrak g = \mathfrak{su}(2)$ or $\mathfrak{su}(1,1)$ | Wei–Norman (one Riccati), or solve $2\times2$ |
| quadratic Hamiltonians, Gaussian states | symplectic moment propagation |
| single exponential to reorder | disentangling identity |
| product of exponentials to merge | Zassenhaus |
| $\mathfrak g$ closes only after a frame change | interaction picture first |
| $\mathfrak g$ large or unbounded | truncated [[Magnus Expansion]], or numerics ([[Exact Diagonalization and Sparse Methods]]) |

**Picture:** a closed algebra is a small room the evolution can never leave, so the motion is described by a few coordinates in that room instead of the full Hilbert space.

## Wei–Norman product form

For $\dot U = A(t)U$ with $A(t) \in \mathfrak g$ at all times, write the propagator as an ordered product of one-parameter subgroups — **coordinates of the second kind**:
$$U(t) = e^{g_1(t)X_1}\, e^{g_2(t)X_2} \cdots e^{g_d(t)X_d}, \qquad g_j(0) = 0.$$

Substituting into the equation of motion and using the adjoint action to move each derivative left (every $e^{gX_i}X_je^{-gX_i}$ re-expands in the basis of $\mathfrak g$, by closure — [[Conjugation]]) gives $d$ coupled scalar ODEs for the $g_j$, with coefficients built from the structure constants. **Hilbert-space dimension never enters.**

Requirements and caveats:

- **Finite dimension is required.** $d$ must be finite for the product to be a finite ordered list; there is no Wei–Norman form on an algebra that fails to close.
- **The scalar system is generally nonlinear.** For $\mathfrak{su}(2)$ and $\mathfrak{su}(1,1)$ it is one Riccati equation plus quadratures.
- **Solvable algebras integrate by quadrature alone** — order the basis so the system is triangular, no nonlinear step. Nilpotent algebras are the special case where the $g_j$ are explicit integrals of the drive.
- **The parametrization is only local.** For non-solvable algebras the product form can fail to cover the entire group — coordinate singularities, e.g. at $g_2 = \pi/2$ in Euler-angle-type parametrizations (Euler angles being the $\mathfrak{su}(2)$ instance of this construction). The solution stays valid on each chart; continuing past a singularity requires reordering the factors.

## Reduction to a faithful low-dimensional representation

The $g_j(t)$ depend only on the structure constants and the drive, **not** on the representation used to compute them. So solve in the smallest faithful representation and transfer the answer:

| Algebra | Smallest faithful rep |
|---|---|
| $\mathfrak{su}(2)$, $\mathfrak{su}(1,1)$ | $2\times2$ |
| Heisenberg | $(2n{+}1)\times(2n{+}1)$ |
| $\mathfrak{sp}(2n,\mathbb R)$ | $2n\times 2n$ |

A time-dependent squeezing problem is solved in $2\times2$ matrices this way; the Fock-space operator follows by substituting the physical $K_\pm, K_0$ into the product form.

## Disentangling identities

Closed forms for reordering a single exponential into a product — BCH series that resum exactly because of the algebra's structure.

- **Heisenberg** ($[a,a^\dagger]=1$): $e^{\alpha a^\dagger - \alpha^* a} = e^{-|\alpha|^2/2}\, e^{\alpha a^\dagger} e^{-\alpha^* a}$ — the normally ordered displacement ([[Displacement Operator]]).
- **$\mathfrak{su}(2)$** ($[J_+,J_-]=2J_0$, $[J_0,J_\pm]=\pm J_\pm$): $e^{\zeta J_+ - \zeta^* J_-} = e^{\tau J_+}\, e^{\ln(1+|\tau|^2)J_0}\, e^{-\tau^* J_-}$, $\;\tau = \frac{\zeta}{|\zeta|}\tan|\zeta|$.
- **$\mathfrak{su}(1,1)$** ($[K_+,K_-]=-2K_0$, $[K_0,K_\pm]=\pm K_\pm$; $K_+ = \tfrac12 a^{\dagger2}$, $K_- = \tfrac12 a^2$, $K_0 = \tfrac12(a^\dagger a + \tfrac12)$): $e^{\zeta K_+ - \zeta^* K_-} = e^{\tau K_+}\, e^{-\ln(1-|\tau|^2)K_0}\, e^{-\tau^* K_-}$, $\;\tau = \frac{\zeta}{|\zeta|}\tanh|\zeta|$ — the normally ordered squeeze operator ([[Squeezed States]]).

The $\tan$ vs. $\tanh$ split is compact vs. non-compact: periodic in the group parameter versus unbounded.

**Zassenhaus** is the dual move — splitting one exponential into a *product*, where BCH merges a product into one exponential:
$$e^{t(A+B)} = e^{tA}\, e^{tB}\, e^{-\frac{t^2}{2}[A,B]}\, e^{\frac{t^3}{6}(2[B,[A,B]] + [A,[A,B]])} \cdots$$
Each factor is an exponential of a nested-bracket element, so the series **terminates whenever the algebra is nilpotent**. Often cleaner than Wei–Norman when you want an explicit splitting rather than a solved ODE system, and it is the algebraic parent of Trotter-type product formulas.

## Covariance and moment propagation

When $\mathfrak g$ is the quadratic algebra, states need not be evolved at all:

- **Gaussian states:** propagate $\bar z \to M\bar z$ and $\sigma \to M\sigma M^{\mathsf T}$ with $M(t) \in Sp(2n,\mathbb R)$ from a $2n$-dimensional matrix ODE ([[Symplectic Group]]).
- **Generally:** for any set of observables closing under commutation with $H$, the Heisenberg equations for their expectation values close among themselves — Ehrenfest with no approximation — giving a finite linear system for the moments.

## Frame transformations that reduce the algebra

For $H(t) = H_0 + V(t)$ whose full generator set does not close usefully, transform to the interaction picture: $\tilde V(t) = e^{iH_0t/\hbar}V(t)e^{-iH_0t/\hbar}$ may lie in a smaller algebra, either exactly or after discarding fast-oscillating terms ([[Rotating Wave Approximation (Atlas)]]). **Choosing a frame is choosing which subalgebra the residual dynamics occupies**, and getting $\tilde V$ to close is frequently the decisive step.

> [!question]- $H(t) = \omega(t)\,a^\dagger a + \chi(t)(a^2 + a^{\dagger 2})$. Identify the algebra and the resulting scalar problem.
> $\{a^\dagger a, a^2, a^{\dagger 2}\}$ closes as $\mathfrak{su}(1,1)$. Wei–Norman gives $U = e^{g_+K_+}e^{g_0K_0}e^{g_-K_-}$: one Riccati equation for $g_+$ driven by $\omega, \chi$, then two quadratures. Fock-space dimension is irrelevant — the entire time-dependent squeezing problem is one nonlinear scalar ODE.

# Connections

- [[Dynamical Lie Algebras and Closure]] — determining $\mathfrak g$; the prerequisite
- [[Magnus Expansion]] — the single-exponential alternative; exact under nilpotency
- [[Baker-Campbell-Hausdorff]] — the series these identities resum; Zassenhaus is its dual
- [[Symplectic Group]] — the quadratic case and covariance propagation
- [[Displacement Operator]] / [[Squeezed States]] — the Heisenberg and $\mathfrak{su}(1,1)$ identities in use
- [[Interaction Picture]] / [[Rotating Wave Approximation (Atlas)]] — frame choice as algebra reduction
- [[Conjugation]] — the adjoint action performing the Wei–Norman reordering
- [[Trotter Product Formula]] — the product-splitting idea in numerical form

---
Source: Wei & Norman, "Lie algebraic solution of linear differential equations," *J. Math. Phys.* 4, 575 (1963); Barnett & Radmore, *Methods in Theoretical Quantum Optics*, App. 5 (disentangling tables)
