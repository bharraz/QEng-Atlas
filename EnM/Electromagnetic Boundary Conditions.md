#EnM

**At any interface: tangential E and normal B are always continuous; normal D jumps by the surface charge and tangential H jumps by the surface current.** All reflection, refraction, and guided-mode physics is just fields contorting to satisfy these four rules.

# Reference

From pillboxes and loops straddling the interface (Maxwell integral forms):

$$
E^\parallel_1 = E^\parallel_2, \qquad B^\perp_1 = B^\perp_2
$$
$$
D^\perp_2 - D^\perp_1 = \sigma_f, \qquad \mathbf{H}^\parallel_2 - \mathbf{H}^\parallel_1 = \mathbf{K}_f\times\hat{n}
$$

where $\sigma_f$, $\mathbf{K}_f$ are free surface charge and current densities. **No free charge/current (dielectrics): all four are continuity statements** — $\varepsilon_1 E^\perp_1 = \varepsilon_2 E^\perp_2$ means normal E *kinks* at a dielectric interface.

**Perfect conductor limit:** interior fields vanish, so at the surface $E^\parallel = 0$ and $B^\perp = 0$; the fields terminate on induced $\sigma$ and $\mathbf{K}$. This is why:
- reflection off metal flips the tangential E phase (mirrors),
- waveguide/cavity modes must have nodes of $E^\parallel$ at the walls — the boundary conditions *are* the mode quantization,
- a real conductor only approximates this within a [[Skin Depth]].

**Matching wave solutions across an interface** with these conditions is the entire derivation of the [[Fresnel Equations]] — kinematics (phase matching along the surface) gives Snell's law, dynamics (amplitude matching) gives $r$ and $t$.

> [!question]- Why must the tangential E of any wave vanish on a good conductor, and what does that force in a rectangular waveguide?
> Any $E^\parallel$ would drive infinite surface current in a perfect conductor. So guided modes must fit standing-wave patterns with $E^\parallel=0$ on the walls — that fitting condition discretizes the transverse wavevector and creates cutoff frequencies.

# Connections

- [[Fresnel Equations]] — boundary conditions solved for a plane wave at a dielectric interface
- [[Waveguides]] — conductor boundary conditions quantizing transverse modes
- [[Maxwell's Equations]] — the integral forms these are derived from
- [[Skin Depth]] — how deep "the boundary" actually is in a real metal
- [[Cavity Modes]] — same wall conditions, closed on all sides

---
Source: Griffiths, *Introduction to Electrodynamics*, §7.3.6 & §9.3
