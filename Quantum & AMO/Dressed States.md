#quantum #AMO

**Stop treating the drive as a perturbation: diagonalize atom+field together, and the true eigenstates are superpositions of the bare levels — "dressed" by the light.** Level repulsion of these eigenstates *is* the AC Stark shift; their splitting *is* Autler-Townes.

# Reference

Rotating frame, detuning $\Delta$, Rabi coupling $\Omega$:
$$
E_\pm = \pm\frac{\hbar}{2}\sqrt{\Omega^2 + \Delta^2}, \qquad
|+\rangle = \sin\theta\,|g\rangle + \cos\theta\,|e\rangle,\quad
\tan 2\theta = -\Omega/\Delta
$$

$E_\pm$ = dressed-state energies (J) — the eigenvalues of the 2×2 rotating-frame Hamiltonian, i.e. a hyperbola in $\Delta$ with minimum gap $\hbar\Omega$; $\Omega$ = Rabi coupling (rad/s), the off-diagonal element; $\Delta = \omega_L - \omega_0$ = detuning (rad/s), the diagonal splitting; $\theta$ = mixing angle (rad), whose tangent is the ratio of off-diagonal to diagonal — the universal 2×2 statement that mixing is strong when coupling beats detuning and weak when it does not. At $\Delta = 0$, $\theta = 45°$ (maximal mixing); at $|\Delta| \gg \Omega$, $\theta \to 0$ and the dressed states collapse onto the bare ones.

**At resonance** ($\Delta = 0$): dressed states are $(|g\rangle \pm |e\rangle)/\sqrt2$, split by exactly $\hbar\Omega$ — the minimum gap of the avoided crossing as the laser is scanned through resonance.

**Far detuned** ($|\Delta| \gg \Omega$): dressed states are nearly bare states, shifted by
$$
\delta E \approx \pm\frac{\hbar\Omega^2}{4\Delta}
$$
— the **AC Stark shift (light shift)** read off as second-order level repulsion. Sign follows detuning: red detuning pushes the ground state *down* (this is why red-detuned dipole traps attract), blue pushes it up.

**Autler-Townes:** probe a third level while dressing a transition — the line splits into a doublet separated by $\tilde\Omega$, the dressed splitting made directly visible. (Cousin: the Mollow triplet in resonance fluorescence.)

Dressed states are also what you adiabatically follow: chirping through resonance transports population $|g\rangle \to |e\rangle$ along one dressed branch — see [[Adiabatic Theorem]].

> [!question]- How does the AC Stark shift emerge from the dressed-state picture without any perturbation theory?
> Exact eigenvalues $\pm\frac{\hbar}{2}\sqrt{\Omega^2+\Delta^2}$ expanded for $|\Delta| \gg \Omega$ give $\pm\hbar(\Delta/2 + \Omega^2/4\Delta)$: the bare energy plus the light shift. Perturbation theory's $\Omega^2/4\Delta$ is just the Taylor expansion of the avoided-crossing hyperbola.

# Connections

- [[Stark Effect and Light Shifts]] — the far-detuned limit as its own subject; dipole traps
- [[Two-Level Systems]] — the avoided-crossing structure being diagonalized
- [[Adiabatic Theorem]] — dressed states are the rails for adiabatic passage
- [[Jaynes-Cummings Model]] — dressed states with the field quantized: the $\pm$ doublet ladder
- [[Rabi Oscillations]] — bare-basis beating between the dressed eigenstates

---
Source: Cohen-Tannoudji, Dupont-Roc & Grynberg, *Atom-Photon Interactions*, Ch. VI
