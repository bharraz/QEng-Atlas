#circuits #electronics

**A mixer multiplies two signals, and multiplication makes sum and difference frequencies: $\cos\omega_1 t\cdot\cos\omega_2 t = \tfrac12[\cos(\omega_1{-}\omega_2)t + \cos(\omega_1{+}\omega_2)t]$.** Everything else — downconversion, phase detection, lock-ins, heterodyne — is choosing which term to keep.

# Reference

Ports: **LO** (the strong pump that switches the diodes — drive at spec, e.g. +7 or +13 dBm), **RF** (signal), **IF** (product out, filter to select sum or difference).

**Diode double-balanced mixer numbers:** conversion loss ~6–7 dB; keep RF ≥ 10 dB below LO or intermod products bloom (1 dB compression spec); LO→IF isolation ~30–40 dB, so LO leakage is real. Terminate the IF in 50 Ω even out of band — reflected products remix.

**Image problem:** both $f_\text{LO}+f_\text{IF}$ and $f_\text{LO}-f_\text{IF}$ convert to the same IF — noise and interferers at the image ride in unless you filter the RF first or use an image-reject architecture.

**IQ mixer:** two mixers with the LO split 0°/90° → I and Q give the full complex amplitude — magnitude *and sign* of the frequency offset; run in reverse it's a single-sideband generator.

**Phase-detector mode:** same frequency into both ports → DC out $\propto\cos\Delta\phi$; zero and maximally steep at quadrature. This is the front end of PLLs and lock-ins.

> [!question]- Mixing 80 MHz RF with a 70 MHz LO gives a 10 MHz IF — what other input frequency lands at the same IF, and why care?
> 60 MHz, the image ($f_\text{LO}-f_\text{IF}$): anything there — including plain noise — lands on top of your IF, doubling the noise bandwidth at best. Filter ahead of the mixer or use an image-reject/IQ mixer.

# Connections

- [[Heterodyne Detection]] — the same trick with one input at optical frequency
- [[Lock-In Detection]] — a mixer plus low-pass, run at audio with huge dynamic range
- [[Phase-Locked Loops]] — the mixer-as-phase-detector inside the loop
- [[Sideband Spectrum of Modulated Light]] — reading mixer-style products in the optical domain
- [[dB Conventions]] — LO levels and conversion loss bookkeeping

---
Source: Pozar, *Microwave Engineering* 4th ed., Ch. 13
