#quantum #AMO

**Move into a frame co-rotating with the drive and the fast oscillation disappears, leaving a static Hamiltonian containing only what's slow: detunings and couplings.** The frame change itself adds a fictitious energy term — that's where detuning comes from.

# Reference

For any unitary frame change $|\psi'\rangle = U(t)|\psi\rangle$:
$$
H' = U H U^\dagger + i\hbar\, \dot{U} U^\dagger
$$
The second term is the **fictitious contribution** — the quantum version of centrifugal/Coriolis terms in a rotating mechanical frame. It's why the transformed Hamiltonian is *not* just $H$ conjugated.

**Spin/qubit at drive frequency $\omega$:** $U = e^{+i\omega t\,\sigma_z/2}$ on $H = \frac{\hbar\omega_0}{2}\sigma_z + \hbar\Omega\cos(\omega t)\,\sigma_x$ gives (after [[Rotating Wave Approximation]])
$$
H' = -\frac{\hbar\Delta}{2}\sigma_z + \frac{\hbar\Omega}{2}\sigma_x, \qquad \Delta = \omega - \omega_0
$$
The fictitious term $-\frac{\hbar\omega}{2}\sigma_z$ ate the big splitting $\omega_0$, leaving only $\Delta$. In NMR language: on resonance, the effective field vanishes and only the drive field remains.

**Oscillator at $\omega$:** $U = e^{+i\omega t\, a^\dagger a}$ sends $a \to a\,e^{-i\omega t}$ and $\hbar\omega_m a^\dagger a \to \hbar(\omega_m - \omega)a^\dagger a$ — the standard first move for sideband and parametric problems.

Bookkeeping gotchas: the frame is a choice, so **quote which frame a phase or frequency lives in** (drive frame vs atom frame — the source of many factor-of-$\Delta$ sign fights); and if $U$ is built from $H_0$ itself, this is exactly the [[Interaction Picture]].

> [!question]- Where does the $i\hbar\,\dot U U^\dagger$ term come from, and what does it do in the spin case?
> Demand that $|\psi'\rangle = U|\psi\rangle$ satisfy a Schrödinger equation: differentiating gives $i\hbar\partial_t|\psi'\rangle = (UHU^\dagger + i\hbar\dot U U^\dagger)|\psi'\rangle$. For $U = e^{i\omega t\sigma_z/2}$ it contributes $-\frac{\hbar\omega}{2}\sigma_z$, which cancels the bare splitting down to the detuning $\Delta$.

# Connections

- [[Interaction Picture]] — the special case $U = e^{iH_0t/\hbar}$
- [[Rotating Wave Approximation]] — the cleanup step done in this frame
- [[Unitary Matrices]] — the transformation machinery
- [[Rabi Oscillations]] — solved trivially once the frame makes $H$ static
- [[Molmer-Sorensen Gate]] — lives entirely in a doubly-rotating frame (spin ⊗ motion)

---
Source: Cohen-Tannoudji, Diu & Laloë, *Quantum Mechanics*, Complement F_IV
