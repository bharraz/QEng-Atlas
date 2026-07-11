#quantum-optics

**Modulating a carrier writes sidebands at $\pm n f_\mathrm{mod}$; the *amplitudes* look the same for AM and PM — the *phases* of the sideband pair are what distinguish them.** This is the decoder ring for every heterodyne spectrum and every EOM-driven scheme in the lab.

# Reference

Pure phase modulation with depth $\beta$:

$$
E = E_0\, e^{i(\omega_c t + \beta\sin\Omega t)} = E_0 \sum_{n=-\infty}^{\infty} J_n(\beta)\, e^{i(\omega_c + n\Omega)t}
$$

with $J_{-n}(\beta) = (-1)^n J_n(\beta)$ — **the lower sidebands carry a sign flip.** Small $\beta$: carrier $\approx 1-\beta^2/4$, first sidebands $\pm\beta/2$.

**AM vs PM — the phase relationships:**

| | sideband pair | beat notes vs carrier | direct photodiode at $\Omega$ |
|---|---|---|---|
| **PM** | antisymmetric ($-1$)$^n$ | cancel | nothing |
| **AM** | symmetric, in phase | add | full modulation |

**Pure PM produces zero intensity modulation** — the upper and lower beats against the carrier interfere destructively. Anything that unbalances the pair (a cavity reflecting one sideband differently, a dispersive medium) converts PM→AM; that conversion *is* the [[Pound-Drever-Hall Locking]] error signal.

**Reading a heterodyne spectrum:** you see powers $|J_n(\beta)|^2$ — symmetric for both AM and PM, so the spectrum analyzer alone can't tell them apart; check direct detection. Calibrate $\beta$ from the carrier/sideband ratio, or exactly: carrier nulls at $\beta = 2.405$ (first zero of $J_0$).

**Bichromatic fields are two tones,** not modulation — but two equal tones symmetric about a (suppressed) carrier are exactly $E \propto \cos(\Omega t)\,e^{i\omega_c t}$: carrier-suppressed AM. That's the [[Molmer-Sorensen Gate]] drive, and why it's engineered as symmetric detuning from the sidebands.

> [!question]- Your EOM-modulated beam shows clean symmetric sidebands on the heterodyne spectrum but the lock is weak. What do you check, and why does the spectrum not help?
> Check for residual AM (direct photodiode signal at $\Omega$) and modulation depth. The power spectrum $|J_n|^2$ is identical for AM and PM — it's blind to the sideband phase relationship that the PDH scheme actually exploits.

# Connections

- [[Electro-Optic Modulator]] — the device that writes these sidebands; $\beta = \pi V/V_\pi$
- [[Bessel Functions]] — where the $J_n(\beta)$ amplitudes come from
- [[Molmer-Sorensen Gate]] — bichromatic light as the two-tone limiting case
- [[Pound-Drever-Hall Locking]] — PM→AM conversion as an error signal
- [[Heterodyne Detection]] — how the spectrum gets measured in the first place

---
Source: Loudon, *The Quantum Theory of Light*, 3rd ed., Ch. 6 (heterodyne detection of modulated fields)
