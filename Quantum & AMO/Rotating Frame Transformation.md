#quantum #AMO

**A qubit driven at frequency $\omega$ has a Hamiltonian that oscillates in time; describe it from a frame rotating with the drive and the fast oscillation disappears, leaving a static Hamiltonian that contains only the slow quantities: the detuning and the coupling.** The frame change itself adds an extra energy term, and that term is where the detuning comes from.

# Reference

For any time-dependent change of frame $|\psi'\rangle = U(t)|\psi\rangle$:

$$
H' = U H U^\dagger + i\hbar\, \dot{U} U^\dagger
$$

- $U(t)$ — the frame's unitary: a rotation at the chosen frequency
- $H'$ — the Hamiltonian that generates evolution in the new frame
- $i\hbar\dot U U^\dagger$ — the **fictitious contribution**, present only when $U$ depends on time

It is the quantum counterpart of the centrifugal and Coriolis terms of a rotating mechanical frame, and the reason the transformed Hamiltonian is *not* only $H$ conjugated.

**Picture:** a strobe light flashing at the drive frequency — a wheel spinning at nearly that rate appears to turn slowly at the difference, and the slow apparent motion is all the rotating frame keeps.

**Spin or qubit at drive frequency $\omega$:** $U = e^{+i\omega t\,\sigma_z/2}$ applied to $H = \frac{\hbar\omega_0}{2}\sigma_z + \hbar\Omega\cos(\omega t)\,\sigma_x$ gives, after the [[Rotating Wave Approximation (Atlas)]],

$$
H' = -\frac{\hbar\Delta}{2}\sigma_z + \frac{\hbar\Omega}{2}\sigma_x, \qquad \Delta = \omega - \omega_0
$$

- $\omega_0$ — bare transition frequency (rad/s)
- $\omega$ — drive frequency (rad/s)
- $\Omega$ — Rabi frequency (rad/s)
- $\Delta$ — detuning (rad/s): all that remains of the large splitting

The fictitious term $-\frac{\hbar\omega}{2}\sigma_z$ cancels the large splitting $\omega_0$ down to $\Delta$. In NMR language: on resonance the effective static field vanishes, and only the drive field remains.

**Oscillator at $\omega$:** $U = e^{+i\omega t\, a^\dagger a}$ sends $a \to a\,e^{-i\omega t}$ and $\hbar\omega_m a^\dagger a \to \hbar(\omega_m - \omega)a^\dagger a$ — the standard first step for sideband and parametric problems ([[Sideband Transitions]]).

**Common frame choices:**

| Frame | Rotates at | What stays static |
|---|---|---|
| drive (laser or local-oscillator) frame | the drive frequency | detuning and coupling; the phases a Ramsey experiment measures |
| atom frame (interaction picture) | the bare transition frequency | the drive appears as a slowly rotating coupling ([[Interaction Picture]]) |
| doubly rotating frame | spin at one frequency, motion at another | spin–motion couplings near a sideband ([[Molmer-Sorensen Gate]]) |
| frame of a strong drive (dressed frame) | the Rabi frequency, about the drive axis | weak probes or noise near the Rabi frequency ([[Dressed States]]) |

**Bookkeeping:** the frame is a choice, so **quote which frame a phase or frequency lives in**. Drive frame against atom frame is the source of many sign disagreements about $\Delta$ ([[Conventions and Factor-of-Two Traps]]). If $U$ is built from $H_0$ itself, the transformation is exactly the [[Interaction Picture]].

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Ramsey fringe phase | the qubit's phase relative to the local oscillator: a drive-frame quantity |
| a frequency shift that tracks the local oscillator's frequency | an error in the frame (detuning), not in the qubit |
| a phase that depends on when a pulse starts relative to the oscillator | a frame or timing convention not kept consistent between pulses |

> [!question]- Where does the $i\hbar\,\dot U U^\dagger$ term come from, and what does it do in the spin case?
> Demand that $|\psi'\rangle = U|\psi\rangle$ obey a Schrödinger equation. Differentiating gives $i\hbar\partial_t|\psi'\rangle = (UHU^\dagger + i\hbar\dot U U^\dagger)|\psi'\rangle$. For $U = e^{i\omega t\sigma_z/2}$ the extra term is $-\frac{\hbar\omega}{2}\sigma_z$, which cancels the bare splitting down to the detuning $\Delta$.

# Connections

- [[Interaction Picture]] — the special case $U = e^{iH_0t/\hbar}$
- [[Rotating Wave Approximation (Atlas)]] — the cleanup step done in this frame
- [[Unitary Matrices]] — the transformation machinery
- [[Rabi Oscillations]] — solved directly once the frame makes $H$ static
- [[Molmer-Sorensen Gate]] — works in a doubly rotating frame (spin ⊗ motion)
- [[Basis Change]] — the time-independent case, with no fictitious term
- [[Reading Matrices and Hamiltonians]] — frames as moving entries between diagonal and off-diagonal

---
Source: Cohen-Tannoudji, Diu & Laloë, *Quantum Mechanics*, Complement F_IV
