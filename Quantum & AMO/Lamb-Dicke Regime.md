#quantum #AMO #ions

**The Lamb–Dicke parameter $\eta = k x_0$ measures the ion's ground-state wavepacket against the laser wavelength; when it's small, the laser phase across the wavepacket expands cleanly into carrier plus one sideband pair.** All coherent spin–motion coupling is order-by-order in $\eta$.

# Reference

$$\eta = k x_0, \qquad x_0 = \sqrt{\frac{\hbar}{2 m \omega}}$$

$\eta$ = Lamb–Dicke parameter (dimensionless — the laser phase, in radians, accumulated across one ground-state wavepacket); $k = 2\pi/\lambda$ = laser wavevector (m⁻¹) projected on the motional axis ($k \to k\cos\theta$ for a beam at angle $\theta$; for a two-photon Raman drive use the *difference* wavevector $\Delta k$, which is ~0 for co-propagating beams and $2k$ for counter-propagating — see [[Raman Transitions]]); $x_0$ = rms ground-state position spread (m); $m$ = ion mass (kg); $\omega$ = secular trap frequency (rad/s).

Proportionalities worth reading off: $\eta \propto k/\sqrt{m\omega}$ — heavier ions and stiffer traps give smaller $\eta$ (weaker sidebands, deeper in the regime), and shorter wavelengths give larger $\eta$. Equivalently $\eta^2 = \omega_{\mathrm{rec}}/\omega$ with $\omega_{\mathrm{rec}} = \hbar k^2/2m$ the recoil frequency: $\eta^2$ is the ratio of one photon's recoil energy to one motional quantum, i.e. the probability that a scattering event changes $n$. Typical values 0.05–0.2.

The laser phase at the ion's position is an operator:

$$e^{ik\hat{x}} = e^{i\eta(a + a^\dagger)} \approx 1 + i\eta(a + a^\dagger) - \tfrac{\eta^2}{2}(a + a^\dagger)^2 + \dots$$

Each order, made resonant by laser detuning $0, \mp\omega$, gives a distinct process:

| order | transition | Rabi rate |
|---|---|---|
| carrier | $\vert g,n\rangle \leftrightarrow \vert e,n\rangle$ | $\Omega\,(1 - \eta^2 n + \dots)$ |
| red sideband | $\vert g,n\rangle \leftrightarrow \vert e,n{-}1\rangle$ | $\eta\sqrt{n}\,\Omega$ |
| blue sideband | $\vert g,n\rangle \leftrightarrow \vert e,n{+}1\rangle$ | $\eta\sqrt{n{+}1}\,\Omega$ |

Here $\Omega$ = bare (carrier) Rabi frequency [rad/s] and $n$ = motional Fock index; the $\sqrt{n}$ factors come from $a|n\rangle = \sqrt{n}|n{-}1\rangle$.

**Lamb–Dicke regime** proper: $\eta^2(2n+1) \ll 1$ — with $2n+1 = \langle (a+a^\dagger)^2\rangle$ this is "phase spread across the *thermally extended* wavepacket ≪ 1 rad", so the expansion truncates and higher sidebands ($O(\eta^2)$) are negligible. Hot ions leave the regime even at small $\eta$; the exact carrier rate $\Omega\,e^{-\eta^2/2} L_n(\eta^2)$ (Debye–Waller factor) is why a hot chain shows dephased, weakened Rabi flopping — thermal spread in $n$ becomes spread in Rabi rate.

**Recoil suppression:** in the regime, scattering on the carrier changes $n$ only with probability $\sim\eta^2$ — the trap absorbs the recoil (Mössbauer logic). This is what makes cycling detection and sideband cooling's carrier-decay step work.

> [!question]- Your carrier Rabi oscillations decay much faster than $T_2$ but the qubit is fine in Ramsey. First suspect?
> Thermal motion: the carrier rate carries $(1 - \eta^2 n)$-type factors, so a distribution over $n$ gives a distribution of Rabi rates — flopping dephases while true coherence is intact. Cool better (or check for heating) rather than blaming the laser.

# Connections

- [[Dipole Approximation]] — this is exactly the term the dipole approximation drops, kept for the COM coordinate
- [[Sideband Transitions]] — the three resonances above, used as tools
- [[Taylor Expansion]] — the whole regime is a controlled small-parameter truncation
- [[Quantum Harmonic Oscillator]] — supplies $x_0$ and the $a, a^\dagger$ this note manipulates

---
Source: Leibfried, Blatt, Monroe & Wineland, *Rev. Mod. Phys.* 75, 281 (2003)
