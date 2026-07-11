#math

**Both say the same thing: the integral of a derivative over a region equals the field evaluated on the boundary** — divergence theorem trades volume for enclosing surface, Stokes trades surface for bounding loop. They're the dictionary between the integral and differential forms of Maxwell.

# Reference

**Divergence theorem** (volume ↔ closed surface):
$$
\int_V (\nabla\cdot\mathbf{F})\, dV = \oint_S \mathbf{F}\cdot d\mathbf{a}
$$

**Stokes' theorem** (open surface ↔ bounding loop):
$$
\int_S (\nabla\times\mathbf{F})\cdot d\mathbf{a} = \oint_C \mathbf{F}\cdot d\mathbf{l}
$$

**Orientation conventions** (sign errors live here):
- Divergence theorem: $d\mathbf{a}$ points **outward** from the enclosed volume.
- Stokes: curl fingers of right hand along the loop direction $d\mathbf{l}$; thumb gives $d\mathbf{a}$. Equivalently, walk the loop with the surface on your left, normal up.
- Any open surface with the same boundary gives the same Stokes integral — curl fields have zero flux through closed surfaces.

**Converting Maxwell:** apply the divergence theorem to Gauss's law and the flux through $S$ becomes $\int \rho\, dV/\varepsilon_0$, so $\nabla\cdot\mathbf{E} = \rho/\varepsilon_0$; apply Stokes to Faraday's loop law and $\oint\mathbf{E}\cdot d\mathbf{l} = -d\Phi_B/dt$ becomes $\nabla\times\mathbf{E} = -\partial_t\mathbf{B}$. Because the region is arbitrary, integrands must match pointwise — that step is the whole conversion.

**Practical direction:** differential forms for deriving (wave equation, boundary conditions), integral forms for symmetric geometry (Gauss pillboxes, Amperian loops) and for interfaces where derivatives blow up.

> [!question]- Why does the same magnetic flux answer come out for any open surface spanning a given loop?
> Two surfaces with the same boundary form a closed surface; the flux difference through them is $\oint(\nabla\times\mathbf{F})\cdot d\mathbf{a}$ over that closed surface $= \int\nabla\cdot(\nabla\times\mathbf{F})\,dV = 0$, since div curl vanishes identically.

# Connections

- [[Maxwell's Equations]] — these theorems are how the integral and differential forms interconvert
- [[Divergence]] — the local quantity the divergence theorem globalizes
- [[Curl]] — the local quantity Stokes globalizes
- [[Faraday Induction]] — the loop law is Stokes applied to ∇×E

---
Source: Griffiths, *Introduction to Electrodynamics*, §1.3.4–1.3.5
