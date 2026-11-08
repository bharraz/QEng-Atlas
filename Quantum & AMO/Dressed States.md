#quantum #AMO

**Drive a two-level atom strongly and its stationary states are no longer the bare ground and excited states: diagonalize atom and field together, and the eigenstates are superpositions of the bare levels — "dressed" by the light.** The repulsion between these eigenstates is the AC Stark shift, and their splitting, seen by a third probe level, is the Autler–Townes doublet.

# Reference

Rotating frame, detuning $\Delta$, Rabi coupling $\Omega$:

$$
E_\pm = \pm\frac{\hbar}{2}\sqrt{\Omega^2 + \Delta^2}, \qquad
|+\rangle = \sin\theta\,|g\rangle + \cos\theta\,|e\rangle,\quad
\tan 2\theta = -\Omega/\Delta
$$

- $E_\pm$ — dressed-state energies (J): the eigenvalues of the $2\times2$ rotating-frame Hamiltonian
- $\Omega$ — Rabi coupling (rad/s), the off-diagonal element
- $\Delta = \omega_L - \omega_0$ — detuning (rad/s), the diagonal splitting
- $\theta$ — mixing angle (rad)

As a function of $\Delta$ the energies trace a hyperbola with minimum gap $\hbar\Omega$. The tangent of $2\theta$ is the ratio of off-diagonal to diagonal: mixing is strong when the coupling exceeds the detuning and weak when it does not ([[Reading Matrices and Hamiltonians]]). At $\Delta = 0$, $\theta = 45°$ (maximal mixing); at $|\Delta| \gg \Omega$, $\theta \to 0$ and the dressed states approach the bare ones.

**Picture:** two pendulums joined by a spring — the motions that keep a fixed frequency are the shared in-phase and out-of-phase swings, not either pendulum alone, and the spring pushes their frequencies apart.

**At resonance** ($\Delta = 0$): the dressed states are $(|g\rangle \pm |e\rangle)/\sqrt2$, split by exactly $\hbar\Omega$ — the minimum gap of the avoided crossing as the laser is scanned through resonance.

**Far detuned** ($|\Delta| \gg \Omega$): the dressed states are nearly bare states, shifted by

$$
\delta E \approx \pm\frac{\hbar\Omega^2}{4\Delta}
$$

the **AC Stark shift (light shift)**, read off as second-order level repulsion. The sign follows the detuning: red detuning pushes the ground state *down*, which is why red-detuned dipole traps attract; blue pushes it up ([[Stark Effect and Light Shifts]]).

**Autler–Townes splitting:** probe a third level while dressing a transition, and the probe line splits into a doublet separated by $\tilde\Omega = \sqrt{\Omega^2+\Delta^2}$ — the dressed splitting made directly visible. The Mollow triplet in resonance fluorescence is the related emission signature.

**Adiabatic passage.** Dressed states are what a system follows when parameters change slowly: chirping the drive through resonance transports population $|g\rangle \to |e\rangle$ along one dressed branch ([[Adiabatic Theorem]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Autler–Townes doublet splitting against drive power | $\tilde\Omega$: the dressed splitting, and through it $\Omega$ |
| Mollow triplet sideband spacing in fluorescence | the Rabi frequency of a strongly driven transition |
| shift of a probe line with a far-detuned dressing beam | the light shift $\Omega^2/4\Delta$ |
| population transfer efficiency of a frequency chirp | whether the passage stayed adiabatic on one branch |

> [!question]- How does the AC Stark shift emerge from the dressed-state picture without any perturbation theory?
> The exact eigenvalues $\pm\frac{\hbar}{2}\sqrt{\Omega^2+\Delta^2}$, expanded for $|\Delta| \gg \Omega$, give $\pm\hbar(\Delta/2 + \Omega^2/4\Delta)$: the bare energy plus the light shift. Perturbation theory's $\Omega^2/4\Delta$ is the Taylor expansion of the avoided-crossing hyperbola.

# Connections

- [[Stark Effect and Light Shifts]] — the far-detuned limit as its own subject; dipole traps
- [[Two-Level Systems]] — the avoided-crossing structure being diagonalized
- [[Adiabatic Theorem]] — dressed states as the rails for adiabatic passage
- [[Jaynes-Cummings Model (Atlas)]] — dressed states with the field quantized: the $\pm$ doublet ladder
- [[Rabi Oscillations]] — bare-basis beating between the dressed eigenstates
- [[Reading Matrices and Hamiltonians]] — the mixing angle as off-diagonal over diagonal
- [[Diagonalization]] — dressing as a change to the eigenbasis

---
Source: Cohen-Tannoudji, Dupont-Roc & Grynberg, *Atom-Photon Interactions*, Ch. VI
