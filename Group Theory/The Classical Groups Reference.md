#group-theory #reference #math

**Each classical group is the set of invertible linear maps preserving one fixed structure — this is the catalogue: defining condition, algebra, dimension, and where each one shows up.**

The construction that generates every row (fix a form, take its isometry group) is [[Bilinear Forms and Preserved Structures]]; $Sp(2n,\mathbb R)$ in full is [[Symplectic Group]].

# Reference

## The catalogue

$n$ = matrix size; dim = real dimension of the group = number of independent generators.

| Group                         | Defining condition                  | Preserves               | Algebra (generators)     | dim                      | Physics home                                      |
| ----------------------------- | ----------------------------------- | ----------------------- | ------------------------ | ------------------------ | ------------------------------------------------- |
| $GL(n,\mathbb{R}/\mathbb{C})$ | $\det A \neq 0$                     | linear structure only   | all matrices             | $n^2$ / $2n^2$           | basis changes, [[Conjugation]]                    |
| $SL(n)$                       | $\det A = 1$                        | volume                  | traceless matrices       | $n^2-1$                  | area/volume-preserving maps                       |
| $O(n)$                        | $A^{\mathsf T}A = \mathbb{1}$       | lengths, angles         | antisymmetric            | $n(n-1)/2$               | spatial rotations + reflections                   |
| $SO(n)$                       | $+\det = 1$                         | + orientation           | antisymmetric            | $n(n-1)/2$               | proper rotations; $SO(3)$ for space               |
| $U(n)$                        | $A^\dagger A = \mathbb{1}$          | Hermitian inner product | anti-Hermitian           | $n^2$                    | quantum evolution, probability                    |
| $SU(n)$                       | $+\det = 1$                         | + phase convention      | traceless anti-Hermitian | $n^2-1$                  | qubits ($n{=}2$), controllability                 |
| $O(p,q)$                      | $A^{\mathsf T}\eta A = \eta$        | indefinite metric       | $\eta$-antisymmetric     | $\frac{(p+q)(p+q-1)}{2}$ | Lorentz $O(3,1)$; hyperbolic geometry             |
| $SU(1,1)$                     | $A^\dagger \eta A = \eta$, $\det = 1$ | indefinite Hermitian form | $\{a^2, a^{\dagger 2}, a^\dagger a\}$ | $3$    | single-mode squeezing ([[Squeezed States]])        |
| $Sp(2n,\mathbb{R})$           | $A^{\mathsf T}JA = J$               | symplectic form (areas) | $JS$, $S$ symmetric      | $n(2n+1)$                | phase space, Gaussian evolution                   |
| $H_3$ (Heisenberg)            | nilpotent; not a form-preserver     | —                       | $\{a, a^\dagger, \mathbb{1}\}$ | 3            | displacements + phase ([[Displacement Operator]]) |
| $\mathrm{Osc}$                | $H_3 \rtimes U(1)$                  | —                       | $\{a, a^\dagger, \mathbb 1, a^\dagger a\}$ | 4  | free oscillator + linear drive                    |

**Dimension counts the independent operations available:**

- $\dim SU(2) = 3$ — rotation axis and angle on the [[Bloch Sphere]].
- $\dim Sp(2,\mathbb R) = 3$ — squeeze, rotation, shear: the ABCD matrices.
- $\dim Sp(4,\mathbb R) = 10$ — the independent quadratic Hamiltonians on two modes, hence the generator count for universal two-mode Gaussian operations.

**Semidirect products** ($\rtimes$) appear when one factor *acts on* the other instead of commuting with it. $\mathrm{Osc} = H_3 \rtimes U(1)$ is number-phase rotation acting on displacements; the same structure with spin in place of $U(1)$ is the [[Molmer-Sorensen Gate]] at zero detuning — spin acting on displacement, hence a spin-*dependent* displacement.

**Low-dimensional isomorphisms and covers**, used implicitly throughout the literature:

| Relation | Consequence |
|---|---|
| $SU(2) \to SO(3)$, two-to-one | spinors; $4\pi$ periodicity ([[SU(2) and SO(3)]]) |
| $Sp(2,\mathbb R) = SL(2,\mathbb R)$ | in one degree of freedom symplectic reduces to $\det = 1$ — why ABCD matrices need only unit determinant |
| $SU(1,1) \cong Sp(2,\mathbb R)$ | the squeezing group; $\mathfrak{su}(1,1) = \{a^2, a^{\dagger 2}, a^\dagger a\}$ |
| $SL(2,\mathbb C)$ double-covers $SO^+(3,1)$ | spinor representations of the Lorentz group |

## Compactness

| | Groups | Properties | Dynamics |
|---|---|---|---|
| **Compact** | $O(n)$, $SO(n)$, $U(n)$, $SU(n)$ | bounded parameters; invariant (Haar) averaging exists; all irreducible unitary reps finite-dimensional | bounded oscillation |
| **Non-compact** | $GL$, $SL$, $O(p,q)$, $SU(1,1)$, $Sp(2n,\mathbb R)$ | unbounded orbits (boosts, squeezes); no invariant averaging; no faithful finite-dimensional unitary rep | exponential growth |

For a dynamical algebra containing both kinds of generator, which part the combined generator lies in determines the qualitative behavior — the algebraic classification of parametric instability ([[Dynamical Lie Algebras and Closure]]).

> [!question]- Two modes are coupled by two-mode squeezing $a^\dagger b^\dagger + ab$ and by a beamsplitter $a^\dagger b + ab^\dagger$. What follows from compactness alone?
> Both are quadratic, so both sit in $\mathfrak{sp}(4,\mathbb R)$. The beamsplitter generators close into a compact $\mathfrak{su}(2)$: excitation conserved, bounded oscillation between modes. The squeezing generators close into non-compact $\mathfrak{su}(1,1)$: unbounded orbits, exponential photon-number growth.

# Connections

- [[Bilinear Forms and Preserved Structures]] — the form-preservation construction generating each row
- [[Symplectic Group]] — $Sp(2n,\mathbb{R})$ in full
- [[Solving Dynamics on Closed Lie Algebras]] — solution methods once generators close into one of these
- [[Dynamical Lie Algebras and Closure]] — which of these groups a given set of Hamiltonians generates
- [[Lie Groups]] / [[Lie Algebras (Atlas)]] — the general framework
- [[SU(2) and SO(3)]] — the covering map in full
- [[Squeezed States]] / [[Displacement Operator]] — $SU(1,1)$ and $H_3$ acting on a mode
- [[Conjugation]] — the adjoint action of a group on its own algebra

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 1; Gilmore, *Lie Groups, Physics, and Geometry*
