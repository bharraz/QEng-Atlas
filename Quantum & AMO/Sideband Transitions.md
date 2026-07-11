#quantum #AMO #ions

**Detune the laser by $0$ or $\mp\omega$ and you select which spin–motion process is resonant: carrier flips the spin, red sideband trades a phonon for a spin flip, blue sideband creates both.** The motional spectrum becomes something you drive, read, and engineer.

# Reference

In the Lamb–Dicke regime, the resonant interaction at each detuning:

| detuning | coupling | Hamiltonian | Rabi rate |
|---|---|---|---|
| $0$ (carrier) | $\vert g,n\rangle \leftrightarrow \vert e,n\rangle$ | $\tfrac{\hbar\Omega}{2}(\sigma_+ + \sigma_-)$ | $\Omega$ |
| $-\omega$ (RSB) | $\vert g,n\rangle \leftrightarrow \vert e,n{-}1\rangle$ | $\tfrac{\hbar\eta\Omega}{2}(\sigma_+ a + \sigma_- a^\dagger)$ | $\eta\sqrt{n}\,\Omega$ |
| $+\omega$ (BSB) | $\vert g,n\rangle \leftrightarrow \vert e,n{+}1\rangle$ | $\tfrac{\hbar\eta\Omega}{2}(\sigma_+ a^\dagger + \sigma_- a)$ | $\eta\sqrt{n{+}1}\,\Omega$ |

The RSB is literally the **Jaynes–Cummings Hamiltonian** with the cavity mode replaced by a phonon mode; the BSB is anti-JC. Everything cavity QED does with photons, an ion does with its own motion — and with both signs of coupling available on demand.

**Spectroscopy of motion:** scan the laser — sidebands appear at every normal-mode frequency; positions calibrate the trap, and micromotion shows up as extra sidebands at $\Omega_{\mathrm{rf}}$. **Thermometry:** thermal-state asymmetry $P_{\mathrm{RSB}}/P_{\mathrm{BSB}} = \bar{n}/(\bar{n}+1)$.

**The $\sqrt{n}$ dependence cuts both ways:** it's how you climb the Fock ladder deterministically ($\pi$-pulse durations scale as $1/\sqrt{n}$, and mismatch reveals which $|n\rangle$ you're in — Fock-state synthesis, motional-state tomography from Rabi-flop Fourier components), and it's why sideband flopping on a thermal state dephases (each $n$ flops at its own rate).

> [!question]- Why does blue-sideband Rabi flopping on a Doppler-cooled ion look like a fast decay rather than oscillation?
> The rate $\eta\sqrt{n{+}1}\,\Omega$ differs per Fock state; a thermal distribution ($\bar{n} \sim 10$) superposes many incommensurate frequencies which dephase in a few cycles. The Fourier transform of that flopping curve *is* the population distribution $P(n)$ — the bug is a diagnostic.

# Connections

- [[Lamb-Dicke Regime]] — where these couplings and their $\eta$-scalings come from
- [[Jaynes-Cummings Model]] — RSB realizes it exactly, phonon-for-photon
- [[Resolved Sideband Cooling]] — RSB cycling as a cooling engine
- [[Molmer-Sorensen Gate]] — both sidebands at once, off-resonantly: the entangling force

---
Source: Leibfried, Blatt, Monroe & Wineland, *Rev. Mod. Phys.* 75, 281 (2003)
