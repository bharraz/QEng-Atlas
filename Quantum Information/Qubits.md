#quantum-info

**A qubit is any two-level quantum system you can initialize, control, and read out** — the information lives in the superposition amplitudes and, crucially, their relative phase, which no classical bit has.

# Reference

$|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ with $|\alpha|^2+|\beta|^2=1$; global phase is unphysical, leaving two real parameters:

$$
|\psi\rangle = \cos\tfrac{\theta}{2}|0\rangle + e^{i\phi}\sin\tfrac{\theta}{2}|1\rangle
$$

— the [[Bloch Sphere]] coordinates. **The phase $\phi$ is the quantum resource**: populations alone are a classical coin.

**Physical zoo** (what $|0\rangle, |1\rangle$ actually are):

| Platform | Encoding | Splitting |
|---|---|---|
| Trapped ion | hyperfine clock states (¹⁷¹Yb⁺ 12.6 GHz) or optical S↔D | GHz / THz |
| Transmon | two lowest levels of an anharmonic LC oscillator | ~5 GHz |
| Photon | polarization, path, or time-bin | — |
| Solid-state spin | electron/nuclear spin in a field (NV, Si:P) | MHz–GHz |

Every platform trades coherence time against gate speed and connectivity; the formalism is identical everywhere.

> [!question]- Why isn't a qubit just a noisy classical bit with probability $|\alpha|^2$?
> Because amplitudes interfere: a Hadamard on $(|0\rangle+|1\rangle)/\sqrt2$ gives $|0\rangle$ deterministically, while on a 50/50 *mixture* it gives a coin flip. The relative phase is real, controllable, and measurable.

# Connections

- [[Bloch Sphere]] — the geometry of the single-qubit state space
- [[Two-Level Systems]] — the physics side of the same abstraction: gap + coupling
- [[Hyperfine Structure]] — where the ion qubit actually lives
- [[Single-Qubit Gates]] — the operations that move the state around

---
Source: Nielsen & Chuang, *Quantum Computation and Quantum Information*, §1.2
