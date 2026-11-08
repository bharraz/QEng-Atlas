#quantum #AMO #solid-state

**Carry a quantum system slowly around a closed loop of its parameters — the direction of a magnetic field, the phases of a pair of lasers, a crystal momentum across the Brillouin zone — and it returns to its starting eigenstate with an extra phase beyond the dynamical $-\int E\,dt/\hbar$.** This geometric phase depends only on the loop's shape, not on its speed or duration. That path-only character makes geometric phases useful for robust gates, and in band structures the same quantity, Berry curvature, underlies the classification of topological matter.

# Reference

**Berry's formula.** Transport an eigenstate $|n(\mathbf{R})\rangle$ adiabatically around a closed loop $C$ in parameter space ([[Adiabatic Theorem]]):

$$
\gamma_n = \oint_C \mathbf{A}_n \cdot d\mathbf{R}, \qquad \mathbf{A}_n = i\langle n|\nabla_{\mathbf{R}}|n\rangle, \qquad \boldsymbol\Omega_n = \nabla_{\mathbf{R}} \times \mathbf{A}_n
$$

- $\mathbf{R}$ — the slowly varied parameters (field direction, laser phases, $\mathbf{k}$)
- $\mathbf{A}_n$ — Berry connection: a vector potential in parameter space
- $\boldsymbol\Omega_n$ — Berry curvature: its curl, the gauge-invariant field strength
- $\gamma_n$ — Berry phase (rad): the flux of $\boldsymbol\Omega_n$ through the loop

Redefining the phases of the eigenstates changes $\mathbf{A}$, much as a gauge transformation changes a vector potential; the loop integral, equivalently the curvature flux, does not ([[Gauge Freedom]]).

**Picture:** carry an arrow around a loop on a globe, never rotating it relative to the surface; it comes back turned by an angle equal to the enclosed solid angle. The quantum state is the arrow, and the Berry phase is that turn.

**A spin following a magnetic field.** A spin-$\tfrac12$ aligned with a field whose direction traces a loop of solid angle $\Theta$ acquires

$$
\gamma = -\frac{\Theta}{2}
$$

- $\Theta$ — solid angle traced by the field direction (sr)
- $\gamma$ — Berry phase of the aligned state (rad); sign depends on convention

For spin $j$ the curvature is that of a monopole of charge $j$ sitting at $\mathbf{B} = 0$, the point where the levels are degenerate ([[Bloch Sphere]]). Two lessons generalize: **degeneracies are the sources of curvature** — near any level crossing the curvature looks like a monopole's — and the phase counts solid angle, a purely geometric quantity ([[Degeneracy and Level Crossings]]).

**Geometric and dynamical phases compared:**

| | Dynamical phase | Geometric phase |
|---|---|---|
| expression | $-\frac{1}{\hbar}\int E(t)\,dt$ | $\oint \mathbf{A}\cdot d\mathbf{R}$ |
| depends on | energies and total time | only the path in parameter space |
| speed or timing noise | enters directly | first-order insensitive |
| reversing the loop | unchanged | changes sign |
| what can corrupt it | any energy fluctuation | anything that deforms the enclosed area |

**Geometric gates.** A phase that depends only on the enclosed area is first-order insensitive to how the loop is traversed: timing and rate noise that would corrupt a dynamical phase leave the area unchanged. The [[Molmer-Sorensen Gate]] uses this in phase space. The spin-dependent loop encloses an area, the area is the entangling phase (the $\Omega_2$ term of the [[Magnus Expansion]]), and closing the loop disentangles the spins from the motion. Adiabatic (Berry) and non-adiabatic (Aharonov–Anandan) geometric single-qubit gates apply the same logic on the Bloch sphere. The protection is real but specific: it covers noise in the path's speed, not noise that deforms its area.

**Berry curvature in crystals.** In a band structure the parameter space is the Brillouin zone, $\mathbf{R} \to \mathbf{k}$, and each band carries a curvature $\Omega_n(\mathbf{k})$. It enters the semiclassical equations of motion as an **anomalous velocity**, completing those of [[Bloch's Theorem and Band Structure]]:

$$
\dot{\mathbf{r}} = \frac{1}{\hbar}\nabla_{\mathbf{k}}E_n - \dot{\mathbf{k}} \times \boldsymbol\Omega_n(\mathbf{k})
$$

- $\mathbf{r}$ — centre of a wavepacket in band $n$ (m)
- $\mathbf{k}$ — its crystal momentum (1/m), driven by applied forces
- $\boldsymbol\Omega_n(\mathbf{k})$ — Berry curvature of band $n$ (m²)

**The topological consequence.** Integrated over the entire zone, the curvature gives an integer — the **Chern number** $C_n = \frac{1}{2\pi}\int \Omega_n\, d^2k \in \mathbb{Z}$ — which no smooth deformation of a gapped band can change. Three results follow:
- the integer quantization of the Hall conductance, $\sigma_{xy} = C e^2/h$ (TKNN);
- **bulk–boundary correspondence**: where regions with different Chern numbers meet, the gap must close at the interface, producing edge states that disorder cannot remove;
- the extension to symmetry-protected classes: time reversal gives $\mathbb{Z}_2$ topological insulators, and particle–hole symmetry gives Majorana modes.

"Topologically protected" means an integer would have to jump. The 1D counterpart is the Zak phase, $\oint \mathbf{A}\cdot d\mathbf{k}$ across the zone, which also underlies the modern theory of electric polarization and the topology of photonic and mechanical bands ([[Topology and Topological Invariants]], [[Topological Phases of Matter]]).

**Reading-the-literature glossary:**
- *Berry connection*: the gauge field.
- *Curvature*: its field strength, concentrated near avoided crossings.
- *Chern number, winding number*: its quantized total.
- *Weyl point*: a 3D band degeneracy acting as a curvature monopole.
- *Anomalous Hall effect, anomalous velocity*: curvature showing up in transport.
- *Holonomic gate*: a geometric phase used for computation.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| phase difference between traversing a loop forwards and backwards | twice the geometric phase: the dynamical part cancels |
| MS gate phase against loop area at fixed duration | the area dependence of the entangling phase |
| spin-echo phase as a field is rotated through a cone | the solid-angle phase, $-\Theta/2$ for spin $\tfrac12$ |
| transverse drift of atoms in an optical lattice under a force | Berry curvature through the anomalous velocity |

> [!question]- Why is a geometric phase robust to timing errors when a dynamical phase is not — both are accumulated phases?
> The dynamical phase is $\int E\,dt$: any fluctuation of $E$ or of the duration integrates directly into it. The geometric phase is a functional of the path only. Traverse the same loop twice as fast, or with a wobbling rate, and the enclosed area — hence the phase — is unchanged. Errors must deform the loop's geometry to matter, a smaller and often controllable class of noise. In the MS gate, laser-detuning jitter changes how fast the phase-space loop is drawn but, to first order at loop closure, not its area.

# Connections

- [[Adiabatic Theorem]] — the transport condition under which Berry's derivation holds
- [[Gauge Freedom]] — the connection–curvature structure, met first in electromagnetism
- [[Molmer-Sorensen Gate]] — a geometric phase as an entangling gate, in phase space
- [[Magnus Expansion]] — the enclosed-area term is $\Omega_2$
- [[Bloch's Theorem and Band Structure]] — semiclassical dynamics completed by the anomalous velocity
- [[Landau-Zener Transitions]] — what happens at the avoided crossings where curvature concentrates
- [[Bloch Sphere]] — solid angle as geometric phase for a two-level system
- [[Degeneracy and Level Crossings]] — degeneracies as the sources of curvature
- [[Topology and Topological Invariants]] — Chern numbers as integrated curvature
- [[Topological Phases of Matter]] — the phases classified by these integers

---
Source: M. V. Berry, *Proc. R. Soc. A* 392, 45 (1984); D. Xiao, M.-C. Chang & Q. Niu, "Berry phase effects on electronic properties," *Rev. Mod. Phys.* 82, 1959 (2010); M. Z. Hasan & C. L. Kane, *Rev. Mod. Phys.* 82, 3045 (2010) (topological insulators)
