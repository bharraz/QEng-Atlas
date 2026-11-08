#quantum

**Whenever a drive is near resonance with one transition and every other transition is far off resonance, a quantum system behaves as if it had only two levels, and every two-level Hamiltonian is the same $2\times2$ problem.** A spin-$\tfrac12$ in a magnetic field, a qubit, an atom driven by a laser, and a particle in a double well differ only in what the two numbers on the diagonal and off the diagonal mean.

# Reference

The most general two-level Hamiltonian, apart from an overall energy offset:

$$
H = \frac{\hbar}{2}\begin{pmatrix} \Delta & \Omega \\ \Omega^* & -\Delta \end{pmatrix} = \frac{\hbar}{2}\left(\Delta\,\sigma_z + \Omega_x\sigma_x + \Omega_y\sigma_y\right)
$$

- $\hbar\Delta$ — diagonal energy splitting (J): bare splitting, or detuning in a rotating frame
- $\Omega$ — off-diagonal coupling (rad/s), complex: its phase sets the rotation axis in the $xy$ plane
- $\Omega_x, \Omega_y$ — real and imaginary parts of $\Omega$, with $\Omega = \Omega_x - i\Omega_y$

Both appear as $\hbar/2$ times a Pauli matrix, so the natural comparison is $\Omega$ against $\Delta$: their *ratio* fixes the eigenstates (the mixing), and their *quadrature sum* fixes the eigenvalues (the rate) ([[Reading Matrices and Hamiltonians]]).

**Picture:** every two-level Hamiltonian is a magnetic field acting on a spin-$\tfrac12$ — $\Delta$ is the field's $z$ component, $\Omega$ its transverse part, and the state precesses about the total field.

**Eigenvalues and mixing:**

$$
E_\pm = \pm\frac{\hbar}{2}\sqrt{\Delta^2 + \lvert\Omega\rvert^2}, \qquad \tan 2\theta = \frac{\lvert\Omega\rvert}{\Delta}
$$

- $E_\pm$ — the two eigenenergies (J)
- $\theta$ — mixing angle (rad): 0 for bare states, 45° for equal superpositions

The gap is never smaller than $\hbar\lvert\Omega\rvert$. Sweep $\Delta$ through zero and the levels **avoid crossing** with minimum gap $\hbar\lvert\Omega\rvert$ at resonance: coupling repels levels. The eigenstates rotate from the bare states (at $\lvert\Delta\rvert \gg \lvert\Omega\rvert$) to equal superpositions (at $\Delta = 0$) ([[Degeneracy and Level Crossings]]).

**Everything is a rotation on the [[Bloch Sphere]].** $H = \frac{\hbar}{2}\vec\Omega\cdot\vec\sigma$ generates precession about $\vec\Omega = (\Omega_x, \Omega_y, \Delta)$ at rate $\lvert\vec\Omega\rvert$. That one statement contains Rabi flopping, Ramsey precession, and adiabatic following.

**What the two numbers mean in different systems:**

| System | Diagonal ($\Delta$) | Off-diagonal ($\Omega$) |
|---|---|---|
| atom or ion driven by a laser, rotating frame | detuning of laser from transition | Rabi frequency: dipole matrix element × field amplitude |
| spin in a static field plus a transverse oscillating field | Larmor frequency minus drive frequency | transverse field strength × gyromagnetic ratio |
| superconducting or spin qubit | qubit frequency minus drive frequency | drive amplitude |
| particle in a double well | energy offset between the wells | tunnelling amplitude |
| two coupled modes (optical, mechanical, microwave) | frequency difference | coupling rate |

**Validity check before trusting the truncation:** neighbouring levels detuned by $\delta$ contribute at order $\Omega/\delta$. Off-resonant scattering and light shifts from those spectator levels are the leading corrections — in ions, the other Zeeman and hyperfine states; in transmons, the third level ([[Leakage, Erasure, and Biased Noise]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Rabi oscillations against drive time and detuning (a chevron) | $\Omega$ from the rate on resonance, the resonance from the symmetry axis |
| Ramsey fringes | $\Delta$, as the precession frequency in the drive's frame |
| a spectrum scanned through an avoided crossing | the coupling: the minimum splitting is $\hbar\lvert\Omega\rvert$ |
| population appearing outside the two levels | the truncation is failing: spectator levels are being driven |

> [!question]- Why can't the two eigenvalues cross while the coupling $\Omega \neq 0$?
> The gap is $\hbar\sqrt{\Delta^2 + |\Omega|^2} \geq \hbar|\Omega|$: a sum of squares cannot vanish unless both terms do. Degeneracy needs $\Delta = 0$ *and* $\Omega = 0$ simultaneously — two conditions, one knob — so generic sweeps produce avoided crossings.

# Connections

- [[Rabi Oscillations]] — the dynamics of this Hamiltonian under resonant drive
- [[Landau-Zener Transitions]] — sweeping $\Delta$ through the avoided crossing
- [[Pauli Matrices (Atlas)]] — the natural basis for any $2\times2$ Hermitian $H$
- [[Dressed States]] — the $E_\pm$ eigenstates named and used
- [[Qubits]] — the same object, in quantum-information terms
- [[Reading Matrices and Hamiltonians]] — the diagonal-against-off-diagonal comparison in general
- [[Effective Hamiltonians and Adiabatic Elimination]] — two-level systems that arise from three or more levels

---
Source: Cohen-Tannoudji, Diu & Laloë, *Quantum Mechanics*, Ch. IV
