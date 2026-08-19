#group-theory #quantum #math

**Every continuous symmetry generator is a conserved quantity — so a symmetry group's dimension counts the conservation laws, and its Casimirs label the degeneracies.**

The cleanest demonstration of why Lie theory is worth learning: the same object is the symmetry generator, the conserved observable, and the label on the multiplet.

# Reference

**Classical statement.** If the action is invariant under $q \to q + \epsilon\, X(q)$ for a continuous parameter $\epsilon$, then
$$Q = \frac{\partial L}{\partial \dot q}\cdot X(q) \qquad \text{satisfies} \qquad \frac{dQ}{dt} = 0.$$
$X$ is the infinitesimal generator of the symmetry — an element of the symmetry algebra — and $Q$ is the conserved charge built from it. **One charge per generator**, so $\dim\mathfrak g$ = number of independent conservation laws.

**Quantum statement**, and it is shorter:
$$[H, G] = 0 \iff G \text{ is conserved}$$
which is $\mathrm{ad}_H\, G = 0$: the conserved observables are exactly the kernel of $\mathrm{ad}_H$ ([[Conjugation]], [[Operators and Superoperators]]). Since $G$ generates the symmetry via $e^{i\theta G}$ and commutes with $H$, "generates a symmetry" and "is conserved" are the same equation read in two directions ([[Generators and the Exponential Map]]).

| Symmetry | Group | Generator | Conserved |
|---|---|---|---|
| Time translation | $\mathbb R$ | $H$ | energy |
| Space translation | $\mathbb R^3$ | $\hat p$ | momentum |
| Rotation | $SO(3)$ / $SU(2)$ | $\hat L$, $\hat J$ | angular momentum |
| Global phase | $U(1)$ | $\hat N$ | particle number / charge |
| Boost | $SO^+(3,1)$ | $K_i$ | (no static charge — mixes $t$) |
| Scaling | $\mathbb R^+$ | dilatation $D$ | conformal weight |

**The continuity requirement is not decoration.** The proof differentiates with respect to the group parameter, so a discrete symmetry has nothing to differentiate. Parity and time reversal give conserved *quantum numbers* and selection rules, but no Noether current ([[Lie Groups]]). This is the sharpest illustration of why the smoothness in "Lie group" is doing work.

## Degeneracy is a representation statement

The part usually left implicit, and the reason this belongs with group theory rather than mechanics:

- If $G$ commutes with $H$, it maps each energy eigenspace to itself. **So every energy eigenspace carries a representation of the symmetry group.**
- Decompose it into irreducibles: **degeneracy = dimension of the irrep** ([[Group Representations]]).
- The **Casimirs** of the symmetry algebra label which irrep, hence which multiplet — and being in the center of $U(\mathfrak g)$, they commute with every Hamiltonian built from $\mathfrak g$ ([[Universal Enveloping Algebra and PBW Basis]]).

So rotational symmetry does not merely conserve $\hat J$; it *forces* levels to come in $(2j+1)$-fold multiplets labeled by $J^2 = j(j+1)$. Symmetry predicts the spectrum's shape before any dynamics is solved.

**Run the argument backwards and it becomes a discovery tool.** Degeneracy you cannot explain from the obvious symmetry means the *actual* symmetry algebra is larger than you assumed:

| System | Naive symmetry | Actual | The extra generator |
|---|---|---|---|
| Hydrogen ($1/r$) | $SO(3)$, degeneracy $2\ell+1$ | $SO(4)$, degeneracy $n^2$ | conserved Runge–Lenz vector |
| Isotropic oscillator, $n$ modes | $SO(n)$ | $SU(n)$ | quadrupole-type $a_i^\dagger a_j$ |
| Landau levels | translations | magnetic translation algebra | non-commuting guiding-center coordinates |

"Accidental degeneracy" is almost always a hidden symmetry. The hydrogen $n^2$ degeneracy is $SO(4)$'s irrep dimension, not an accident, and the oscillator's $\mathfrak{su}(n)$ is why the $a_i^\dagger a_j$ operators close ([[Dynamical Lie Algebras and Closure]]).

## What to check before invoking it

| Requirement | If it fails |
|---|---|
| Symmetry is **continuous** | conserved quantum number and selection rules, no current |
| Symmetry of the **action**, not just $H$ | quasi-symmetries give charges up to boundary terms |
| Symmetry is **global** (constant parameter) | a *local* (gauge) symmetry gives Noether's **second** theorem: constraints and identities, not independent charges |
| Symmetry is **exact** | approximate symmetry ⇒ approximate conservation; the breaking size sets the leak rate |

The gauge row is worth stating plainly: gauge symmetry does not produce new conserved charges but relations among the equations of motion — which is why gauge redundancy reduces degrees of freedom rather than adding constants of motion.

**Approximate symmetry is the working case in the lab.** Rotating-frame or averaged Hamiltonians have symmetries the full $H$ lacks; the resulting conservation holds to the order at which the approximation holds, which is exactly the truncation-legitimacy question ([[Graded and Filtered Lie Algebras]], [[Rotating Wave Approximation (Atlas)]]). A "conserved" quantity in an effective theory is conserved to the order the effective theory is valid, and no further.

> [!question]- A level shows $n^2$-fold degeneracy where the rotational symmetry only predicts $2\ell+1$. What do you conclude, and what do you look for?
> The symmetry algebra is larger than $\mathfrak{so}(3)$ — degeneracy is an irrep dimension, so an irrep of dimension $n^2$ means extra generators commuting with $H$. Look for another conserved vector operator; for $1/r$ it is Runge–Lenz, extending $\mathfrak{so}(3)$ to $\mathfrak{so}(4)$.

# Connections

- [[Lie Groups]] — why continuity is required; the discrete-symmetry contrast
- [[Lie Algebras (Atlas)]] — generators as the conserved observables; Casimirs and rank
- [[Group Representations]] — degeneracy as irrep dimension; Schur's lemma
- [[Universal Enveloping Algebra and PBW Basis]] — Casimirs as the center, hence multiplet labels
- [[Cartan Subalgebras, Roots, and Weights]] — weights as the good quantum numbers within a multiplet
- [[Symmetry in Quantum Mechanics]] — the physics-side treatment of good quantum numbers
- [[Conjugation]] — $[H,G]=0$ as $\mathrm{ad}_H G = 0$; symmetry as invariance under the adjoint action
- [[Euler-Lagrange Equation]] — the variational setting the classical theorem lives in
- [[Dynamical Lie Algebras and Closure]] — closure of the symmetry algebra; hidden symmetries as extra generators

---
Source: Zee, *Group Theory in a Nutshell for Physicists*, Ch. IV; Goldstein, *Classical Mechanics*, §13.7; Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 4 (degeneracy and irreps)
