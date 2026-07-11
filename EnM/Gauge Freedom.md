#EnM

**The potentials are not unique: shift $\mathbf{A}\to\mathbf{A}+\nabla\chi$ and $V\to V-\partial_t\chi$ and every field — every measurable — is unchanged.** Gauge choice is bookkeeping; pick the one that makes your problem's equations decouple.

# Reference

$$
\mathbf{A}' = \mathbf{A}+\nabla\chi, \qquad V' = V - \frac{\partial\chi}{\partial t} \quad\Rightarrow\quad \mathbf{E}, \mathbf{B} \text{ unchanged}
$$

since $\mathbf{B}=\nabla\times\mathbf{A}$ kills the gradient and $\mathbf{E}=-\nabla V-\partial_t\mathbf{A}$ cancels the rest.

| Gauge | Condition | What you get | Good for |
|---|---|---|---|
| **Coulomb** | $\nabla\cdot\mathbf{A}=0$ | $\nabla^2 V=-\rho/\varepsilon_0$ — instantaneous Coulomb potential; all radiation lives in transverse $\mathbf{A}$ | atoms + quantized light: static Coulomb binds, $\mathbf{A}$ is the photon field (AMO default) |
| **Lorenz** | $\nabla\cdot\mathbf{A}=-\mu_0\varepsilon_0\,\partial_t V$ | symmetric wave equations $\Box V=\rho/\varepsilon_0$, $\Box\mathbf{A}=\mu_0\mathbf{J}$ | radiation, retarded solutions, anything relativistic |

The "instantaneous" Coulomb potential doesn't violate causality — $V$ alone isn't measurable, and the fields assembled from $V$ and $\mathbf{A}$ are properly retarded.

**Physics is gauge invariant, so a gauge-dependent intermediate quantity appearing in a final answer is a bug.** Classic AMO instance: $\mathbf{d}\cdot\mathbf{E}$ vs $\mathbf{p}\cdot\mathbf{A}$ atom–light couplings look different, give the same on-shell rates, and differ off-resonance in ways that confuse people about light shifts — they're related by a gauge(-like) transformation.

> [!question]- Coulomb gauge gives an instantaneous potential $V$. Why doesn't measuring the field near a suddenly-moved charge reveal faster-than-light signaling?
> Because $\mathbf{E}=-\nabla V-\partial_t\mathbf{A}$, and in Coulomb gauge $\partial_t\mathbf{A}$ contains an exactly compensating instantaneous piece. The gauge split is unphysical; only the sum — retarded — is real.

# Connections

- [[Vector Potential]] — the object being regauged; why $\mathbf{A}$ exists at all
- [[Helmholtz Decomposition]] — Coulomb gauge = putting all the longitudinal part into $V$
- [[Retarded Potentials]] — the Lorenz-gauge solution
- [[Generators and the Exponential Map]] — gauge transformations as a symmetry group; U(1) is the prototype

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 10.1; Jackson §6.3
