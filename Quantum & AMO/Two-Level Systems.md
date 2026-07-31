#quantum

**The universal approximation of quantum physics: whenever a drive is near-resonant with one transition and everything else is far detuned, the system is effectively two levels — and every two-level Hamiltonian is the same problem.** Spin-1/2, qubit, atom+laser: one algebra.

# Reference

Most general (traceless part) two-level Hamiltonian:
$$
H = \frac{\hbar}{2}\begin{pmatrix} \Delta & \Omega \\ \Omega^* & -\Delta \end{pmatrix} = \frac{\hbar}{2}\left(\Delta\,\sigma_z + \Omega_x\sigma_x + \Omega_y\sigma_y\right)
$$
$\hbar\Delta$ = diagonal energy splitting (J) — the bare level separation, or the detuning once in a rotating frame; $\Omega$ = off-diagonal coupling (rad/s), complex, with its phase setting the rotation axis in the $xy$ plane. Both appear as $\hbar/2$ × a Pauli, so the natural comparison is $\Omega$ against $\Delta$: their *ratio* fixes the eigenstates (mixing), their *quadrature sum* fixes the eigenvalues (rate).

**Eigenvalues:** $E_\pm = \pm\frac{\hbar}{2}\sqrt{\Delta^2 + |\Omega|^2}$ — the gap is never smaller than $\hbar|\Omega|$. Sweep $\Delta$ through zero and the levels **avoid crossing** with minimum gap $\hbar|\Omega|$ at resonance: coupling repels levels. Eigenstates rotate from bare states (at $|\Delta| \gg \Omega$) to equal superpositions (at $\Delta = 0$), with mixing angle $\tan 2\theta = |\Omega|/\Delta$.

Everything is a rotation on the [[Bloch Sphere]]: $H = \frac{\hbar}{2}\vec\Omega\cdot\vec\sigma$ generates precession about $\vec\Omega = (\Omega_x, \Omega_y, \Delta)$ at rate $|\vec\Omega|$ — this single sentence contains Rabi flopping, Ramsey precession, and adiabatic following.

**Validity check** before trusting the truncation: neighboring levels detuned by $\delta$ contribute at $O(\Omega/\delta)$ — off-resonant scattering and light shifts from the spectator levels are the leading corrections (in ions: the other Zeeman/hyperfine states).

> [!question]- Why can't the two eigenvalues cross while the coupling $\Omega \neq 0$?
> The gap is $\hbar\sqrt{\Delta^2 + |\Omega|^2} \geq \hbar|\Omega|$: a sum of squares can't vanish unless both terms do. Degeneracy needs $\Delta = 0$ *and* $\Omega = 0$ simultaneously — two conditions, one knob, so generic sweeps produce avoided crossings.

# Connections

- [[Rabi Oscillations]] — the dynamics of this Hamiltonian under resonant drive
- [[Landau-Zener Transitions]] — sweeping $\Delta$ through the avoided crossing
- [[Reference Atlas/Linear Algebra/Pauli Matrices]] — the natural basis for any 2×2 Hermitian $H$
- [[Dressed States]] — the $E_\pm$ eigenstates named and used
- [[Qubits]] — the same object, quantum-information flavored

---
Source: Cohen-Tannoudji, Diu & Laloë, *Quantum Mechanics*, Ch. IV
