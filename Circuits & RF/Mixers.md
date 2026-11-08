#circuits #electronics

**A mixer is a three-port device that multiplies two signals, and multiplication makes sum and difference frequencies: $\cos\omega_1 t\cdot\cos\omega_2 t = \tfrac12[\cos(\omega_1{-}\omega_2)t + \cos(\omega_1{+}\omega_2)t]$.** Downconversion, phase detection, lock-ins, and heterodyne detection are all a choice of which term to keep. Note the two outputs carry half the amplitude each (the ½), and that the *difference* term is what survives low-pass filtering, so a mixer converts a frequency *offset* into a slow signal while discarding the carrier.

# Reference

**Ports** (the names come from radio receivers):
- **LO** (local oscillator) — the strong reference signal you supply. In the common passive mixer, the *diode double-balanced mixer*, four diodes in a ring act as switches that the LO flips every half cycle, so the RF is multiplied by a ±1 square wave at the LO frequency. The diodes only switch cleanly when the LO is at its specified drive level, e.g. +7 or +13 dBm. Because a square wave contains odd harmonics, weaker products also appear at $3f_\text{LO} \pm f_\text{RF}$ and above.
- **RF** — the signal to be converted.
- **IF** (intermediate frequency) — the product out; a filter after the port selects the sum or the difference.

**Picture:** two tones beating: the product of two sinusoids is their sum and difference, and the slow difference beat carries the phase relationship between them.

**Diode double-balanced mixer numbers:**
- conversion loss ~6–7 dB: the IF output sits that far below the RF input
- RF should stay ≥ 10 dB below the LO; closer than that, the RF itself starts switching the diodes and intermodulation (intermod) products grow quickly — the 1 dB compression spec marks where
- LO→IF isolation ~30–40 dB, so LO leakage at the output is real
- products reflected from an unmatched IF port re-enter the mixer and mix again, so the IF port needs a 50 Ω termination even out of band, not only in the wanted band

**Image problem:** both $f_\text{LO}+f_\text{IF}$ and $f_\text{LO}-f_\text{IF}$ convert to the same IF — noise and interferers at the image ride in unless you filter the RF first or use an image-reject architecture (an IQ mixer whose two outputs are combined so that one of the two inputs cancels).

**IQ mixer:** two mixers with the LO split 0°/90° → the in-phase (I) and quadrature (Q) outputs give the full complex amplitude — magnitude *and sign* of the frequency offset; run in reverse it's a single-sideband generator.

**Phase-detector mode:** same frequency into both ports → the difference term is at DC, giving $V_{\mathrm{IF}} \propto A_{\mathrm{RF}}\cos\Delta\phi$ with $\Delta\phi$ the phase difference (rad). The useful operating point is quadrature ($\Delta\phi = 90°$): output crosses zero there and the slope $dV/d\Delta\phi$ is maximal, so it is simultaneously a null detector and the most sensitive discriminator. Note the output scales with RF *amplitude* as well as phase — amplitude noise leaks into the phase reading unless the RF is limited or the loop is amplitude-insensitive. This is the front end of [[Phase-Locked Loops|PLLs]] and [[Lock-In Detection|lock-ins]].

> [!question]- Mixing 80 MHz RF with a 70 MHz LO gives a 10 MHz IF — what other input frequency lands at the same IF, and why does it matter?
> 60 MHz, the image ($f_\text{LO}-f_\text{IF}$): anything there — including plain noise — lands on top of your IF, doubling the noise bandwidth at best. Filter ahead of the mixer or use an image-reject/IQ mixer.

# Connections

- [[Heterodyne Detection]] — the same multiplication with one input at optical frequency
- [[Lock-In Detection]] — a mixer plus low-pass, run at audio with huge dynamic range
- [[Phase-Locked Loops]] — the mixer-as-phase-detector inside the loop
- [[Sideband Spectrum of Modulated Light]] — reading mixer-style products in the optical domain
- [[dB Conventions]] — LO levels and conversion loss bookkeeping

---
Source: Pozar, *Microwave Engineering* 4th ed., Ch. 13
