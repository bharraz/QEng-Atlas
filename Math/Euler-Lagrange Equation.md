#math

**Demand the action $S=\int L\,dt$ be stationary against any small variation of the path, and the equations of motion fall out** — one recipe that works in any coordinates, needs no force diagrams, and makes symmetries and conservation laws the same fact.

# Reference

$$
\delta S = 0 \;\Rightarrow\; \frac{d}{dt}\frac{\partial L}{\partial \dot q_i} = \frac{\partial L}{\partial q_i}, \qquad L = T - V
$$

**Picture:** of all paths between two fixed endpoints, the physical one is where small wiggles change the action only at second order, like the bottom of a valley.

**Worked one-liner:** $L = \tfrac{1}{2}m\dot x^2 - V(x)$ gives $m\ddot x = -V'(x)$ — Newton back in one line. The advantage is generalized coordinates: write $T-V$ in whatever angles/lengths fit the constraints, and the machinery handles the rest (no constraint forces ever appear).

**Cyclic coordinate = free conservation law:** if $\partial L/\partial q = 0$, then $p \equiv \partial L/\partial\dot q$ is conserved — no further derivation is needed. **Noether generalizes it:** every continuous symmetry of $L$ yields a conserved quantity — time translation → energy, space translation → momentum, rotation → angular momentum. This is the classical counterpart of symmetry generators in QM.

**Standard workflow for small oscillations:** write $L$, expand $V$ to second order about equilibrium, get coupled linear EOM, diagonalize → normal modes. This is how ion-chain mode structure is derived.

**Dissipation has no Lagrangian:** $\gamma\dot x$ breaks time-reversal symmetry of $S$. Add damping by hand afterward (or via Rayleigh dissipation function).

> [!question]- Why does a coordinate that doesn't appear in $L$ give a conserved quantity?
> The E-L equation reads $\dot p = \partial L/\partial q = 0$ directly, so $p = \partial L/\partial\dot q$ is constant. "Doesn't appear in $L$" means $L$ is symmetric under shifting that coordinate — the simplest case of Noether's theorem.

# Connections

- [[Generators and the Exponential Map]] — Noether's symmetries are these generators; conserved charge = generator of the symmetry
- [[Normal Modes of Ion Chains]] — derived exactly by the small-oscillation workflow above
- [[Taylor Expansion]] — expanding $V$ about equilibrium is step one of every small-oscillation problem

---
Source: Landau & Lifshitz, *Mechanics*, Ch. 1–2 (Least action; conservation laws)
