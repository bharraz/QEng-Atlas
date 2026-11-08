#quantum #AMO #ions

**A trapped ion oscillates in its trap at frequency $\omega$, so a laser beam reaches it with a phase that swings back and forth at $\omega$: the ion sees phase-modulated light, with sidebands at the laser frequency $\pm\,\omega$.** Tuning the laser to the carrier or to a sideband selects which spin–motion process is resonant: the carrier flips the spin, the red sideband trades a phonon (one quantum of motion) for a spin flip, and the blue sideband creates both. The motional spectrum becomes something you drive, read, and engineer.

# Reference

**Where the sidebands come from.** The laser field at the ion is $E_0\cos(kx - \omega_L t)$. If the ion moves as $x(t) = x_m\cos\omega t$, the phase $kx(t)$ oscillates at $\omega$ — the same phase modulation an [[Electro-Optic Modulator]] applies on purpose — so the ion sees

$$
e^{ikx_m\cos\omega t} = \sum_n i^n J_n(kx_m)\, e^{in\omega t}
$$

lines at $\omega_L + n\omega$ with Bessel-function weights. Quantum mechanically $x = x_0(a + a^\dagger)$, and the phase factor becomes $e^{i\eta(a + a^\dagger)}$ with $\eta = kx_0$ the [[Lamb-Dicke Regime|Lamb–Dicke parameter]]. In the Lamb–Dicke regime, $\eta^2(2\bar n + 1) \ll 1$, it expands as $1 + i\eta(a + a^\dagger)$: the $1$ is the carrier, and the $a$ and $a^\dagger$ terms are the first red and blue sidebands.

- $\omega$ — trap frequency of the motional mode (rad/s), set by the [[Paul Traps|trap]]
- $\omega_L$ — laser frequency (rad/s): detuning is $\omega_L-\omega_0$, with $\omega_0$ the ion's transition
- $k$ — laser wavevector projected on the direction of motion (m⁻¹)
- $x_0 = \sqrt{\hbar/2m\omega}$ — ground-state spread of the motion (m)
- $a, a^\dagger$ — lower and raise the motional quantum number $n$ (the phonon number)

In the Lamb–Dicke regime, the resonant interaction at each detuning:

| detuning | coupling | Hamiltonian | Rabi rate |
|---|---|---|---|
| $0$ (carrier) | $\vert g,n\rangle \leftrightarrow \vert e,n\rangle$ | $\tfrac{\hbar\Omega}{2}(\sigma_+ + \sigma_-)$ | $\Omega$ |
| $-\omega$ (RSB) | $\vert g,n\rangle \leftrightarrow \vert e,n{-}1\rangle$ | $\tfrac{\hbar\eta\Omega}{2}(\sigma_+ a + \sigma_- a^\dagger)$ | $\eta\sqrt{n}\,\Omega$ |
| $+\omega$ (BSB) | $\vert g,n\rangle \leftrightarrow \vert e,n{+}1\rangle$ | $\tfrac{\hbar\eta\Omega}{2}(\sigma_+ a^\dagger + \sigma_- a)$ | $\eta\sqrt{n{+}1}\,\Omega$ |

**Picture:** the ion's motion as a phase wobble on the light it sees: as in an FM radio signal, the wobble puts sidebands on the carrier, one motional quantum above and below.

RSB and BSB are the red and blue sidebands; $\Omega$ is the carrier Rabi frequency. The RSB is the **Jaynes–Cummings (JC) Hamiltonian** with the cavity mode replaced by a phonon mode; the BSB is anti-JC. Everything cavity QED does with photons, an ion does with its own motion — and with both signs of coupling available on demand.

**Spectroscopy of motion:** scan the laser — sidebands appear at every normal-mode frequency; positions calibrate the trap, and micromotion shows up as extra sidebands at $\Omega_{\mathrm{rf}}$ (the trap's RF drive frequency). **Thermometry:** thermal-state asymmetry $P_{\mathrm{RSB}}/P_{\mathrm{BSB}} = \bar{n}/(\bar{n}+1)$.

**The $\sqrt{n}$ dependence cuts both ways:** it's how you climb the Fock ladder deterministically ($\pi$-pulse durations scale as $1/\sqrt{n}$, and mismatch reveals which $|n\rangle$ you're in — Fock-state synthesis, motional-state tomography from Rabi-flop Fourier components), and it's why sideband flopping on a thermal state dephases (each $n$ flops at its own rate).

> [!question]- Why does blue-sideband Rabi flopping on a Doppler-cooled ion look like a fast decay rather than oscillation?
> The rate $\eta\sqrt{n{+}1}\,\Omega$ differs per Fock state; a thermal distribution ($\bar{n} \sim 10$) superposes many incommensurate frequencies which dephase in a few cycles. The Fourier transform of that flopping curve *is* the population distribution $P(n)$ — the bug is a diagnostic.

# Connections

- [[Lamb-Dicke Regime]] — where these couplings and their $\eta$-scalings come from
- [[Jaynes-Cummings Model (Atlas)]] — RSB realizes it exactly, phonon-for-photon
- [[Resolved Sideband Cooling]] — RSB cycling as a cooling engine
- [[Molmer-Sorensen Gate]] — both sidebands at once, off-resonantly: the entangling force
- [[Electro-Optic Modulator]] — the same phase-modulation sidebands, made deliberately on the light
- [[Paul Traps]] — the trap that sets $\omega$, and the source of micromotion sidebands
- [[Controlling Bosonic Modes]] — sideband control of motional states

---
Source: Leibfried, Blatt, Monroe & Wineland, *Rev. Mod. Phys.* 75, 281 (2003)
