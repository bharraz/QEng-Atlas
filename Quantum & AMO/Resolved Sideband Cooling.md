 #AMO #ions

**When the trap frequency beats the linewidth ($\omega \gg \Gamma$), the motional sidebands resolve — drive the red one and every optical cycle removes a phonon.** This is how you get from Doppler's $\bar{n} \sim 10$ to the ground state.

# Reference

Cycle: drive the red sideband $|g, n\rangle \to |e, n-1\rangle$ (Rabi rate $\eta\sqrt{n}\,\Omega$), then let/make the ion decay $|e, n-1\rangle \to |g, n-1\rangle$. In the Lamb–Dicke regime decay goes overwhelmingly on the carrier ($\Delta n = 0$, recoil suppressed), so each cycle is a net $n \to n-1$. Repeat until the RSB has nothing left to drive.

**Implementations:** a narrow optical transition ($S \to D$ quadrupole) cycled with a quench beam, or a stimulated Raman pair between hyperfine states with spontaneous repump — same physics, $\Gamma_{\mathrm{eff}}$ engineered to sit below $\omega$.

**Cooling limit** — off-resonant carrier and blue-sideband scattering fight you:

$$\bar{n}_{\min} \sim \left(\frac{\Gamma_{\mathrm{eff}}}{2\omega}\right)^2 \ll 1$$

$\bar n$ = mean phonon number (dimensionless occupation of the motional mode); $\Gamma_{\mathrm{eff}}$ = effective linewidth of the cooling transition (s⁻¹; natural, or engineered by a quench/repump beam); $\omega$ = trap frequency (rad/s). The ratio $\Gamma_{\mathrm{eff}}/2\omega$ is the amplitude of off-resonant excitation of the *wrong* (heating) sideband, so the limit is that leakage squared — resolve the sidebands better and the floor drops quadratically.

Ground-state occupation of 99%+ is routine; competing against it is the trap's anomalous heating rate $\dot{\bar{n}}$ — cool faster than the trap reheats, and mind that $\eta\sqrt{n}\,\Omega \to 0$ as $n \to 0$ (the last phonon is the slowest; pulsed sequences chirp pulse durations to match).

**Thermometry from sideband asymmetry:** after cooling, compare sideband strengths. For a thermal state,

$$\frac{P_{\mathrm{RSB}}}{P_{\mathrm{BSB}}} = \frac{\bar{n}}{\bar{n} + 1} \equiv R \qquad \Rightarrow \qquad \bar{n} = \frac{R}{1 - R}$$

A vanishing red sideband *is* the ground-state signature — $|n{=}0\rangle$ has no phonon to give.

> [!question]- Why does the red sideband disappear at $\bar{n} = 0$ while the blue survives?
> RSB requires removing a phonon: from $|n{=}0\rangle$ there is none ($\eta\sqrt{n}\,\Omega = 0$). BSB adds one, rate $\eta\sqrt{n+1}\,\Omega \ne 0$ always. The asymmetry is absolute thermometry — no calibration of $\Omega$, $\eta$, or detection needed, just the ratio.

# Connections

- [[Sideband Transitions]] — the RSB/BSB couplings and rates this scheme runs on
- [[Doppler Cooling]] — stage one; delivers the $\bar{n} \sim 10$, Lamb–Dicke starting point
- [[Lamb-Dicke Regime]] — guarantees decay recoil doesn't undo the phonon removal
- [[Fock States]] — the destination: motional $|0\rangle$ as the clean slate for gates

---
Source: Leibfried, Blatt, Monroe & Wineland, *Rev. Mod. Phys.* 75, 281 (2003)
