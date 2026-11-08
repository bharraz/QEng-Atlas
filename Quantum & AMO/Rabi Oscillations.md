#AMO

**Drive a two-level atom with light close to its transition frequency and the population moves back and forth between the two levels, at a rate set by the light's field strength and its detuning.** In the drive's rotating frame this is the Bloch vector precessing about a fixed axis. It is the primitive behind every single-qubit gate and every pulse calibration.

# Reference

**Population starting in $|g\rangle$**, in the rotating frame, with detuning $\Delta = \omega_L - \omega_0$ and Rabi frequency $\hbar\Omega = -\langle e|\vec d\cdot\vec E_0|g\rangle$:

$$
P_e(t) = \frac{\Omega^2}{\Omega^2 + \Delta^2}\,\sin^2\!\left(\frac{\tilde\Omega\, t}{2}\right), \qquad \tilde\Omega = \sqrt{\Omega^2 + \Delta^2}
$$

- $P_e$ — excited-state population (dimensionless probability)
- $\Omega$ — resonant Rabi frequency (rad/s), $\propto d\sqrt{I}$: dipole matrix element × field amplitude
- $\Delta$ — detuning (rad/s)
- $\tilde\Omega$ — generalized Rabi frequency (rad/s): length of the drive vector $(\Omega, 0, \Delta)$

The prefactor $\Omega^2/\tilde\Omega^2$ is the squared sine of that vector's tilt from the $z$ axis: the contrast is set by the *ratio* $\Omega/\Delta$, the rate by the *magnitude*. A $\pi$-time therefore scales as $1/\Omega \propto 1/\sqrt{I}$; quadrupling the laser power halves the pulse time.

**Picture:** Rabi flops are a spin precessing in a magnetic field, the field vector being the drive vector $(\Omega, 0, \Delta)$ ([[Bloch Sphere]]).

**Any starting state.** With $H = \frac{\hbar}{2}(\Omega\sigma_x - \Delta\sigma_z)$ and $\sigma_z = |e\rangle\langle e| - |g\rangle\langle g|$, the evolution over time $t$ is a rotation:

$$
U(t) = \cos\frac{\tilde\Omega t}{2}\,\mathbb{1} - i\sin\frac{\tilde\Omega t}{2}\;\frac{\Omega\sigma_x - \Delta\sigma_z}{\tilde\Omega}
$$

- $U(t)$ — evolution operator in the rotating frame: apply it to $(c_e, c_g)$
- $\mathbb{1}$ — the identity: the part of the state left unchanged
- $(\Omega\sigma_x - \Delta\sigma_z)/\tilde\Omega$ — the rotation axis, a unit vector

so $c_e(t) = \big[\cos\frac{\tilde\Omega t}{2} + i\frac{\Delta}{\tilde\Omega}\sin\frac{\tilde\Omega t}{2}\big]c_e(0) - i\frac{\Omega}{\tilde\Omega}\sin\frac{\tilde\Omega t}{2}\,c_g(0)$, and $c_g(t)$ follows with $\Delta \to -\Delta$ and $e \leftrightarrow g$. Phase conventions for $\Omega$ and the sign of $\Delta$ differ between texts by a frame factor $e^{\pm i\Delta t/2}$ ([[Conventions and Factor-of-Two Traps]]).

**On resonance** ($\Delta = 0$): full-contrast flopping, $P_e = \sin^2(\Omega t/2)$.
- **$\pi$ pulse** ($\Omega t = \pi$): complete inversion $|g\rangle \to |e\rangle$.
- **$\pi/2$ pulse**: an equal superposition — the beamsplitter of [[Ramsey Interferometry]].

**Detuned:** the oscillation *speeds up* ($\tilde\Omega > \Omega$) but its contrast drops to $\Omega^2/(\Omega^2+\Delta^2)$. Geometrically, the precession axis $(\Omega, 0, \Delta)$ tilts out of the equatorial plane, so the Bloch vector traces a cone that never reaches the south pole. A Rabi lineshape scan (fixed $t = \pi/\Omega$, sweep $\Delta$) has a full width of order $\Omega$: **power broadening in its coherent form — slower pulses give narrower lines.**

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| $P_e$ against pulse time on resonance | $\Omega$, from the oscillation period |
| $P_e$ against time and detuning (a chevron) | the resonance frequency from the symmetry axis; $\tilde\Omega$ from the fringe spacing |
| decay of the flopping contrast | decoherence; in ions also thermal motion, since $n$-dependent Rabi rates from the Debye–Waller factor smear $\tilde\Omega$ ([[Debye-Waller Factor]]) |
| linewidth of a fixed-duration scan | of order $\Omega$: coherent power broadening |
| a $\pi$ pulse that under-inverts and runs fast | detuning (see the question below) |

> [!question]- Your $\pi$ pulse inverts only 96% of the population, and the oscillation runs slightly faster than expected. First suspect?
> Detuning: $\Delta \neq 0$ raises the rate to $\sqrt{\Omega^2+\Delta^2}$ and caps transfer at $\Omega^2/(\Omega^2+\Delta^2)$ — both signatures at once. An amplitude miscalibration alone changes the rate but still reaches full contrast on resonance.

# Connections

- [[Two-Level Systems]] — the Hamiltonian whose dynamics this is
- [[Ramsey Interferometry]] — $\pi/2$ pulses as atom-interferometer beamsplitters
- [[Bloch Sphere]] — flopping as precession about the tilted drive axis
- [[Optical Bloch Equations]] — add spontaneous emission and the oscillations damp
- [[Sideband Transitions]] — Rabi flopping on motional sidebands, at rates scaled by $\eta\sqrt{n}$
- [[Pulse Shaping and Optimal Control]] — shaping pulses beyond square Rabi pulses
- [[Reading Matrices and Hamiltonians]] — the resonant and far-detuned regimes of one $2\times2$ matrix

---
Source: Foot, *Atomic Physics*, §7.1–7.3; D. A. Steck, *Quantum and Atom Optics*, Ch. 5 (Rabi flopping with arbitrary initial conditions)
