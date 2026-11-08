#math

**Some properties of a curve, a surface, or a map survive every smooth deformation — the number of times a loop winds around a point, the number of holes in a surface — and because these properties are integers, they cannot change gradually: they can change only where the deformation stops being smooth.** In physics the deformed object is usually a family of quantum states over a parameter space: a Bloch band over the Brillouin zone, or a ground state over a loop of Hamiltonians. Smoothness is guaranteed by a nonzero energy gap, and the integer is computed from Berry phases. "Topologically protected" means that changing the property requires closing the gap or breaking a symmetry — not that nothing can change it.

# Reference

**The winding number.** A closed curve $z(t)$ in the plane that avoids the origin, traversed once:

$$
w = \frac{1}{2\pi}\oint d\theta = \frac{1}{2\pi i}\oint \frac{dz}{z} \in \mathbb{Z}
$$

- $z(t)$ — the curve, as a complex number
- $\theta$ — angle of $z$ seen from the origin (rad)
- $w$ — net number of turns around the origin, counterclockwise positive

Deform the curve however you like; $w$ changes only if the curve passes through the origin, where $\theta$ is undefined ([[Contour Integration and Residues]]).

**Picture:** a rubber band looped around a pole — stretch and move it however you like, and the number of turns around the pole changes only if you cut the band or pass it through the pole.

**The same integer in a Hamiltonian.** A two-band Hamiltonian in one dimension, $H(k) = d_x(k)\sigma_x + d_y(k)\sigma_y$, has energies $\pm\lvert\vec d(k)\rvert$. As $k$ crosses the Brillouin zone, $(d_x, d_y)$ traces a closed curve; the gap is open as long as the curve avoids the origin, and its winding number is a property of the occupied band. Changing the winding means passing through $\vec d = 0$: closing the gap. The SSH chain is this example ([[Topological Phases of Matter]]).

**Degree and Chern number.** A two-band Hamiltonian in two dimensions, $H(\vec k) = \vec d(\vec k)\cdot\vec\sigma$, maps the Brillouin zone (a torus) to directions $\hat d = \vec d/\lvert\vec d\rvert$ on a sphere. The number of times $\hat d$ covers the sphere is an integer:

$$
C = \frac{1}{4\pi}\int_{\mathrm{BZ}} \hat d\cdot\left(\partial_{k_x}\hat d \times \partial_{k_y}\hat d\right) d^2k = \frac{1}{2\pi}\int_{\mathrm{BZ}} \Omega(\vec k)\, d^2k
$$

- $\hat d(\vec k)$ — unit vector of the Hamiltonian at crystal momentum $\vec k$
- $\Omega(\vec k)$ — Berry curvature of the band (m²): integrates over $d^2k$ to a number
- $C$ — Chern number, the same for every smooth gapped deformation

The overall sign depends on which band and which orientation convention is used. The second form, an integral of Berry curvature, applies to any number of bands ([[Berry Phase and Geometric Phases]]).

**Gauss–Bonnet, the model for all of this.** For a closed surface:

$$
\int K\, dA = 2\pi\chi = 2\pi(2 - 2g)
$$

- $K$ — local Gaussian curvature (1/m²)
- $\chi$ — Euler characteristic (dimensionless)
- $g$ — number of handles (genus): 0 for a sphere, 1 for a torus

A quantity defined locally, curvature, integrates to a global integer. Dent a sphere and the curvature rearranges, but its total stays $4\pi$. The Chern number is the same statement for Berry curvature over the Brillouin zone.

**Why a nonzero Chern number is an obstruction.** It is impossible to choose the phases of the Bloch states smoothly over the entire Brillouin zone when $C \neq 0$: any choice has a singular point somewhere, much as a hairy ball cannot be combed flat everywhere. Physically, this is why a band with $C \neq 0$ has no exponentially localized Wannier functions, and why its Berry connection cannot be a single smooth function — only its curvature is.

**Homotopy groups: classifying loops and defects.** Two loops are equivalent if one deforms into the other; the classes form the fundamental group $\pi_1$.

| Space | $\pi_1$ | Physical consequence |
|---|---|---|
| a circle, e.g. the phase of a superfluid order parameter | $\mathbb{Z}$ | vortices with quantized circulation $h/m$ per unit winding |
| $SO(3)$, rotations | $\mathbb{Z}_2$ | a $2\pi$ rotation cannot be undone continuously, but a $4\pi$ rotation can: the reason spinors change sign under $2\pi$ ([[SU(2) and SO(3)]]) |
| $SU(2)$ | trivial | the double cover of $SO(3)$ has no non-contractible loops |
| a sphere $S^2$, e.g. a magnetization direction | trivial; $\pi_2 = \mathbb{Z}$ | no stable vortex lines, but stable point defects (hedgehogs) and skyrmions |

**Symmetry restricts the allowed deformations.** Requiring a symmetry throughout — chiral (sublattice) symmetry, time reversal with $\Theta^2 = -1$, particle–hole symmetry — forbids some deformations and creates invariants that would otherwise be trivial, often valued in $\mathbb{Z}_2$. In the 1D example, chiral symmetry keeps $d_z = 0$; without it the curve could be lifted out of the plane and slid past the origin, and the winding would no longer be protected. This is the meaning of "symmetry-protected" ([[Parity and Time Reversal]]).

**Reading-the-literature glossary:**

| Term | Meaning |
|---|---|
| homotopy | continuous deformation of a map or loop |
| topological invariant | a quantity unchanged by every such deformation |
| winding number, degree | how many times a map wraps its target |
| fibre bundle | a vector space attached to each point of a parameter space: the occupied Bloch states over the Brillouin zone |
| connection, curvature | the Berry connection and its curl, telling how states change from point to point |
| Chern number | integrated curvature: the integer classifying a 2D band |
| $\mathbb{Z}_2$ invariant | an invariant that is only defined, and only takes two values, when a symmetry is imposed |
| obstruction | the impossibility of a smooth global choice of phase |

> [!question]- A 1D two-band model with $H(k) = d_x\sigma_x + d_y\sigma_y$ has a curve $\vec d(k)$ that encircles the origin once. Can you deform it, keeping the gap open, until the curve no longer encircles the origin?
> Not while $d_z = 0$. In the plane, unlinking the curve from the origin requires passing through $\vec d = 0$, where the two bands touch. If a $d_z\sigma_z$ term is allowed, the curve can be lifted out of the plane, moved past the origin, and lowered again without ever reaching $\vec d = 0$, so the gap stays open throughout. The winding number is therefore an invariant only of Hamiltonians with chiral symmetry ($\sigma_z H \sigma_z = -H$); breaking that symmetry removes the protection.

# Connections

- [[Berry Phase and Geometric Phases]] — the connection and curvature that topological invariants integrate
- [[Topological Phases of Matter]] — the physical phases these invariants classify
- [[Degeneracy and Level Crossings]] — gap closings, the only places an invariant can change
- [[Contour Integration and Residues]] — winding numbers in complex analysis
- [[SU(2) and SO(3)]] — $\pi_1(SO(3)) = \mathbb{Z}_2$ and the spinor sign
- [[Lie Groups]] — groups as spaces with their own topology
- [[Gauge Freedom]] — why only the curvature, not the connection, is physical
- [[Parity and Time Reversal]] — the symmetries that make $\mathbb{Z}_2$ invariants possible

---
Source: M. Nakahara, *Geometry, Topology and Physics*, 2nd ed. (2003), Ch. 4 & 9–10; J. K. Asbóth, L. Oroszlány & A. Pályi, *A Short Course on Topological Insulators* (Springer, 2016), Ch. 1–3
