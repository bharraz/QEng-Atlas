#quantum

**Every qubit state is a point in a unit ball: pure states on the surface, mixed states inside, and every unitary is a rigid rotation.** It turns abstract 2×2 density matrices into geometry you can gesture at.

# Reference

$$
\rho = \frac{\mathbb{1} + \vec{r}\cdot\vec{\sigma}}{2}, \qquad \vec r = (\langle\sigma_x\rangle, \langle\sigma_y\rangle, \langle\sigma_z\rangle), \qquad \mathrm{Tr}\,\rho^2 = \tfrac{1}{2}(1 + |\vec r|^2)
$$

Pure states ($|\vec r| = 1$) parametrized by angles:
$$
|\psi\rangle = \cos\tfrac{\theta}{2}|0\rangle + e^{i\phi}\sin\tfrac{\theta}{2}|1\rangle
$$
Note the **half-angles**: orthogonal states are *antipodal* (180° apart on the sphere, not 90°). $|0\rangle$ north pole, $|1\rangle$ south, $|{\pm}\rangle = (|0\rangle \pm |1\rangle)/\sqrt2$ on the $\pm x$ axis.

**Dynamics = rotation:** $e^{-i\theta\,\hat n\cdot\vec\sigma/2}$ rotates $\vec r$ by $\theta$ about $\hat n$. A resonant Rabi drive rotates about an equatorial axis set by the drive phase; detuning tilts the rotation axis toward $z$; free precession spins about $z$ at the detuning rate. Every pulse sequence is a choreography of these rotations — this is *the* picture for designing composite pulses and reading off echo sequences.

**Decoherence = shrinking:** T2 contracts the equatorial (xy) components, T1 pulls $r_z$ toward the thermal pole. Pure dephasing collapses the ball to the $z$-axis; the maximally mixed state $\mathbb{1}/2$ is the center.

Caveat: this ball is special to 2 levels — for $d \geq 3$ the state space is not a sphere and intuition exported from qubits can lie.

> [!question]- Why do orthogonal states sit at antipodes instead of at right angles?
> The map $|\psi\rangle \to \vec r$ uses half-angles: Hilbert-space angle $\gamma$ becomes Bloch-sphere angle $2\gamma$. $\langle 0|1\rangle = 0$ means 90° in Hilbert space → 180° on the sphere. (Same factor-of-two that makes a $2\pi$ spin rotation give $-1$.)

# Connections

- [[Pauli Matrices]] — the coordinate axes of the ball
- [[Single-Qubit Gates]] — named rotations of this sphere
- [[Density Matrix]] — the object being visualized; $|\vec r|$ is purity
- [[T1 and T2]] — shrink-along-z vs shrink-in-xy, drawn
- [[Rabi Oscillations]] — drive-induced rotation traced on the sphere

---
Source: Nielsen & Chuang, *Quantum Computation and Quantum Information*, §1.2, 4.2
