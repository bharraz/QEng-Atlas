#group-theory #math

**A Lie group is a group whose elements depend smoothly on continuous parameters — a group that is also a smooth surface, so you can rotate by any angle rather than in discrete steps.** Continuous symmetry lives here, and continuous symmetry is what produces conservation laws.

# Reference

Formally a Lie group is a group that is also a differentiable manifold, with multiplication and inversion smooth. The practical content: elements sit arbitrarily close to the identity, so you can reach any of them by accumulating infinitesimal steps.

**The dimension** of a Lie group is the number of independent continuous parameters — the number of knobs.

| Group | Elements | Dimension | Where it shows up |
|---|---|---|---|
| $U(1)$ | phases $e^{i\theta}$ | 1 | electromagnetic gauge symmetry, any overall phase |
| $SU(2)$ | $2\times2$ unitary, $\det=1$ | 3 | spin, qubits, isospin |
| $SO(3)$ | rotations of 3D space | 3 | rigid-body and orbital rotations |
| $SU(3)$ | $3\times3$ unitary, $\det=1$ | 8 | color (QCD), flavor |
| Poincaré | Lorentz boosts + rotations + translations | 10 | relativistic spacetime symmetry |

**Compact vs non-compact**: rotations form a compact group (the parameter space is bounded — angles wrap around), which is why their representations are finite-dimensional and unitary. Lorentz boosts are non-compact (rapidity runs to infinity), which is why there is no finite-dimensional unitary representation of the Lorentz group.

## Covering groups — same algebra, different topology

The Lie algebra fixes a group only *locally*. Groups sharing one algebra differ in global topology, and among them there is a unique simply connected one — the **universal cover** — of which the others are quotients by a discrete subgroup of the center:

| Cover | Covered group | Kernel | Physics |
|---|---|---|---|
| $SU(2)$ | $SO(3) = SU(2)/\mathbb{Z}_2$ | $\{\pm\mathbb{1}\}$ | spin vs orbital rotations |
| $\mathbb{R}$ | $U(1) = \mathbb{R}/2\pi\mathbb{Z}$ | $2\pi\mathbb{Z}$ | phase winding |
| $SL(2,\mathbb{C})$ | Lorentz group $SO^+(3,1)$ | $\{\pm\mathbb{1}\}$ | relativistic spinors |

Why it matters physically: quantum states are rays, so a symmetry need only be represented **up to a phase** — projective representations of $G$ are ordinary representations of its universal cover. That is the precise reason spin-1/2 exists: it is not a representation of $SO(3)$ at all, but of $SU(2)$ (see [[SU(2) and SO(3)]]). Loops in the group that cannot be contracted (the non-trivial $\pi_1$) are exactly what the cover unwinds; the $2\pi$ rotation is such a loop in $SO(3)$.

## Building bigger groups

- **Direct product** $G \times H$: independent symmetries, commuting factors — e.g. $SU(2)_{\text{spin}} \times SO(3)_{\text{orbit}}$ before spin-orbit coupling locks them into the diagonal subgroup.
- **Semidirect product** $G \ltimes H$: one factor acts on the other — the Euclidean group (rotations acting on translations) and the Poincaré group are the standard cases; the commutator of a rotation and a translation is another translation, so the factors don't decouple.

Why the continuity matters: a continuous symmetry can be built from infinitesimal ones, and each infinitesimal generator is a conserved quantity (Noether). The generators and their commutation relations — the [[Lie Algebras|Lie algebra]] — hold essentially all the local structure, which is why physicists work with the algebra and exponentiate back to the group.

> [!question]- Why can a discrete symmetry (like parity) not give a conservation law by Noether's theorem, while a rotation can?
> Noether's theorem needs a continuous family of symmetries so it can take a derivative with respect to the parameter and build a conserved current. A discrete symmetry has no parameter to differentiate. Rotations form a Lie group with a continuous angle; parity is a single isolated element with no neighborhood — it gives a conserved *quantum number* (parity eigenvalue) but not a Noether current.

# Connections

- [[Lie Algebras]] — the infinitesimal version; the generators and their commutators
- [[Generators and the Exponential Map]] — how $e^{-i\theta G}$ turns a generator into a group element
- [[SU(2) and SO(3)]] — the two three-dimensional Lie groups you meet first, and their subtle relationship
- [[(Atlas) Group Theory]] — the discrete-friendly axioms these also satisfy
- [[Unitary Matrices]] — $U(N)$ and $SU(N)$ are the unitary Lie groups

---
Source: Hall, *Lie Groups, Lie Algebras, and Representations*, Ch. 1; Zee, *Group Theory in a Nutshell*, Ch. IV
