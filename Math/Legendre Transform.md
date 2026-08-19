#math

**Re-express a convex function in terms of its slope instead of its coordinate, losing nothing — the move behind $L \to H$, every thermodynamic potential, and the pairing of conjugate variables.**

# Reference

$$f^*(p) = \sup_x \big[\,p\,x - f(x)\,\big]$$

For smooth convex $f$ the supremum is where the derivative vanishes, so the recipe is mechanical:

1. Set $p = \dfrac{df}{dx}$ — the new variable **is** the old slope.
2. Solve for $x(p)$.
3. Substitute: $f^*(p) = p\,x(p) - f(x(p))$.

**Why nothing is lost.** A convex function is the envelope of its tangent lines, so specifying (slope, intercept) for every tangent determines the curve exactly as well as specifying every point. $f^*$ *is* that catalogue of tangents — $-f^*(p)$ is the intercept of the tangent with slope $p$. Hence the involution:
$$f^{**} = f \qquad\text{(for convex } f)$$
Transform twice and you are back. For non-convex $f$, $f^{**}$ is the **convex hull** — the transform silently convexifies, which is not a defect but the content of Maxwell constructions and phase coexistence.

**The derivative relation reverses:**
$$p = \frac{df}{dx} \qquad\Longleftrightarrow\qquad x = \frac{df^*}{dp}$$

so $x$ and $p$ are **conjugate**: each is the other's derivative of the appropriate potential. This is the origin of the phrase "conjugate variables" throughout physics, and it is the same pairing that becomes $[\hat x,\hat p]=i\hbar$ after quantization ([[Symplectic Group]]).

## Mechanics: $L \to H$

$$H(q,p) = p\dot q - L(q,\dot q), \qquad p = \frac{\partial L}{\partial \dot q}$$

The transform is in $\dot q$ only; $q$ is a **passive variable**, carried along untouched. The payoff is structural, not cosmetic:

| | Lagrangian | Hamiltonian |
|---|---|---|
| Variables | $(q, \dot q)$ — $\dot q$ is a derivative, not independent | $(q,p)$ — genuinely independent coordinates |
| Equations | $n$ second-order | $2n$ **first-order** |
| Structure | variational ([[Euler-Lagrange Equation]]) | phase space with a symplectic form |

Trading second-order for first-order equations on a $2n$-dimensional space is what makes phase space, Liouville's theorem, canonical transformations, and symplectic integrators available at all.

**When it fails:** if $L$ is not convex in $\dot q$, $p = \partial L/\partial\dot q$ cannot be inverted for $\dot q$. Gauge theories are the standard case — the transform is degenerate, some momenta are *constraints* rather than variables, and Dirac's constrained-Hamiltonian machinery is the repair. A degenerate Legendre transform is the technical meaning of "this theory has gauge freedom" ([[Gauge Freedom]]).

## Thermodynamics: every potential is one transform

Start from $U(S,V,N)$ with $dU = T\,dS - P\,dV + \mu\,dN$, and trade any extensive variable for its conjugate intensive one:

| Potential | Transform | Differential | Natural for |
|---|---|---|---|
| $U(S,V)$ | — | $T\,dS - P\,dV$ | isolated |
| $F = U - TS$ | $S \to T$ | $-S\,dT - P\,dV$ | fixed $T$, $V$ |
| $H = U + PV$ | $V \to -P$ | $T\,dS + V\,dP$ | fixed $S$, $P$ |
| $G = U - TS + PV$ | both | $-S\,dT + V\,dP$ | fixed $T$, $P$ — chemistry |
| $\Omega = U - TS - \mu N$ | $S\to T$, $N\to\mu$ | $-S\,dT - P\,dV - N\,d\mu$ | open systems |

The conjugate pairs are $(T,S)$, $(P,V)$, $(\mu,N)$ — each product has units of energy, which is the check that you have paired them correctly. **You transform the variable you cannot control into the one you can:** a system in a bath has fixed $T$, not fixed $S$, so $F$ rather than $U$ is what is minimized.

**Maxwell relations fall out for free** from equality of mixed second derivatives. From $dF = -S\,dT - P\,dV$:
$$\left(\frac{\partial S}{\partial V}\right)_T = \left(\frac{\partial P}{\partial T}\right)_V$$
There is one such relation per potential, and they are all the statement that $\partial^2 f/\partial x\partial y$ does not care about order.

**Convexity is thermodynamic stability.** $U$ convex in its extensive variables means $C_V > 0$ and $\kappa_T > 0$; where convexity fails the transform convexifies, and the flat region it produces *is* the coexistence region of a first-order phase transition.

## The same move elsewhere

- **Convex optimization** — $f^*$ is the conjugate function, and the dual problem is built from it; strong duality is the statement $f^{**}=f$.
- **Large deviations** — the rate function is the Legendre transform of the cumulant generating function, which is why free energies and rate functions look alike.
- **Statistics** — the cumulant generating function $\log M(t)$ and its transform relate moments to tail probabilities ([[Central Limit Theorem]]).

> [!question]- Why is $F = U - TS$ minimized for a system in a thermal bath, rather than $U$?
> Because you cannot hold $S$ fixed — the bath exchanges energy, so $T$ is the controlled variable. The Legendre transform swaps $S$ for $T$, producing the potential whose natural variables are the ones actually fixed. Minimizing $U$ would answer a question about an isolated system you do not have.

# Connections

- [[Euler-Lagrange Equation]] — the Lagrangian side; the transform that produces $H$
- [[Symplectic Group]] — the phase-space structure the transform buys, and $(q,p)$ as conjugate
- [[Gauge Freedom]] — degenerate transforms and constraints
- [[Thermal States]] — where the thermodynamic potentials get used
- [[Central Limit Theorem]] — cumulant generating functions and their transforms
- [[Optimization and Curve Fitting]] — convex duality in the optimization setting
- [[Positive Semidefinite Matrices]] — convexity as a matrix condition on the Hessian

---
Source: Zia, Redish & McKay, "Making sense of the Legendre transform," *Am. J. Phys.* 77, 614 (2009); Callen, *Thermodynamics and an Introduction to Thermostatistics*, Ch. 5
