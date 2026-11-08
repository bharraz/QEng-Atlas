#linear-algebra #math

**An operator is a linear map whose inputs and outputs are vectors — $d/dx$ takes a function and returns a function — and a superoperator is one rung up, a linear map on operators; the entire matrix toolkit applies at every rung because linearity is the only structure it ever used.**

This is the mathematician's version of [[Operators and Observables]]: same machinery, no $\hbar$ required.

# Reference

| Rung | Maps | Example spaces | Examples |
|---|---|---|---|
| Vector | — | $\mathbb R^n$, $L^2$ | states, signals, wavefunctions |
| **Operator** | vectors → vectors | matrices; $d/dx$ on functions | $H$, filters, $\nabla^2$ |
| **Superoperator** | operators → operators | matrices on vectorized matrices | $[H,\cdot\,]$, Lindbladian, channels |

**Picture:** a ladder of linear maps: vectors at the bottom, operators acting on vectors one rung up, superoperators acting on operators above that, and the same matrix methods on every rung.

Membership requires only $L(\alpha f + \beta g) = \alpha Lf + \beta Lg$. Eigenvectors, spectral decomposition, exponentials and the resolvent are consequences of linearity plus an inner product, so they climb the ladder unchanged.

## $d/dx$ as the archetype

| Fact about $D = d/dx$ | Consequence |
|---|---|
| $D\,e^{\lambda x} = \lambda e^{\lambda x}$ | exponentials are $D$'s eigenfunctions — **this is why Fourier and Laplace transforms exist**: they are the change of basis to $D$'s eigenbasis, where differentiation becomes multiplication ($\dot x \leftrightarrow i\omega X$) and linear constant-coefficient ODEs become algebra ([[Fourier Transform]], [[Laplace Transform]]) |
| $e^{aD}f(x) = f(x+a)$ | **differentiation generates translation** — the Taylor series read as a group action. The quantum $e^{-ia\hat p/\hbar}$ is this identity with $\hat p = -i\hbar D$ ([[Generators and the Exponential Map]]) |
| $[D, x] = 1$ | non-commutation with no quantum mechanics in sight — it is the product rule. $\hbar$ scales the structure, it does not create it |

Other members of the same category:

- **Convolution with a kernel** — every LTI system ([[Impulse and Frequency Response]]), diagonalized by the Fourier basis for the same eigenfunction reason.
- **Integral operators** $f \mapsto \int K(x,y)f(y)\,dy$ — [[Green's Functions]] are inverses of differential operators in this sense.
- **Shift/delay** — $z^{-1}$ in discrete time.

**What infinite dimension changes** — three items, all of which matter in practice:

1. **Spectra need not be discrete.** $D$ on the full line has continuous spectrum and non-normalizable "eigenfunctions" $e^{ikx}$; the [[Dirac Delta]] formalism is the accounting system for this.
2. **Boundary conditions are part of the operator.** $-iD$ on $[0,L]$ with periodic, Dirichlet, or open boundaries are *different operators* with different spectra — the operational meaning of "domain," and why [[Sturm-Liouville Theory]] fixes an interval and boundary conditions before promising an orthogonal basis.
3. **Hermitian $\neq$ self-adjoint.** Symmetric under the inner product is not enough for the spectral theorem; domains must match too. Practical flag: momentum on a half-line has *no* self-adjoint version, which is why radial momentum in 3D needs care and some "obvious" observables do not exist.

## Superoperators

| Superoperator | Definition | Role |
|---|---|---|
| $\mathrm{ad}_H$ | $[H, \cdot\,]$ | generator of Heisenberg-picture evolution; its exponential is [[Conjugation\|conjugation]], $e^{\mathrm{ad}_A}B = e^ABe^{-A}$ |
| Liouvillian $\mathcal L$ | $-\tfrac{i}{\hbar}[H,\rho] + \sum_k \mathcal D[L_k]\rho$ | generator of open-system dynamics ([[Lindblad Master Equation]]) |
| Channel $\mathcal E$ | $\sum_k E_k \rho E_k^\dagger$ | the finite-time map ([[Quantum Channels]]) |
| Transfer operator | acts on probability densities | the classical analog — same structure, probability for amplitude |

**Vectorization makes them matrices.** Stack an $n\times n$ operator's columns into a length-$n^2$ vector:
$$|A\rho B\rangle\rangle = (B^{\mathsf T}\otimes A)\,|\rho\rangle\rangle$$
Every superoperator is then an $n^2\times n^2$ matrix and all rung-two machinery applies verbatim: eigenvalues of $\mathcal L$ are decay rates, its zero-eigenvector the steady state, $e^{\mathcal L t}$ the propagator via `expm`, spectral gaps the mixing times. Two costs:

- **Dimension squares** — $4^N$ for $N$ qubits, the ceiling drop in [[Exact Diagonalization and Sparse Methods]].
- **Generically non-normal** — Liouvillians need Schur-side tools, not the spectral theorem ([[Matrix Decompositions in Practice]]).

**Structure that exists only at rung three:** Hermiticity preservation, trace preservation and complete positivity are properties *of the map*, invisible at the operator level — the CPTP conditions for a physical evolution.

> [!question]- Fourier solves linear ODEs, the interaction picture simplifies driven Hamiltonians, and diagonalizing $\mathcal L$ gives decay rates. What single move is shared?
> Change basis to the eigenbasis of the relevant operator, at whichever rung it lives: $d/dt$ on signals (rung two), $\mathrm{ad}_{H_0}$ on operators (rung three — hence phases $e^{i\omega_{jk}t}$ at the Bohr frequencies), $\mathcal L$ on density matrices (rung three).

# Connections

- [[Operators and Observables]] — the quantum counterpart; Hermitian/unitary/normal taxonomy
- [[Sturm-Liouville Theory]] — differential operators with boundary conditions as self-adjoint eigenproblems
- [[Fourier Transform]] / [[Laplace Transform]] — changes of basis to $D$'s eigenbasis
- [[Green's Functions]] — inverses of differential operators
- [[Generators and the Exponential Map]] — $e^{aD}$ as translation
- [[Conjugation]] — $e^{\mathrm{ad}}$ as the bridge between rungs two and three
- [[Vectorization and Superoperators]] — the flattening that turns rung three into rung two
- [[Lindblad Master Equation]] / [[Quantum Channels]] — the physical superoperators
- [[Matrix Decompositions in Practice]] — why Liouvillians need non-normal tools

---
Source: Stone & Goldbart, *Mathematics for Physics*, Ch. 4–5 (domains, self-adjointness); Wiseman & Milburn, *Quantum Measurement and Control*, App. A (superoperators, vectorization)
