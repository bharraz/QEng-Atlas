#optics

**A Pockels crystal changes refractive index linearly with applied voltage, phase-modulating the light passing through** — drive it sinusoidally and the optical spectrum sprouts sidebands at multiples of the drive frequency with Bessel-function amplitudes.

# Reference

Pockels effect: $\Delta n \propto V$, giving phase $\phi = \pi V/V_\pi$ (rad). $V_\pi$ = half-wave voltage (V), the voltage producing $\pi$ of optical phase — the single figure of merit, scaling as $V_\pi \propto \lambda d / (n^3 r\, L)$ with $d$ the electrode gap, $L$ the interaction length, $r$ the electro-optic coefficient. Hence hundreds of volts for bulk crystals (large $d$) versus a few volts for waveguide devices (µm gaps, cm lengths), and why a resonant RF tank — which multiplies the applied voltage by its $Q$ — is the standard workaround at a fixed frequency.

Modulation depth $\beta = \pi V_{\text{pk}}/V_\pi$ (rad) is the peak phase excursion.

Phase modulation at $\Omega$ with depth $\beta$:
$$
E_0\, e^{i(\omega t + \beta\sin\Omega t)} = E_0 \sum_{n=-\infty}^{\infty} J_n(\beta)\, e^{i(\omega + n\Omega)t}
$$
Carrier amplitude $J_0(\beta)$, sidebands at $\omega \pm n\Omega$ with amplitudes $J_n(\beta)$, and $J_{-n} = (-1)^n J_n$ — the odd-order sign flip is the fingerprint of PM vs AM. Small $\beta$: carrier plus two sidebands of amplitude $\pm\beta/2$. $\beta \approx 1.08$ maximizes the product $J_0J_1$, the PDH error-signal slope (the usual PDH operating point); first-sideband power alone peaks at $\beta \approx 1.84$.

**Picture:** the crystal as a voltage-controlled delay line: wiggling the optical path length wiggles the phase, and a phase wiggle at frequency $\Omega$ is the same thing as sidebands spaced by $\Omega$.

**Amplitude modulation** needs interference to convert phase to intensity: a Mach-Zehnder with the EOM in one arm, or polarization rotation between crossed polarizers (Pockels cell as fast shutter).

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| residual amplitude modulation (RAM) | etalon fringes between the crystal faces and input polarization off the crystal axis turn phase modulation into intensity modulation | a drifting offset on a PDH error signal; align the input polarization to the crystal axis, wedge or AR-coat the faces, temperature-stabilize |
| acoustic resonances | bulk crystals are also piezoelectric, so the drive excites sound waves | spurious peaks and phase jumps in the modulation response at particular frequencies |
| resonant drive off resonance | the resonant RF tank drifts with temperature, and an impedance mismatch reflects drive power | modulation depth falls; measure the reflected RF with a directional coupler |
| photorefractive damage | in lithium niobate, visible light moves charge and changes the index | slow drift and beam distortion at high visible intensity; MgO-doped or heated crystals resist it |
| clipping | bulk crystal apertures are a few mm | diffraction rings and loss |
| RF heating | dissipated drive power warms the crystal | slow drift of RAM and of the bias point of amplitude modulators |

> [!question]- Pure phase modulation, direct photodetection — what do you see at $\Omega$, and why?
> Nothing: $|E|^2$ is constant. The upper and lower sidebands beat against the carrier with opposite sign ($J_{-1} = -J_1$) and cancel exactly. You only get a signal at $\Omega$ when something unbalances the sidebands in amplitude or phase — a cavity's dispersion, for instance, which is precisely how PDH works.

# Connections

- [[Bessel Functions]] — $J_n(\beta)$ owns the sideband amplitudes; the $\beta \ll 1$ limits are the small-modulation approximations
- [[Sideband Spectrum of Modulated Light]] — reading PM vs AM off a heterodyne spectrum, sign conventions and all
- [[Pound-Drever-Hall Locking]] — the flagship application: EOM sidebands as the phase reference
- [[Birefringence]] — the Pockels effect is voltage-controlled birefringence; crystal axes matter

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 20 (electro-optics)
