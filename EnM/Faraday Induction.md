#EnM

**A changing magnetic flux through a loop drives an emf around it** — and the sign (Lenz) always opposes the change, which is why induction acts like inertia for flux.

# Reference

$$
\mathcal{E} = -\frac{d\Phi_B}{dt}, \qquad \Phi_B = \int \mathbf{B}\cdot d\mathbf{A}, \qquad \nabla\times\mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}
$$

Lenz's law is the minus sign: induced currents flow to oppose the flux change. **Mutual inductance** packages the coupling between two circuits:

$$
\mathcal{E}_2 = -M\frac{dI_1}{dt}, \qquad M_{12} = M_{21}
$$

**This is the mechanism behind magnetic pickup.** Any circuit loop is a one-turn secondary of a transformer whose primary is every nearby dI/dt — mains wiring, switching supplies, RF drives. The induced voltage scales with **loop area** and frequency ($\mathcal{E} = -\dot{B}\,A$ for uniform field), which is why the fix is always: shrink the loop (twist the pair, route signal over its return), not "add more ground."

Self-inductance is the same physics applied to a circuit's own flux: $\mathcal{E} = -L\,dI/dt$ — the origin of inductive kick when you interrupt current through a coil.

> [!question]- Your 60 Hz hum doubles when you move a cable. Capacitive or inductive pickup?
> Inductive — it depends on loop geometry (area, orientation relative to the source), not on impedance to a noisy conductor. Confirm: inductive pickup persists into low-impedance circuits and shrinks when you twist or reroute; capacitive pickup dies when you lower the victim's impedance or add a shield.

# Connections

- [[Noise Coupling Mechanisms]] — induction is the "inductive" row of the four-mechanism table; dI/dt into low-Z loops
- [[Ground Loops]] — two ground paths enclose an area; dΦ/dt around that loop is the hum
- [[Magnetostatics]] — where the B fields you're integrating come from
- [[Maxwell's Equations]] — this is the curl-E equation, promoted from circuit law to field law

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 7.1–7.2
