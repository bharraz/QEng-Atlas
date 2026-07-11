#optics

**Beat the signal field against a strong local oscillator on a photodiode: the cross term oscillates at the difference frequency and carries the signal's full amplitude *and* phase into RF** — where your electronics are actually good.

# Reference

Photocurrent from $E_s + E_{LO}$:
$$
I \propto P_{LO} + P_s + 2\sqrt{P_s P_{LO}}\,\cos(\Delta\omega\, t + \Delta\phi)
$$
The beat at $\Delta\omega = \omega_s - \omega_{LO}$ is a faithful downconversion of the optical field — amplitude in the beat size, optical phase in the RF phase. Direct detection measures $|E|^2$ and throws phase away; heterodyne keeps it.

**LO gain beats detector noise:** the signal term scales as $\sqrt{P_{LO}}$, so cranking the LO amplifies the beat above amplifier/Johnson noise until *LO shot noise* dominates — at which point you're shot-noise-limited on a possibly picowatt signal. Noiseless gain, from a beam splitter and a bright beam. Condition: LO shot noise > electronic noise floor, the first thing to check when a beat looks buried.

**Practical requirements:** mode overlap is everything — the beat amplitude multiplies by the overlap integral, so match spatial modes and polarization or watch contrast vanish. $\Delta\omega$ must sit inside the photodiode bandwidth; an AOM in one arm is the standard way to synthesize the offset.

**Homodyne** is the $\Delta\omega = 0$ special case: the beat becomes DC, measuring one quadrature selected by the LO phase; balanced detection subtracts the LO's classical noise. Heterodyne gets both quadratures at once but pays 3 dB (image vacuum noise).

Uses on your table: laser beat notes (linewidth), fiber-noise cancellation, vibrometry, and every RF-domain measurement of an optical phase.

> [!question]- Why does a stronger LO improve SNR when it also adds shot noise?
> Signal beat grows as $\sqrt{P_{LO}}$; LO shot-noise current also grows as $\sqrt{P_{LO}}$ — so SNR vs LO power *saturates* at the shot-noise limit set by $P_s$ alone, rather than degrading. Meanwhile fixed electronic noise becomes negligible. The LO buys you out of technical noise for free; it can't buy you past the photon statistics of the signal.

# Connections

- [[Mixers]] — the photodiode *is* the mixer; square-law detection does the multiplication
- [[Laser Linewidth]] — beat-note linewidth measurement is heterodyne detection verbatim
- [[Homodyne Detection]] — the zero-offset limit, quadrature measurement and vacuum-limited noise
- [[Acousto-Optic Modulator]] — the standard offset-frequency generator
- [[Photodetection and Shot Noise]] — the noise floor that LO gain runs into

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 18 (photodetectors: heterodyning)
