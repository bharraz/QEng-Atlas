#solid-state #quantum

**Cool a magnet through its Curie temperature, or tune the field on a chain of spins past a critical value, and a property that was zero becomes nonzero — a magnetization, a condensate amplitude — while the system's response diverges at the transition itself.** Near a continuous transition, fluctuations grow correlated over ever larger distances, and the behaviour stops depending on microscopic details: systems as different as a liquid at its critical point and a uniaxial magnet share the same exponents. Phase transitions are where simulators prepare interesting states, where adiabatic preparation becomes slow, and where defects are created by finite ramps.

# Reference

**Order parameter and symmetry breaking.** An order parameter $m$ is zero in the disordered phase and nonzero in the ordered one: magnetization in a ferromagnet, the condensate wavefunction in a superfluid. A Hamiltonian with a symmetry — spin flip, phase rotation — can have ground states that do not share it; the system chooses one, and the symmetry is broken ([[Symmetry in Quantum Mechanics]]).

**Landau theory.** Near a transition, expand the free energy in the order parameter, keeping the terms the symmetry allows:

$$
F(m) = F_0 + a\,(T - T_c)\,m^2 + b\,m^4 - h\,m
$$

- $m$ — order parameter (units of the quantity: magnetization, amplitude)
- $T_c$ — critical temperature (K)
- $a, b$ — positive constants, material-specific
- $h$ — field conjugate to $m$, which breaks the symmetry explicitly

Above $T_c$ the minimum is at $m = 0$; below, at $m = \pm\sqrt{a(T_c - T)/2b}$. A negative $m^4$ coefficient, or a symmetry-allowed $m^3$ term, makes the transition first order, with a jump in $m$ and latent heat.

**Picture:** a ball in a bowl whose bottom slowly rises into a bump as the system cools — the centre becomes a hilltop, and the ball has to roll off to one side.

**Continuous versus first-order transitions:**

| | Continuous (second order) | First order |
|---|---|---|
| order parameter at $T_c$ | rises continuously from zero | jumps |
| correlation length $\xi$ | diverges | stays finite |
| latent heat | none | nonzero |
| metastability, hysteresis | none | yes: supercooling, superheating |
| examples | Curie point, superfluid He, BEC, superconductivity in zero field | melting, boiling away from the critical point, many structural transitions |

**Critical exponents and universality.** Near a continuous transition, with $\tau = (T - T_c)/T_c$:

$$
\xi \propto \lvert\tau\rvert^{-\nu}, \qquad m \propto (-\tau)^{\beta}, \qquad \chi \propto \lvert\tau\rvert^{-\gamma}
$$

- $\xi$ — correlation length (m): distance over which fluctuations are correlated
- $\chi$ — susceptibility: response of $m$ to $h$
- $\nu, \beta, \gamma$ — critical exponents

The exponents depend only on the dimension, the symmetry of the order parameter, and whether interactions are short-range — the **universality class** — not on microscopic details:

| Class | Order parameter | $\beta$ | $\nu$ | Example |
|---|---|---|---|---|
| mean field (Landau) | any | 1/2 | 1/2 | long-range interactions; above four dimensions |
| 2D Ising | one component, $\pm$ | 1/8 | 1 | adsorbed monolayers, 2D uniaxial magnets |
| 3D Ising | one component | 0.326 | 0.630 | uniaxial magnets, liquid–gas critical point |
| 3D XY | two components (a phase) | 0.348 | 0.672 | superfluid $^4$He |
| 3D Heisenberg | three components | 0.37 | 0.71 | isotropic ferromagnets |

**Low dimensions.** A continuous symmetry cannot be spontaneously broken at nonzero temperature in one or two dimensions with short-range interactions (Mermin–Wagner). In 2D the XY model instead has a Berezinskii–Kosterlitz–Thouless transition: bound vortex–antivortex pairs unbind above $T_\text{BKT}$, a transition driven by topological defects rather than by a local order parameter ([[Topology and Topological Invariants]]).

**Quantum phase transitions.** At zero temperature a parameter $g$ in the Hamiltonian — a transverse field, a hopping-to-interaction ratio — can drive a transition through quantum rather than thermal fluctuations. The 1D transverse-field Ising chain $H = -J\sum Z_iZ_{i+1} - h\sum X_i$ orders for $h < J$ and is paramagnetic for $h > J$. Near the critical point $g_c$:
- **The gap closes,** as $\Delta \propto \lvert g - g_c\rvert^{z\nu}$, and in a finite system of size $L$ the minimum gap scales as $L^{-z}$.
- **The dynamical exponent $z$** relates time to space. A $d$-dimensional quantum transition behaves like a classical one in $d + z$ dimensions.
- **At finite temperature** a "quantum critical" region fans out above $g_c$, where temperature is the only scale.

Superfluid–Mott transitions in lattices are quantum phase transitions ([[Hubbard Models and Mott Insulators]], [[Spin Chains and Magnons]]).

**Crossing a transition at finite speed: Kibble–Zurek.** Ramping through a continuous transition over a time $\tau_Q$, the system cannot follow once its relaxation time exceeds the time left to the transition. It freezes, leaving domains of size $\hat\xi \propto \tau_Q^{\nu/(1+z\nu)}$, so the density of defects scales as

$$
n_\text{defects} \propto \tau_Q^{-d\nu/(1+z\nu)}
$$

- $\tau_Q$ — ramp (quench) time across the transition (s)
- $d$ — number of spatial dimensions

This is the same gap closing that limits adiabatic state preparation: preparing an ordered ground state by a slow ramp takes a time that grows with system size ([[Adiabatic Theorem]], [[Quench Dynamics and Thermalization]]).

**Beyond Landau.** Topological phases have no local order parameter and break no symmetry, so they fall outside this framework ([[Topological Phases of Matter]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| order parameter against temperature or coupling | the transition point and $\beta$ |
| peak in susceptibility or heat capacity | the location of the transition; its sharpening with size, the exponents |
| correlation function from snapshots or scattering | $\xi$, and its divergence at the transition |
| curves for different system sizes collapsing onto one when rescaled | the exponents and the universality class (finite-size scaling) |
| defect density against ramp time | the Kibble–Zurek exponent $d\nu/(1+z\nu)$ |
| hysteresis between up- and down-sweeps | a first-order transition |

> [!question]- A simulator ramps the transverse-field Ising chain from the paramagnet into the ordered phase. Doubling the ramp time does not halve the number of domain walls. Why not, and what does the scaling tell you?
> Near the critical point the gap closes, so no finite ramp is adiabatic there; the system freezes when its relaxation time exceeds the remaining ramp time and leaves domains of size $\hat\xi$. For the 1D transverse-field Ising chain $\nu = z = 1$, so the defect density scales as $\tau_Q^{-1/2}$: doubling the ramp time reduces it only by $\sqrt2$. Measuring that exponent tests whether the dynamics is in the Kibble–Zurek regime and which universality class the transition belongs to.

# Connections

- [[Symmetry in Quantum Mechanics]] — the symmetries that order breaks
- [[Bose-Einstein Condensation]] — a transition with a phase as order parameter
- [[Superconductivity]] — a charged condensate and its transition
- [[Magnetism in Solids]] — the standard ordered phases
- [[Hubbard Models and Mott Insulators]] — the superfluid–Mott quantum phase transition
- [[Spin Chains and Magnons]] — transverse-field Ising and Heisenberg chains
- [[Quench Dynamics and Thermalization]] — dynamics after sudden and finite-speed changes
- [[Adiabatic Theorem]] — why gap closing slows state preparation
- [[Topological Phases of Matter]] — phases with no local order parameter
- [[Legendre Transform]] — the thermodynamic potentials whose derivatives jump or diverge

---
Source: N. Goldenfeld, *Lectures on Phase Transitions and the Renormalization Group* (1992); S. Sachdev, *Quantum Phase Transitions*, 2nd ed. (2011); W. H. Zurek, *Phys. Rep.* 276, 177 (1996); A. Pelissetto & E. Vicari, *Phys. Rep.* 368, 549 (2002) (exponent values)
