#AMO

**Put an atom in a static electric field and its levels shift, at second order in the field — $-\tfrac{1}{2}\alpha E^2$ — because the field mixes each level with others of opposite parity and the mixed levels repel; a laser is an oscillating field, so every beam shifts every level it does not drive resonantly.** Dipole traps and optical tweezers are built on this effect. Differential shifts between qubit levels are a dephasing mechanism wherever light is present.

# Reference

**DC Stark shift.** An atom in a state of definite parity has no permanent dipole, so the linear term vanishes ([[Parity and Time Reversal]]) and

$$
\Delta E = -\tfrac{1}{2}\alpha E^2, \qquad \alpha = 2\sum_k \frac{|\langle k|d|0\rangle|^2}{E_k - E_0}
$$

- $\Delta E$ — level shift (J)
- $E$ — applied electric field (V/m)
- $\alpha$ — static polarizability (C·m²/V): defined by the induced dipole, $d_\text{ind} = \alpha E$
- $\langle k\vert d\vert 0\rangle$ — transition dipole matrix element to level $k$ (C·m)
- $E_k - E_0$ — energy denominator (J)

$\alpha$ is usually quoted in atomic units, 1 a.u. = 1.649×10⁻⁴¹ C·m²/V. Two proportionalities do most of the work: $\alpha$ grows as the *square* of the dipole matrix element and as the *inverse* of the energy gap. So a single nearby, strongly coupled level usually dominates the sum, and highly excited states — large orbitals, small gaps — are enormously polarizable ($n^7$ for Rydberg states, [[Rydberg Atoms and Blockade]]). Levels repel; the ground state has all denominators positive and always shifts *down*. Degenerate states of opposite parity, as in hydrogen's $n = 2$ level, shift linearly instead ([[Degeneracy and Level Crossings]]).

**Picture:** an off-resonant field is a coupling the atom cannot follow — each level borrows a little of the other level's character and is pushed away from it.

**AC Stark shift (light shift)**, two levels, rotating-wave approximation, far off resonance ($|\Delta| \gg \Gamma, \Omega$):

$$
\Delta E_g = \frac{\hbar\Omega^2}{4\Delta}, \qquad \Delta E_e = -\frac{\hbar\Omega^2}{4\Delta}
$$

- $\Omega$ — resonant Rabi frequency (rad/s), with $\Omega^2 \propto I$, the laser intensity
- $\Delta = \omega_L - \omega_0$ — laser detuning (rad/s)

The shifts are equal and opposite because the two levels repel each other, and $\Omega^2/4\Delta$ is the second-order form (coupling² / gap) with everything in angular frequency ([[Effective Hamiltonians and Adiabatic Elimination]]). The Rabi frequency and the light shift share units because they are entries of the same Hamiltonian: one off-diagonal, the other a change of a diagonal entry ([[Reading Matrices and Hamiltonians]]).

**Trap depth against scattering.** Since $\Omega^2 \propto I$:

$$
U \propto \frac{I}{\Delta} \quad \text{but} \quad R_{\mathrm{scatt}} \propto \frac{I}{\Delta^2}
$$

- $U$ — light-shift potential (J): the trap depth
- $R_\text{scatt}$ — photon scattering rate (1/s): heating and decoherence

So at fixed trap depth the scattering falls as $1/\Delta$: detune far and raise the power, until the available laser power runs out.

**Sign flips with detuning:** red detuning ($\Delta < 0$) pushes the ground state down, so atoms are pulled toward high intensity (dipole traps, tweezers); blue detuning pushes them out. The equivalent picture is dressed-state level repulsion ([[Dressed States]]).

**Vector and tensor light shifts.** For atoms with angular momentum, circularly polarized light shifts different $m$ sublevels by different amounts, as if it were a magnetic field along the beam (the vector shift, odd under time reversal); linearly polarized light can shift $|m|$ sublevels differently (the tensor shift). Both depend on polarization purity and beam alignment ([[Zeeman Effect (Atlas)]]).

**Differential light shifts, the part that causes dephasing in practice.** Raman beams, lattice or tweezer light, and even the repumper shift qubit levels unequally. Intensity noise then converts directly to qubit frequency noise, and spatial intensity gradients give shift inhomogeneity across a chain. The standard countermeasures are magic-wavelength choices, intensity stabilization, and echo sequences ([[Intensity Stabilization]], [[Spin Echo and Dynamical Decoupling]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Ramsey frequency shift against beam intensity | the differential light shift; linear in $I$ if far detuned |
| trap frequency from parametric or motional spectroscopy | the trap depth and curvature from the light-shift potential |
| shift that changes sign as the laser crosses a transition | which transition dominates the polarizability |
| shift that depends on circular polarization | a vector light shift: impure polarization or a misaligned beam |
| Autler–Townes splitting of a probe line | the exact dressed splitting, beyond the perturbative regime |

> [!question]- Your dipole-trap laser doubles in intensity but you also double the detuning. What happens to trap depth and to scattering-induced decoherence?
> Depth $\propto I/\Delta$ is unchanged. Scattering $\propto I/\Delta^2$ is halved. At fixed depth, a larger detuning with more power always reduces scattering — until the laser runs out of power.

# Connections

- [[Time-Independent Perturbation Theory]] — both shifts are its second-order formula; level repulsion sets the signs
- [[Dressed States]] — the same AC shift derived by diagonalizing atom and field exactly
- [[Dielectrics and Polarizability]] — $\alpha$ is the microscopic object behind $\varepsilon_r$
- [[Intensity Stabilization]] — reducing the intensity noise that light shifts turn into frequency noise
- [[Effective Hamiltonians and Adiabatic Elimination]] — light shifts as second-order terms of an eliminated level
- [[Parity and Time Reversal]] — why the DC shift starts at second order
- [[Reading Matrices and Hamiltonians]] — the far-detuned regime of a $2\times2$ Hamiltonian

---
Source: Foot, *Atomic Physics*, §7.7 & §9.5; R. Grimm, M. Weidemüller & Y. B. Ovchinnikov, "Optical dipole traps for neutral atoms," *Adv. At. Mol. Opt. Phys.* 42, 95 (2000)
