 #AMO

**Electric fields shift atomic levels at second order — $-\tfrac{1}{2}\alpha E^2$ — and a laser is just an oscillating field, so every beam light-shifts every level it doesn't resonantly drive.** Dipole traps *are* this effect; differential versions of it are a decoherence budget line.

# Reference

**DC Stark:** atoms have no permanent dipole (parity eigenstates), so the linear term vanishes and

$$\Delta E = -\tfrac{1}{2}\alpha E^2, \qquad \alpha = 2\sum_k \frac{|\langle k|d|0\rangle|^2}{E_k - E_0}$$

$\Delta E$ = level shift (J); $E$ = applied electric field (V/m); $\alpha$ = static polarizability (C·m²/V, i.e. J per (V/m)²; usually quoted in atomic units, 1 a.u. = 1.649×10⁻⁴¹ C·m²/V), defined by the dipole the field induces, $d_{\text{ind}} = \alpha E$.

The sum runs over every other level $k$: $\langle k|d|0\rangle$ = transition dipole matrix element (C·m), $E_k - E_0$ = energy denominator (J). Two proportionalities do all the work — $\alpha$ grows as the *square* of the dipole matrix element and as the *inverse* of the energy gap, so a single nearby strongly-coupled level usually dominates the sum, and highly excited states (large orbitals, tiny gaps) are enormously polarizable ($n^7$ for Rydbergs — [[Rydberg Atoms and Blockade]]). Levels repel; the ground state has all denominators positive and therefore always shifts *down*.

**AC / light shift** (two-level, RWA, detuning $\Delta = \omega_L - \omega_0$, far off resonance $|\Delta| \gg \Gamma, \Omega$):

$$\Delta E_g = \frac{\hbar\Omega^2}{4\Delta}, \qquad \Delta E_e = -\frac{\hbar\Omega^2}{4\Delta}$$

$\Omega$ = resonant Rabi frequency (rad/s), with $\Omega^2 \propto I$ the laser intensity; $\Delta = \omega_L - \omega_0$ = laser detuning (rad/s). The shifts are equal and opposite because the two levels repel each other, and $\Omega^2/4\Delta$ is again the second-order form (coupling² / gap) with everything in angular frequency.

Reading the two proportionalities against each other is the whole design logic: shift $\propto I/\Delta$ but photon scattering $\propto I/\Delta^2$, so at fixed trap depth the scattering falls as $1/\Delta$.

**Sign flips with detuning:** red ($\Delta < 0$) pushes the ground state down ⇒ atoms pulled toward high intensity (dipole traps, tweezers); blue pushes them out. Since $\Omega^2 \propto I$:

$$U \propto \frac{I}{\Delta} \quad \text{but} \quad R_{\mathrm{scatt}} \propto \frac{I}{\Delta^2}$$

— so detune far and crank the power: same trap depth, less scattering. Equivalent picture: dressed-state level repulsion.

**The gotcha layer:** *differential* light shifts. Raman beams, lattice/tweezer light, even the repumper shift qubit levels unequally; intensity noise then converts directly to qubit frequency noise (dephasing), and spatial intensity gradients give shift inhomogeneity across a chain. Standard countermeasures: magic-wavelength choices, intensity stabilization, echo.

> [!question]- Your dipole-trap laser doubles in intensity but you also double the detuning. What happens to trap depth and to scattering-induced decoherence?
> Depth $\propto I/\Delta$: unchanged. Scattering $\propto I/\Delta^2$: halved. Far-detuned + high power always wins on coherence for fixed depth — until you run out of laser.

# Connections

- [[Time-Independent Perturbation Theory]] — both shifts are its second-order formula; level repulsion sets the signs
- [[Dressed States]] — the same AC shift derived by diagonalizing atom+field exactly
- [[Dielectrics and Polarizability]] — $\alpha$ is the microscopic object behind $\varepsilon_r$; same quantity, bulk vs single atom

---
Source: Foot, *Atomic Physics*, §7.7 & §9.5
