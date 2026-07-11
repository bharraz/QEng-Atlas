#quantum #AMO #ions

**The Lamb–Dicke parameter $\eta = k x_0$ measures the ion's ground-state wavepacket against the laser wavelength; when it's small, the laser phase across the wavepacket expands cleanly into carrier plus one sideband pair.** All coherent spin–motion coupling is order-by-order in $\eta$.

# Reference

$$\eta = k x_0, \qquad x_0 = \sqrt{\frac{\hbar}{2 m \omega}}$$

with $x_0$ the ground-state spread; equivalently $\eta^2 = \omega_{\mathrm{rec}}/\omega$ (recoil vs trap frequency). Typical values 0.05–0.2 (angle factor $k \to k\cos\theta$; for Raman pairs use $\Delta k$).

The laser phase at the ion's position is an operator:

$$e^{ik\hat{x}} = e^{i\eta(a + a^\dagger)} \approx 1 + i\eta(a + a^\dagger) - \tfrac{\eta^2}{2}(a + a^\dagger)^2 + \dots$$

Each order, made resonant by laser detuning $0, \mp\omega$, gives a distinct process:

| order | transition | Rabi rate |
|---|---|---|
| carrier | $\vert g,n\rangle \leftrightarrow \vert e,n\rangle$ | $\Omega\,(1 - \eta^2 n + \dots)$ |
| red sideband | $\vert g,n\rangle \leftrightarrow \vert e,n{-}1\rangle$ | $\eta\sqrt{n}\,\Omega$ |
| blue sideband | $\vert g,n\rangle \leftrightarrow \vert e,n{+}1\rangle$ | $\eta\sqrt{n{+}1}\,\Omega$ |

**Lamb–Dicke regime** proper: $\eta^2(2n+1) \ll 1$ — the expansion truncates, higher sidebands ($\eta^2$) negligible. Hot ions leave the regime even at small $\eta$; the exact carrier rate $\Omega\,e^{-\eta^2/2} L_n(\eta^2)$ (Debye–Waller factor) is why a hot chain shows dephased, weakened Rabi flopping — thermal spread in $n$ becomes spread in Rabi rate.

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
