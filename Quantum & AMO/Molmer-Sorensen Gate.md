#quantum #AMO #ions

**Drive both sidebands at once, detuned symmetrically by $\pm\delta$: the ions feel a spin-dependent force that pushes their shared mode around a closed loop in phase space, and the geometric phase picked up — the enclosed area — depends on the joint spin state.** Close the loop and the motion factors out: pure spin–spin entanglement, insensitive to $\bar{n}$.

# Reference

Bichromatic field at $\omega_0 \pm (\omega + \delta)$ — a small symmetric detuning $\delta$ from red and blue sidebands. The combined drive is a force on the mode whose sign depends on the collective spin operator $S_\phi = \sigma_\phi^{(1)} + \sigma_\phi^{(2)}$ ($\phi$ set by laser phases): each $S_\phi$ eigenstate's motional wavepacket is displaced around a circle of radius $\propto \eta\Omega/\delta$, completing a loop every $2\pi/\delta$.

**Loop closure:** at

$$\tau = \frac{2\pi K}{\delta}, \quad K \in \mathbb{Z}$$

$\tau$ = gate duration (s); $\delta$ = symmetric detuning of the two tones from their sidebands (rad/s) — it is also the *angular rate at which the phase-space loop is traversed*, so $2\pi/\delta$ is one lap and $K$ = number of laps. At these times the displacement returns to zero and spin and motion disentangle exactly, whatever the motional state. The residue is the geometric phase = enclosed phase-space area, $\propto (\eta\Omega/\delta)^2$ per loop and proportional to $S_\phi^2$, giving an effective $\sigma_\phi^{(1)}\sigma_\phi^{(2)}$ interaction:

$$U = \exp\!\left(-i\chi\,\sigma_\phi^{(1)}\sigma_\phi^{(2)}\right), \qquad \chi = \frac{\pi}{4} \;\text{(maximally entangling) when}\; \delta = 2\eta\Omega\sqrt{K}$$

$\chi$ = accumulated two-spin phase (rad; the enclosed area in units of $\hbar$); $\eta$ = Lamb–Dicke parameter of the driven mode; $\Omega$ = single-tone carrier Rabi frequency (rad/s), so $\eta\Omega$ = sideband coupling rate and $\eta\Omega/\delta$ = loop radius in phase space (dimensionless, in units of the ground-state spread $x_0$). The condition fixes the loop radius at $1/2\sqrt{K}$: more laps, smaller circles, same total area.

Scalings to carry: gate time $\tau = 2\pi K/\delta = \pi\sqrt{K}/\eta\Omega$ — speed comes from $\eta\Omega$, so faster gates want tighter Lamb–Dicke coupling or more power, and going to $K > 1$ costs time as $\sqrt{K}$ while buying robustness to detuning error.

From $|gg\rangle$: the Bell state $(|gg\rangle - i|ee\rangle)/\sqrt{2}$. Gate time $\tau = 2\pi K/\delta$ — more loops ($K > 1$) buys robustness at the cost of speed.

**Why it's the trapped-ion workhorse:**
- **$\bar{n}$-insensitive:** displacements are rigid translations in phase space — the same for every Fock state — and the geometric phase is area, not overlap. Doppler-cooled thermal states work (Lamb–Dicke still required; $\eta\sqrt{n}$ corrections erode fidelity for hot ions).
- Loop closure also makes it first-order insensitive to the motional phase at gate start.
- Error anatomy: detuning miscalibration or timing error → unclosed loop → residual spin–motion entanglement (leaks fidelity into the "environment" you own); mode frequency drift and motional heating during the loop are the usual fidelity ceiling.

> [!question]- Why does the MS gate work on a thermal ion when a naive "sideband $\pi$-pulse" gate wouldn't?
> Sideband pulses have $n$-dependent Rabi rates ($\eta\sqrt{n}\,\Omega$) — a thermal mixture dephases them. The MS force displaces all Fock states identically, and the acquired phase is the enclosed *area*, an $n$-independent geometric quantity; once the loop closes, motion factors out regardless of the initial motional state.

# Connections

- [[Displacement Operator]] — the loop is composed displacements; BCH's composition phase *is* the enclosed area
- [[Sideband Transitions]] — the two off-resonant couplings whose interference builds the spin-dependent force
- [[Entangling Gates]] — MS is the native two-qubit gate that compiles to CNOT
- [[Sideband Spectrum of Modulated Light]] — generating and sanity-checking the bichromatic drive
- [[Normal Modes of Ion Chains]] — which shared mode carries the force, and the crowding problem at large N
- [[Reference Atlas/Math/Magnus Expansion]] — why the gate is exactly solvable: $H$ linear in phase-space operators terminates the series at $\Omega_2$, the geometric phase

---
Source: Leibfried, Blatt, Monroe & Wineland, *Rev. Mod. Phys.* 75, 281 (2003)
