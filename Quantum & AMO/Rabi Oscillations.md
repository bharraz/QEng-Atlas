 #AMO

**Drive a two-level system near resonance and the population sloshes coherently between the levels at the Rabi frequency — the Bloch vector precessing about the drive axis.** This is the primitive every gate and every pulse calibration is built from.

# Reference

Rotating frame, drive $\Omega$ (set by field amplitude × dipole matrix element, $\hbar\Omega = -\langle e|\vec d\cdot\vec E_0|g\rangle$), detuning $\Delta = \omega_L - \omega_0$. Starting in $|g\rangle$:

$$
P_e(t) = \frac{\Omega^2}{\Omega^2 + \Delta^2}\,\sin^2\!\left(\frac{\tilde\Omega\, t}{2}\right), \qquad \tilde\Omega = \sqrt{\Omega^2 + \Delta^2}
$$

$P_e$ = excited-state population (dimensionless probability); $\Omega$ = resonant Rabi frequency (rad/s), $\propto d\sqrt{I}$ — dipole matrix element × field amplitude; $\Delta$ = detuning (rad/s); $\tilde\Omega$ = generalized Rabi frequency (rad/s), the length of the drive vector $(\Omega, 0, \Delta)$ on the Bloch sphere. The prefactor $\Omega^2/\tilde\Omega^2$ is the squared sine of that vector's tilt from the $z$-axis: contrast is set by the *ratio* $\Omega/\Delta$, rate by the *magnitude*. A π-time therefore scales as $1/\Omega \propto 1/\sqrt{I}$ — quadrupling laser power halves the pulse time.

**On resonance** ($\Delta = 0$): full-contrast flopping $P_e = \sin^2(\Omega t/2)$.
- **$\pi$ pulse** ($\Omega t = \pi$): complete inversion $|g\rangle \to |e\rangle$.
- **$\pi/2$ pulse**: equal superposition — the beamsplitter of [[Ramsey Interferometry]].

**Detuned:** oscillation *speeds up* ($\tilde\Omega > \Omega$) but contrast drops to $\Omega^2/(\Omega^2+\Delta^2)$ — geometrically, the precession axis $(\Omega, 0, \Delta)$ tilts out of the equatorial plane, so the Bloch vector traces a cone that never reaches the south pole. A Rabi lineshape scan (fixed $t = \pi/\Omega$, sweep $\Delta$) has FWHM $\sim \Omega$: **power broadening in its coherent form — slower pulses give narrower lines.**

Calibration reality: contrast decay of the flopping envelope reveals decoherence and, in ions, thermal motion ($n$-dependent Rabi rates from the Debye-Waller factor smear $\tilde\Omega$).

> [!question]- Your $\pi$ pulse inverts only 96% of the population, and the oscillation runs slightly faster than expected. First suspect?
> Detuning: $\Delta \neq 0$ raises the rate to $\sqrt{\Omega^2+\Delta^2}$ and caps transfer at $\Omega^2/(\Omega^2+\Delta^2)$ — both signatures at once. Amplitude miscalibration alone changes the rate but still reaches full contrast on resonance.

# Connections

- [[Two-Level Systems]] — the Hamiltonian whose dynamics this is
- [[Ramsey Interferometry]] — $\pi/2$ pulses as atom-interferometer beamsplitters
- [[Bloch Sphere]] — flopping = precession about the tilted drive axis
- [[Optical Bloch Equations]] — add spontaneous emission and the oscillations damp
- [[Sideband Transitions]] — Rabi flopping on motional sidebands, rates scaled by $\eta\sqrt{n}$

---
Source: Foot, *Atomic Physics*, §7.1–7.3
