#optics

**A Pockels crystal changes refractive index linearly with applied voltage, phase-modulating the light passing through** — drive it sinusoidally and the optical spectrum sprouts sidebands at multiples of the drive frequency with Bessel-function amplitudes.

# Reference

Pockels effect: $\Delta n \propto V$, giving phase $\phi = \pi V/V_\pi$ (rad). $V_\pi$ = half-wave voltage (V), the voltage producing $\pi$ of optical phase — the single figure of merit, scaling as $V_\pi \propto \lambda d / (n^3 r\, L)$ with $d$ the electrode gap, $L$ the interaction length, $r$ the electro-optic coefficient. Hence hundreds of volts for bulk crystals (large $d$) versus a few volts for waveguide devices (µm gaps, cm lengths), and why a resonant RF tank — which multiplies the applied voltage by its $Q$ — is the standard workaround at a fixed frequency.

Modulation depth $\beta = \pi V_{\text{pk}}/V_\pi$ (rad) is just the peak phase excursion.

Phase modulation at $\Omega$ with depth $\beta$:
$$
E_0\, e^{i(\omega t + \beta\sin\Omega t)} = E_0 \sum_{n=-\infty}^{\infty} J_n(\beta)\, e^{i(\omega + n\Omega)t}
$$
Carrier amplitude $J_0(\beta)$, sidebands at $\omega \pm n\Omega$ with amplitudes $J_n(\beta)$, and $J_{-n} = (-1)^n J_n$ — the odd-order sign flip is the fingerprint of PM vs AM. Small $\beta$: carrier plus two sidebands of amplitude $\pm\beta/2$. $\beta \approx 1.08$ maximizes first-sideband power (the PDH sweet spot).

**Amplitude modulation** needs interference to convert phase to intensity: a Mach-Zehnder with the EOM in one arm, or polarization rotation between crossed polarizers (Pockels cell as fast shutter).

Gotchas: residual amplitude modulation (RAM) from etalon fringes and polarization misalignment puts a drifting offset on your PDH error signal — align input polarization to the crystal axis, wedge/AR the faces, temperature-stabilize. Bulk crystals are also piezoelectric: watch for acoustic resonances.

> [!question]- Pure phase modulation, direct photodetection — what do you see at $\Omega$, and why?
> Nothing: $|E|^2$ is constant. The upper and lower sidebands beat against the carrier with opposite sign ($J_{-1} = -J_1$) and cancel exactly. You only get a signal at $\Omega$ when something unbalances the sidebands in amplitude or phase — a cavity's dispersion, for instance, which is precisely how PDH works.

# Connections

- [[Bessel Functions]] — $J_n(\beta)$ owns the sideband amplitudes; the $\beta \ll 1$ limits are the small-modulation kit
- [[Sideband Spectrum of Modulated Light]] — reading PM vs AM off a heterodyne spectrum, sign conventions and all
- [[Pound-Drever-Hall Locking]] — the flagship application: EOM sidebands as the phase reference
- [[Birefringence]] — the Pockels effect is voltage-controlled birefringence; crystal axes matter

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 20 (electro-optics)
